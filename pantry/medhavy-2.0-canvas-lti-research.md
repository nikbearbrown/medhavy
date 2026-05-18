# Canvas LTI Integration — Research Report
**Medhavy 2.0 Design Grounding**

---

## Executive summary

Canvas LTI integration is mature, well-documented, and the right path for Medhavy's institutional deployment. The standard is LTI 1.3 with LTI Advantage — the current specification supported by Canvas (Instructure) at the "LTI Advantage Complete" certification level. Every capability Medhavy needs for 2.0 — single sign-on from Canvas into Medhavy, grade passback to the Canvas gradebook, course roster sync, and course navigation embedding — is supported by existing specification components.

The key findings are:

**On what LTI 1.3 gives Medhavy.** Three services cover everything in the 2.0 roadmap. Assignment and Grade Services (AGS) handles grade passback — Glimmer scores returned to the Canvas gradebook without manual entry. Names and Role Provisioning Services (NRPS) handles roster sync — Medhavy knows which students are enrolled without manual CSV imports. Deep Linking handles content embedding — instructors can add Medhavy textbook sections directly into Canvas modules. None of these require Canvas admin API keys or custom Canvas integrations. They are standard LTI Advantage services that any Canvas institution can enable.

**On the authentication flow.** LTI 1.3 replaces the old shared-secret OAuth 1.0 model with OpenID Connect (OIDC) over OAuth 2.0, using JSON Web Tokens (JWTs) signed with RSA keys. Medhavy already issues its own JWTs for textbook access. The LTI 1.3 authentication flow is structurally similar: Canvas initiates a login request, Medhavy validates the JWT signature against Canvas's public JWK endpoint, and the user lands in Medhavy authenticated. The existing Clerk + Supabase architecture needs one new layer — an LTI identity mapping table — but the core auth infrastructure is already in place.

**On the institutional approval bottleneck.** This is the most important practical finding. Every Canvas institution has its own LTI approval process. The technical integration takes days. The institutional approval takes weeks to months, involves security review, legal review, accessibility review, and sometimes a data processing agreement. At the University of Washington, LTI additions were frozen entirely from November 2024 to March 2025 to allow the institution to update its intake process. UC Riverside explicitly states that student data transmission through LTI requires approval review. Building the integration is the easy part. Getting it approved at each institution is the work.

**On Dynamic Registration.** Canvas added Dynamic Registration in 2025, eliminating the manual copy-paste of JSON configuration blocks between systems. An administrator enters a single registration URL, and Canvas and the tool exchange configuration automatically. This reduces per-institution setup time dramatically and should be Medhavy's primary installation path.

**On what this means for Medhavy's existing auth architecture.** The current Medhavy Hub JWT flow — Hub issues a 24-hour token, textbook validates it — does not need to be replaced. LTI 1.3 is an additional authentication pathway for institutional deployments, not a replacement for the existing model. Students who arrive via Canvas LTI launch get a Medhavy session token through the LTI flow; students who access Medhavy directly continue using the existing Clerk-based flow.

---

## 1. What LTI 1.3 is and what it provides

Learning Tools Interoperability (LTI) is a specification from the 1EdTech Consortium (formerly IMS Global) that defines how Learning Management Systems communicate with external tools. It is the dominant integration standard in higher education. Canvas is certified LTI Advantage Complete, meaning it supports the full LTI 1.3 specification plus all three LTI Advantage service extensions.

LTI 1.3 is not an API in the conventional sense. It is a launch protocol: Canvas initiates a launch to Medhavy by sending a signed JWT containing user identity, course context, and role information. Medhavy validates the JWT, maps the identity to a Medhavy user account, and serves the appropriate content. The key difference from earlier LTI versions is the security model: LTI 1.1 used shared secrets over OAuth 1.0; LTI 1.3 uses asymmetric RSA key pairs with JWTs over OAuth 2.0 and OpenID Connect.

### The three LTI Advantage services

LTI Advantage sits on top of the LTI 1.3 security framework and provides three service extensions that cover all of Medhavy's institutional integration needs.

**Assignment and Grade Services (AGS).** Allows Medhavy to write scores back to the Canvas gradebook, create gradebook columns (line items) programmatically, and read existing submission data. This is the mechanism for returning Glimmer scores to Canvas without instructors manually entering grades. The Score service within AGS has been extended beyond the LTI 1.1 basic outcomes model: it can pass submission data (not just a number) that appears in Canvas's SpeedGrader view, allowing instructors to see what the student produced in Medhavy without leaving Canvas.

**Names and Role Provisioning Services (NRPS).** Allows Medhavy to request the full course roster — all enrolled students and their roles — from a Canvas course, including students who have never launched Medhavy. In LTI 1.1, the tool could only discover students as they individually launched and authenticated. NRPS eliminates this: Medhavy can pull the complete roster on demand, detect students who have left the course, and populate its class management layer without any manual CSV import. This directly replaces the current Medhavy class invite / join flow for Canvas-integrated courses.

**Deep Linking (LTI-DL 2.0).** Allows instructors to embed specific Medhavy resources — a textbook section, a Quiz Me session for a specific concept node, a Case Study — directly into Canvas course modules. The instructor launches Medhavy from within Canvas, selects a resource, and Canvas stores a link that students click to land directly in the right place. This is the mechanism that makes Medhavy feel integrated into the course rather than accessed as a separate external site.

### What Canvas specifically supports

Canvas supports LTI Advantage Complete, meaning all three services above plus:

- Dynamic Registration (added 2025) — automated configuration exchange replacing manual JSON copy-paste
- Platform Storage — enhanced security for LTI launches in privacy-oriented browsers (Safari, Firefox)
- Platform Notification Service (PNS) — server-to-server notifications from Canvas to Medhavy on events like assignment submission, enrollment changes
- xAPI — for learning activity stream data, relevant to the bandit's signal layer

---

## 2. The authentication flow in detail

### The OIDC launch sequence

The LTI 1.3 launch uses a three-step OIDC third-party flow. Understanding this is essential for scoping the engineering work.

**Step 1 — Canvas initiates login.** When a student clicks a Medhavy link in Canvas, Canvas sends a login initiation request to Medhavy's OIDC initiation URL (configured in the Developer Key). The request includes the `iss` (issuer — always `https://canvas.instructure.com` for Instructure-hosted Canvas), the `login_hint` (Canvas's opaque user identifier), and the `target_link_uri` (where Medhavy should ultimately redirect the user).

**Step 2 — Medhavy requests authorization.** Medhavy generates a state parameter (a CSRF token for the session), stores it, and redirects the user's browser to Canvas's authorization URL (`/api/lti/authorize_redirect`) with the state, nonce, client ID, and redirect URI. This is the standard OIDC authorization code flow.

**Step 3 — Canvas sends the ID token.** Canvas validates the request and redirects back to Medhavy's redirect URI with an `id_token` — a signed JWT containing the full LTI payload. Medhavy validates the JWT signature against Canvas's public JWK endpoint (`https://sso.canvaslms.com/api/lti/security/jwks`), validates the state matches what was stored in step 2, and processes the payload.

The JWT payload contains everything Medhavy needs to authenticate the user and establish context:
- `sub` — the Canvas user ID (stable across sessions, use this as the primary identifier)
- `name`, `email`, `given_name`, `family_name` — user profile claims (only available if privacy level is set to "public" in the Developer Key)
- `https://purl.imsglobal.org/spec/lti/claim/roles` — the user's role in the course (Instructor, Student, etc.)
- `https://purl.imsglobal.org/spec/lti/claim/context` — course ID, title, and type
- `https://purl.imsglobal.org/spec/lti/claim/resource_link` — the specific resource being launched
- `https://purl.imsglobal.org/spec/lti/claim/custom` — any custom parameters configured in the Developer Key
- AGS and NRPS service endpoint claims — the URLs Medhavy should call to use these services in this context

### How this maps to Medhavy's existing auth architecture

Medhavy currently uses Clerk for identity and issues its own JWTs for textbook access. The LTI flow introduces a new identity source: Canvas users whose primary identity is a Canvas `sub` rather than a Clerk user ID.

The integration requires one new component: an **LTI identity mapping table** in Supabase. When a user arrives via LTI launch, Medhavy checks whether the Canvas `sub` maps to an existing Medhavy user. If yes, it creates a Medhavy session for that user. If no, it creates a new Medhavy user account (using the name and email from the LTI claims), adds the mapping to the table, and creates the session.

The existing Clerk-based flow continues unchanged for direct Medhavy access. The LTI flow is an additional authentication pathway, not a replacement.

**The LTI identity mapping table** (new Supabase table):

```sql
lti_identity_mappings (
  id              uuid primary key,
  canvas_sub      text not null,          -- Canvas user ID from JWT sub claim
  canvas_iss      text not null,          -- Canvas issuer (for multi-institution support)
  canvas_email    text,                   -- Email from LTI claims (for display)
  medhavy_user_id text not null,          -- Clerk user ID in Medhavy
  created_at      timestamptz not null,
  last_seen_at    timestamptz,
  unique (canvas_sub, canvas_iss)
)
```

The `canvas_iss` field is critical for multi-institution support. Different Canvas instances (a university's production Canvas vs. a community college partner Canvas) will have different issuers. The combination of `canvas_sub` and `canvas_iss` uniquely identifies a user across all Canvas deployments.

### Token exchange for LTI Advantage service calls

To use AGS or NRPS after the initial launch, Medhavy must obtain an access token via the OAuth 2.0 Client Credentials Grant. This is a server-to-server request — no user browser involved — using Medhavy's RSA private key to sign a JWT assertion, which Canvas validates against the public JWK URL Medhavy registered.

The access token is scoped: Medhavy must request exactly the scopes it needs. For Medhavy 2.0:

- `https://purl.imsglobal.org/spec/lti-ags/scope/lineitem` — create and manage gradebook columns
- `https://purl.imsglobal.org/spec/lti-ags/scope/score` — write scores to the gradebook
- `https://purl.imsglobal.org/spec/lti-ags/scope/result.readonly` — read existing scores
- `https://purl.imsglobal.org/spec/lti-nrps/scope/contextmembership.readonly` — read course roster

Tokens are short-lived (typically 1 hour). Medhavy should cache tokens and refresh before expiry rather than requesting a new token per API call. Canvas throttles AGS requests — the documentation notes they are throttled like all Canvas API requests and Medhavy should respect the rate-limit headers in responses.

---

## 3. The Developer Key configuration

Every Canvas LTI integration starts with a Developer Key — a configuration object that the Canvas administrator creates at the account level. The Developer Key contains Medhavy's registration information and controls which permissions are granted.

### Configuration method: Dynamic Registration (recommended)

Canvas added Dynamic Registration in 2025 as the preferred installation path. Rather than manually filling out a form or pasting a JSON block, the administrator:

1. Goes to Admin → Developer Keys → "+ Developer Key" → "+ LTI Registration"
2. Enters Medhavy's Dynamic Registration URL (e.g., `https://hub.medhavy.app/lti/register`)
3. Canvas fetches Medhavy's OpenID configuration, exchanges registration information automatically, and creates the Developer Key

Medhavy's Dynamic Registration endpoint must return a registration response conforming to the 1EdTech Dynamic Registration specification, then send a `postMessage` to the Canvas parent window (`{subject: 'org.imsglobal.lti.close'}`) to close the registration iframe. Canvas presents the administrator with a summary of what was registered and allows them to make modifications.

One important caveat from the Canvas documentation: the administrator can restrict the scopes Medhavy requested during Dynamic Registration. Medhavy should detect scope restrictions in the configuration response and surface a warning if critical scopes (AGS score write, NRPS roster read) have been removed.

### Manual JSON configuration (fallback)

For institutions that have not enabled Dynamic Registration (older Canvas instances, or institutions that restrict it), Medhavy should also provide a JSON configuration block. The minimal JSON for Medhavy's use case:

```json
{
  "title": "Medhavy",
  "description": "AI-powered interactive textbooks",
  "oidc_initiation_url": "https://hub.medhavy.app/lti/login",
  "target_link_uri": "https://hub.medhavy.app/lti/launch",
  "scopes": [
    "https://purl.imsglobal.org/spec/lti-ags/scope/lineitem",
    "https://purl.imsglobal.org/spec/lti-ags/scope/score",
    "https://purl.imsglobal.org/spec/lti-ags/scope/result.readonly",
    "https://purl.imsglobal.org/spec/lti-nrps/scope/contextmembership.readonly"
  ],
  "extensions": [{
    "domain": "medhavy.app",
    "platform": "canvas.instructure.com",
    "privacy_level": "public",
    "settings": {
      "placements": [
        {
          "placement": "course_navigation",
          "message_type": "LtiResourceLinkRequest",
          "target_link_uri": "https://hub.medhavy.app/lti/launch",
          "text": "Medhavy Textbook"
        },
        {
          "placement": "assignment_selection",
          "message_type": "LtiDeepLinkingRequest",
          "target_link_uri": "https://hub.medhavy.app/lti/deep-link"
        }
      ]
    }
  }]
}
```

The `privacy_level: "public"` setting is required to receive user name and email claims. Without it, Canvas sends only an opaque `user_id`, which Medhavy cannot use to create useful user accounts.

### Canvas-specific JWK endpoint change

A breaking change worth noting for implementation: Canvas's public JWK endpoint domain changed from `https://canvas.instructure.com/api/lti/security/jwks` to `https://sso.canvaslms.com/api/lti/security/jwks`. Tools that hard-coded the old domain will fail JWT validation. Medhavy should fetch the JWK URL dynamically from Canvas's OpenID configuration endpoint rather than hard-coding it.

---

## 4. Grade passback: how Glimmer scores reach Canvas

Glimmer is the Medhavy mode whose output is gradeable and needs to appear in the Canvas gradebook. The AGS flow for this is well-specified.

### Creating the line item (gradebook column)

When an instructor uses Deep Linking to add a Glimmer assignment to a Canvas course, Medhavy creates a line item via the AGS Line Item service. The line item corresponds to one gradebook column. Medhavy specifies:

- `label` — the assignment name ("Glimmer: Apoptosis Week 3")
- `scoreMaximum` — the maximum possible score (Medhavy uses the 5-dimension rubric; the numeric representation of a full rubric score needs to be defined — a reasonable default is 100)
- `resourceLinkId` — the Canvas resource link ID from the deep linking response, connecting the gradebook column to the specific Medhavy resource

### Submitting a score

When a Glimmer submission passes the AI interrogation cycle and is released to the instructor, Medhavy pushes a score to the Canvas gradebook via the AGS Score service. The score payload:

```json
{
  "userId": "<canvas_sub_for_student>",
  "scoreGiven": 85,
  "scoreMaximum": 100,
  "comment": "Strong mechanism explanation; specificity improved after revision.",
  "activityProgress": "Completed",
  "gradingProgress": "PendingManual",
  "timestamp": "2026-05-17T14:30:00Z"
}
```

The `gradingProgress: "PendingManual"` value is important: it tells Canvas the score is provisional and requires instructor review before being finalized. This matches Medhavy's workflow — the AI pre-grades and the instructor grades — and surfaces a "needs grading" indicator in SpeedGrader.

When the instructor grades in Medhavy's instructor dashboard, Medhavy pushes an updated score with `gradingProgress: "FullyGraded"`. The final score and instructor comments appear in the Canvas gradebook immediately.

### Submission data in SpeedGrader

AGS allows Medhavy to include submission data — the student's actual Glimmer submission text — alongside the score. When this is configured, instructors can view the student's submission in Canvas's SpeedGrader view without leaving Canvas. The submission is passed as a URL to the student's Medhavy submission page or as inline content. This is a significant UX improvement for instructor grading workflows.

### The line item creation timing problem

A practical issue: Medhavy needs to create the line item before it can post scores. There are two approaches:

**Deep Linking approach (preferred):** The line item is created when the instructor adds the Glimmer assignment to their Canvas course via Deep Linking. Medhavy creates the line item at that point and stores the line item URL for later score submission. This is the cleanest flow but requires Deep Linking to be part of the assignment setup.

**Score-first approach (fallback):** AGS allows tools to create a line item via the AGS API without Deep Linking, using the `lineitem` scope. Medhavy creates the line item the first time it tries to submit a score for a (course, assignment) pair that has no existing line item. This is more flexible but requires Medhavy to manage line item creation logic.

For Medhavy 2.0, the Deep Linking approach is preferred because it keeps the gradebook structure under instructor control — the instructor explicitly decides which Glimmer assignments should have Canvas gradebook columns.

---

## 5. Roster sync: how class enrollment reaches Medhavy

The current Medhavy class system requires instructors to create classes, generate invite links, and have students join. In a Canvas-integrated deployment, this manual process is unnecessary: NRPS provides the full roster automatically.

### The NRPS flow

When a course is connected to Medhavy via LTI (i.e., the Medhavy tool has been launched at least once in the course context), Medhavy can call the NRPS endpoint to get the current roster. The endpoint URL is provided in the LTI launch JWT under the `https://purl.imsglobal.org/spec/lti-nrps/claim/namesroleservice` claim.

A NRPS response returns an array of members, each with:
- `user_id` — Canvas's opaque user identifier (matches the `sub` in LTI launches)
- `name`, `email` — profile information (if privacy level permits)
- `roles` — 1EdTech role URIs indicating the user's role (e.g., `http://purl.imsglobal.org/vocab/lis/v2/membership#Learner` for students, `http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor` for instructors)
- `status` — Active or Inactive (for detecting dropped students)

### How this changes the Medhavy class creation flow for Canvas courses

When an instructor installs Medhavy in their Canvas course:

1. Medhavy uses NRPS to pull the roster automatically
2. Medhavy creates a Medhavy class record linked to the Canvas course ID
3. All enrolled students are pre-populated in the Medhavy class — no invite link required
4. When a student first launches Medhavy from Canvas, Medhavy finds them already in the class and creates or links their Medhavy account

Medhavy should run a roster sync on a schedule (daily or triggered by a Platform Notification Service event) to detect new enrollments and dropped students. A student who leaves the Canvas course should lose Canvas-based access to Medhavy, mirroring the existing class-based access model.

### Role mapping

Canvas roles map to Medhavy roles as follows:

| Canvas LTI Role URI | Medhavy Role |
|---|---|
| `http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor` | instructor |
| `http://purl.imsglobal.org/vocab/lis/v2/membership#Learner` | student |
| `http://purl.imsglobal.org/vocab/lis/v2/membership#TeachingAssistant` | instructor (with limited admin) |
| `http://purl.imsglobal.org/vocab/lis/v2/institution/person#Administrator` | admin |

Medhavy should store the Canvas role at the time of LTI launch and update it on NRPS sync. A student who becomes a TA mid-semester should have their Medhavy role updated accordingly.

---

## 6. Deep Linking: embedding Medhavy in Canvas modules

Deep Linking (LTI-DL 2.0) allows instructors to place specific Medhavy resources inside Canvas course modules rather than just a generic "open Medhavy" link.

### The Deep Linking flow

1. The instructor adds a module item in Canvas and selects "External Tool" → Medhavy
2. If the tool is configured with the `assignment_selection` or `link_selection` placement, Canvas launches an iframe to Medhavy's Deep Linking URL with an `LtiDeepLinkingRequest` message type JWT
3. Medhavy presents its content selection UI in the iframe — the instructor browses the textbook and selects a specific concept node, chapter, or mode
4. Medhavy POSTs a Deep Linking response back to Canvas with a JSON array of selected content items
5. Canvas stores the selected resources and adds them to the course module

### What Medhavy can offer as deep-linkable resources

For Medhavy 2.0, the following resource types are natural candidates for Deep Linking:

- A specific textbook chapter or section (LtiResourceLink content item — student clicks and lands on that section)
- A Quiz Me session scoped to a specific concept node (student clicks and opens Quiz Me for concept X)
- A Case Study assignment (student clicks and opens a specific professor-approved case)
- A Glimmer assignment (student clicks and opens the Glimmer for a specific concept, with grade passback enabled)

The Glimmer case is the most important because it enables the Canvas gradebook integration. A deep-linked Glimmer assignment creates a Canvas assignment with grade passback, appearing in the Canvas gradebook as a standard assignment.

### Canvas module integration vs. course navigation

Medhavy can appear in Canvas in two places:

**Course navigation tab** (always visible in the left nav of every Canvas course): Good for students who want to open the textbook directly. Always present once the tool is installed. Launches the Medhavy textbook home for the course.

**Module items** (via Deep Linking): Good for structured course delivery. Instructors add specific Medhavy resources as module items that students encounter in sequence with other course materials. The Glimmer assignment, for example, would appear as a week's module item alongside readings and lecture notes.

Medhavy 2.0 should support both placements. Course navigation for ambient access; module items via Deep Linking for structured assignment delivery.

---

## 7. The institutional approval bottleneck

This is the most practically significant finding in the entire research. The engineering work for LTI integration is well-understood and scoped. The institutional deployment process is where time actually goes.

### What approval involves at each institution

Every Canvas institution controls which LTI tools are available to its instructors and students. The approval process varies by institution but consistently involves:

- **Security review** — does the tool transmit student data? Where is it stored? Who has access? What encryption is used? FERPA compliance documentation is typically required.
- **Legal review** — data processing agreement (DPA) review. The institution's legal team reviews Medhavy's terms of service and data handling agreements. Many institutions require a signed DPA before any student data can flow through an LTI integration.
- **Accessibility review** — WCAG 2.1 AA compliance. Institutions in the US are subject to Section 508 requirements; many require a Voluntary Product Accessibility Template (VPAT) from the vendor before approving any tool.
- **IT security review** — penetration testing results, SOC 2 compliance, or equivalent security posture documentation.

At Rice University, the process is documented as requiring review in "accessibility, security, legal, and cost" dimensions. At UC Riverside, student data transmission through LTI requires explicit approval. At the University of Washington, a November 2024 freeze on all new LTI additions — lasting until March 2025 — was imposed to allow UW-IT to update its intake process.

### The timeline reality

Based on documented institutional processes, a realistic timeline for getting a new LTI tool approved at a single institution:

- Security and FERPA documentation prepared by Medhavy: 2-4 weeks
- Submission to institutional review queue: same day
- Institutional review cycle: 4-12 weeks (varies widely; smaller institutions are faster; large research universities are slower)
- DPA negotiation and execution: 2-8 weeks in parallel with review
- Canvas admin configuration: 1-2 days after approval

Total: 2-6 months from initial contact to first live students, depending on institution. This is the timeline that should drive when Medhavy starts the process, not when engineering is ready.

### Instructure's EdTech Collective

Instructure announced the EdTech Collective partner directory at InstructureCon 2024 — a public Canvas-integrated tool marketplace where institutions can browse vetted tools and see LTI configuration information. Being listed in the EdTech Collective provides:

- Discovery: institutions searching for AI tutoring tools find Medhavy
- Pre-vetting signal: listing implies a baseline of Instructure review
- Simplified installation: Canvas Apps Page integration means institutions can install from within Canvas rather than through manual configuration

Applying for EdTech Collective listing should be a parallel track to the engineering work. It is not a substitute for individual institutional approval but it reduces friction significantly.

### 1EdTech LTI Advantage certification

Canvas is certified LTI Advantage Complete (certification number in the 1EdTech TrustEd Apps Directory, originally certified June 2024, currently listed as out of date — institutions should verify with Instructure directly). For Medhavy as a tool provider, achieving 1EdTech LTI Advantage certification for Medhavy itself provides a credential that many institutional security reviewers recognize and that can accelerate the approval process. The certification requires passing the 1EdTech conformance test suite. This is engineering work but has outsized return in institutional sales cycles.

---

## 8. How the LTI layer interacts with Medhavy's existing architecture

### The Hub's current JWT flow is not replaced

Medhavy Hub currently issues 24-hour JWTs that textbooks validate against the Hub's `/api/access/verify` endpoint. This flow remains unchanged for direct Medhavy access (students bookmarking textbooks, institutions that are not Canvas users, instructors accessing the admin dashboard).

LTI 1.3 is an additional authentication pathway that gates into the same Hub user and access model. The flow for a Canvas-connected student:

1. Student clicks Medhavy link in Canvas → Canvas initiates LTI 1.3 launch
2. Medhavy validates the Canvas JWT → looks up or creates Medhavy user via LTI identity mapping table
3. Medhavy issues its own 24-hour textbook access JWT for the student → student lands in the textbook
4. All subsequent page loads: textbook validates the Medhavy JWT against Hub's existing `/api/access/verify` endpoint as before

The LTI layer is the front door for Canvas-sourced sessions. Once the user is in Medhavy, the existing session management takes over.

### New API routes required in Medhavy Hub

The LTI integration requires adding the following routes to Medhavy Hub:

**`GET /lti/openid-configuration`** — Returns Medhavy's OpenID configuration document. Required for Dynamic Registration. Contains Medhavy's JWKS URL, authorization endpoint, token endpoint, and supported scopes.

**`GET /lti/jwks`** — Returns Medhavy's public JWK set. Canvas uses this to verify JWTs that Medhavy sends during the Client Credentials Grant for AGS/NRPS service calls.

**`POST /lti/login`** — The OIDC initiation URL. Receives Canvas's login initiation request (step 1 of the auth flow), generates state and nonce, redirects to Canvas's authorization endpoint.

**`POST /lti/launch`** — The target link URI. Receives the signed JWT from Canvas (step 3 of the auth flow), validates it, looks up or creates the Medhavy user, issues a Medhavy session, and redirects to the appropriate textbook or resource.

**`POST /lti/deep-link`** — The Deep Linking endpoint. Presents the content selection UI and returns Deep Linking response content items to Canvas.

**`POST /lti/register`** — The Dynamic Registration endpoint. Handles the registration token exchange and returns the tool's registration response.

### Supabase schema additions

Beyond the LTI identity mapping table described in section 2, two additional tables:

**`lti_deployments`** — One row per Canvas course deployment. Stores the Canvas deployment ID, course ID, issuer, AGS line items endpoint, NRPS endpoint, and the Medhavy class ID it maps to.

```sql
lti_deployments (
  id                uuid primary key,
  canvas_deployment_id  text not null,
  canvas_course_id      text not null,
  canvas_iss            text not null,
  ags_endpoint          text,      -- Line items endpoint from launch JWT
  nrps_endpoint         text,      -- NRPS endpoint from launch JWT
  medhavy_class_id      uuid references classes(id),
  created_at            timestamptz not null,
  unique (canvas_deployment_id, canvas_iss)
)
```

**`lti_line_items`** — One row per Glimmer assignment that has grade passback enabled.

```sql
lti_line_items (
  id                    uuid primary key,
  lti_deployment_id     uuid references lti_deployments(id),
  canvas_line_item_url  text not null,  -- AGS line item endpoint from Canvas
  glimmer_assignment_id uuid references glimmer_assignments(id),
  score_maximum         numeric not null default 100,
  created_at            timestamptz not null
)
```

---

## 9. What the bandit's signal layer gains from LTI

The 2.0 contextual bandit requires clean per-student per-concept signals. LTI integration strengthens the signal layer in two ways not possible without it.

**Gradebook context as a signal.** When Glimmer assignments are connected to Canvas gradebook columns via AGS, Medhavy can read the current score distribution for an assignment across the class. This gives the bandit a class-level calibration signal: if 80% of students in this course have low Glimmer scores on mechanism, the bandit should offer more Case Study (which addresses application under ambiguity, building mechanism reasoning) before offering more Glimmer. Without the Canvas gradebook connection, this class-level signal requires aggregating Medhavy-internal Glimmer rubric scores, which is possible but less integrated.

**Assignment completion as an enrollment-level trigger.** With Platform Notification Service (PNS), Canvas can push notifications to Medhavy when a Canvas assignment is submitted or its due date passes. This gives the bandit a time-pressure signal: in the 48 hours before a Glimmer is due, the bandit should prioritize Quiz Me (ensuring retrievability is high before the generative task) over Case Study or more Glimmer preparation. Without LTI, this temporal context requires the instructor to manually set assignment dates in Medhavy as well as Canvas.

---

## 10. Build sequence for LTI integration

### Phase 1 — Core LTI 1.3 launch (prerequisite for everything else)

1. Generate RSA key pair for Medhavy's LTI signing identity; host public JWK at `/lti/jwks`
2. Implement OIDC login initiation handler at `/lti/login`
3. Implement JWT validation and user account lookup/creation at `/lti/launch`
4. Implement LTI identity mapping table and creation logic
5. Implement `lti_deployments` table and course context storage
6. Test against Canvas's test environment (Canvas provides a test environment at `canvas.test.instructure.com`)

Without Phase 1, nothing else works. It is the foundation.

### Phase 2 — NRPS roster sync

1. Implement OAuth 2.0 Client Credentials Grant for AGS/NRPS token acquisition
2. Implement NRPS roster pull and Medhavy class population
3. Implement scheduled roster sync (daily or event-triggered)
4. Map Canvas roles to Medhavy roles
5. Handle dropped students (Canvas status: Inactive)

Phase 2 eliminates the manual class invite flow for Canvas courses.

### Phase 3 — AGS grade passback for Glimmer

1. Implement line item creation via AGS
2. Implement score submission on Glimmer AI interrogation completion (PendingManual)
3. Implement score update on instructor grading (FullyGraded)
4. Implement submission data passback for SpeedGrader view
5. Add `lti_line_items` table

Phase 3 closes the gradebook loop.

### Phase 4 — Deep Linking

1. Implement `/lti/deep-link` endpoint
2. Build content selection UI (browse textbook by chapter and concept node)
3. Return appropriate content items (resource links, Glimmer assignments with AGS)
4. Configure `assignment_selection` and `link_selection` placements in Developer Key JSON

Phase 4 enables structured course delivery and is the prerequisite for Glimmer appearing as a Canvas assignment.

### Phase 5 — Dynamic Registration

1. Implement `/lti/register` Dynamic Registration endpoint
2. Implement OpenID configuration endpoint
3. Implement postMessage close signal to Canvas
4. Test with Canvas's Dynamic Registration flow
5. Apply for EdTech Collective listing

Phase 5 reduces per-institution installation friction from hours to minutes.

---

## 11. Decisions required before build begins

**Privacy level.** The Developer Key's privacy level determines what user data Canvas sends in LTI launches. `public` sends name and email; `anonymous` sends only an opaque user ID. Medhavy needs name and email to create useful accounts and to match LTI identities to existing Medhavy accounts. Set privacy level to `public`. This is a product decision, not just a configuration decision, because it affects what data Medhavy receives and must handle per FERPA.

**Grade passback granularity.** AGS can return a single numeric score per Glimmer assignment, or it can return scores for multiple line items (one per rubric dimension). A single composite score is simpler and matches Canvas's standard assignment model. Per-dimension scores would require five gradebook columns per Glimmer. The single composite score is the right default; the instructor's Medhavy dashboard shows the full rubric breakdown.

**Canvas-sourced class vs. Medhavy-native class.** When a Canvas course is connected via LTI, should Medhavy create a new Medhavy class automatically, or should the instructor manually link the Canvas course to an existing Medhavy class? Automatic creation is simpler for instructors but may create duplicate classes if an instructor already has a Medhavy class for the same course. The recommended approach: if no Medhavy class exists for this Canvas course ID, create one automatically. If one exists (matched by course ID stored in `lti_deployments`), link to it.

**Scope of NRPS access.** NRPS exposes the full course roster including students who have never interacted with Medhavy. This is useful for the instructor dashboard (showing which enrolled students have not started) but raises FERPA implications for storing data about students who have not consented to Medhavy's data handling by visiting the platform. The conservative approach: store NRPS roster data only in the `lti_deployments` context, do not create Medhavy user accounts for students until they first launch. The account creation moment is the functional consent event.

---

## Key references

Instructure Developer Documentation. "External Tools Introduction." https://developerdocs.instructure.com/services/canvas/external-tools/lti/file.tools_intro

Instructure Developer Documentation. "Configuring LTI Advantage Tools." https://canvas.instructure.com/doc/api/file.lti_dev_key_config.html

Instructure Developer Documentation. "LTI Advantage: Assignment and Grading Services." https://developerdocs.instructure.com/services/canvas/external-tools/lti/file.assignment_tools

Instructure Developer Documentation. "Names and Role Provisioning Services." https://developerdocs.instructure.com/services/canvas/external-tools/lti/file.provisioning

Instructure Developer Documentation. "LTI Registration (Dynamic Registration)." https://developerdocs.instructure.com/services/canvas/external-tools/lti/file.registration

1EdTech Consortium. "LTI 1.3 and LTI Advantage Specification." https://www.imsglobal.org/spec/lti/v1p3/

1EdTech Consortium. "Assignment and Grade Services v2.0." https://www.imsglobal.org/spec/lti-ags/v2p0/

1EdTech Consortium. "Names and Role Provisioning Services v2.0." https://www.imsglobal.org/spec/lti-nrps/v2p0/

1EdTech Consortium. "Deep Linking 2.0." https://www.imsglobal.org/spec/lti-dl/v2p0/

Edlink. "Does Canvas Support LTI 1.3 & LTI Advantage?" https://ed.link/community/does-canvas-support-lti-1-3-lti-advantage/

Instructure. "Everything You Need to Know About Our LTI Optimizations: Updates, Releases, and Efficiencies." Canvas Community Blog, March 2025.

Instructure. "InstructureCon 2024: EdTech Collective and Canvas Apps Page announcements." Press release, July 2024.
