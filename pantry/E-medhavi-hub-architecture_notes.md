# Research Notes — Appendix E: The Medhavi Hub — Architecture Reference

*Technical reference appendix for the Medhavy book. Synthesises existing pantry content (`medhavy-1.5-feature-roadmap-complete.md`, `04-the-four-layers_notes.md`, `12-the-design-conversation_notes.md`, `PEDAGOGY ARCHITECTURE.txt`, `MVAL.txt`) with targeted verification of the canonical 2025–2026 patterns for Clerk + Supabase integration, dynamic CORS in Next.js 14 App Router, and Supabase service role key security best practices. Compiled 2026-05-17 for Cowork to compile against pantry.*

> **Critical flag at top.** TIKTOC §Appendix E lists `API.md` and `ARCHITECTURE.md` as primary pantry sources. **Neither file exists in `books/medhavy/pantry/`.** The pantry scan (2026-05-17) returns no `API.md` artifact and no `ARCHITECTURE.md` artifact. The Ch 4 notes (`04-the-four-layers_notes.md` §H, flag #3) and Ch 12 notes (`12-the-design-conversation_notes.md` §1.1 header) both *reference* these documents but neither contains the actual schemas, endpoint specifications, or system diagrams. The Ch 12 notes header text — *"Companion to `PEDAGOGY ARCHITECTURE.txt`, `MVAL.txt`, `Lexicon.txt`, the Medhavi Hub `ARCHITECTURE.md` / `API.md`..."* — implies they once existed in some Medhavy-internal location but were not copied into the pantry. **Action requested of the author:** confirm whether the Medhavi Hub `ARCHITECTURE.md` and `API.md` files can be copied into pantry from a private Medhavi repo, or approve the reconstruction below (which is built from the roadmap document plus the architecture-level claims in `04-the-four-layers_notes.md` and `12-the-design-conversation_notes.md`).

> **Second flag at top.** The pantry roadmap document specifies the platform-as-it-exists (Ask AI, Cancer Biology + Physics Vol. 1 deployments, Mixture-of-Experts routing) but does **not** include database schemas, API endpoints, or auth flow diagrams. The reconstruction below is therefore **architecturally licensed** — it specifies the canonical Clerk + Supabase + Next.js + AWS S3 + PostHog stack that the platform descriptions imply, but the **specific table schemas, endpoint signatures, and routing rules in §D and §G below are pattern-derived, not document-derived**. The appendix author should treat these as a *starting specification the developer reviews against the actual deployed code* rather than as a copy of the deployed schema.

---

## A. Appendix scope — what this appendix delivers and to whom

Appendix E is the system-architecture reference for the developer reading the book. The Charles Fadel type can skip it; the developer who is about to build on or extend the Medhavi Hub cannot.

The appendix delivers, in roughly 3,500–4,500 words:

1. **The system context.** What the Medhavi Hub is, what it talks to, and what is hosted on it. A textual description of the diagram that would appear in `ARCHITECTURE.md`.
2. **The tech stack, named precisely.** Next.js for the application layer, Clerk for identity, Supabase (Postgres) for application data, AWS S3 for content storage, PostHog for product analytics. Why each was chosen and what the alternatives were.
3. **The auth architecture.** How a user logs in via Clerk, how the Clerk JWT propagates to Supabase, how Row Level Security (RLS) policies on Supabase are gated on Clerk claims, how logout invalidates session state across both systems, and how the CORS strategy handles the multi-textbook deployment model.
4. **The textbook access decision tree.** The runtime resolution of "does this user have access to this textbook?" — the load-bearing piece of the access-control story.
5. **Database schema summary.** Core tables (users, textbooks, classes, sessions), analytics tables (events, signal capture for the GLP measurement layer), and concept-map tables (nodes, prerequisites, mode-appropriateness flags, outcomes).
6. **Key design decisions, defended.** Why Clerk for identity and Supabase for data rather than Supabase Auth alone; why dynamic CORS rather than a static allow-list; why the service role key is used (and what is done to keep it safe).
7. **API reference summary.** The five top-level endpoint groups (access, textbooks, classes, analytics, memory) at the level of detail a developer needs to plan a build, not to write the calls verbatim.
8. **The concept-map editor workflow.** Pipeline → session → node review → export to S3. The workflow the Tic TOC instrument (Ch 12) drives.

The appendix is *not* a complete API specification. The complete spec lives in the (currently absent) `API.md`. The appendix is the developer's orientation document — enough to start building, with the canonical reference document as the next stop.

---

## B. System context — what the Medhavi Hub is

The Medhavi Hub is the **platform infrastructure** that hosts a portfolio of intelligent textbooks. Each textbook (Cancer Biology, Physics Vol. 1, the deployments named in `medhavy-1.5-feature-roadmap-complete.md`) is an instance running on shared platform services — auth, content storage, analytics, concept-map management. The Hub provides what no single textbook deployment is in a position to provide: cross-textbook identity, shared instrumentation, and a single audit surface for the engagement-trap defence Ch 7 argues for.

The Hub's relationship to the four layers Ch 4 names:

- **Layer 1 (Book Library).** The Hub hosts the textbook content in S3 with metadata in Supabase. Each textbook is a registered tenant; per-tenant content is namespaced.
- **Layer 2 (Curriculum Design / Tic TOC).** The Hub hosts the concept-map editor and stores the concept-map artefacts (nodes, prerequisite edges, Bloom-level tags, mode-appropriateness flags) in Supabase tables. The Tic TOC instrument (Ch 12) reads and writes through Hub APIs.
- **Layer 3 (Adaptive Engine).** The Hub hosts the per-learner per-arm posterior state (Appendix D's bandit) and the policy-update endpoints. The within-learner discipline is implemented as per-user-per-textbook-per-concept rows in Supabase.
- **Layer 4 (Measurement / GLP).** The Hub captures the seven GLP component signals (Y1..Y7) per session via instrumented events to PostHog and structured rows in Supabase. The seven-day delayed-probe scheduling is the Hub's responsibility, not the textbook deployment's.

The Hub is the "platform" in "the platform is opinionated, the model has no opinions of its own" (`medhavy-1.5-feature-roadmap-complete.md` closing). The opinions live in the schema, the access control, and the audit discipline — not in the LLM call.

### B.1 System context diagram — textual description

The diagram that would appear in `ARCHITECTURE.md`:

- **Top tier — Users.** Three classes: students (the learners), instructors (faculty managing classes), authors (the Charles Fadel type producing concept maps). Each enters the system through a Next.js application served by the Hub.
- **Middle tier — Medhavi Hub.** A Next.js 14 (App Router) application deployed to Vercel `[verify]` (or comparable Node hosting). The Hub serves the textbook UIs, runs the per-session mode-selection logic, and hosts the concept-map editor. Internal to the Hub: API routes for access, textbook registry, class management, analytics ingestion, and memory (per-learner GLP state).
- **Identity provider — Clerk.** External-managed identity. Provides JWT-signed session tokens. Configured as a third-party JWT issuer for Supabase. Clerk's hosted UI handles sign-in / sign-up / MFA.
- **Application database — Supabase (Postgres).** Stores all relational data: users (mirrored from Clerk), tenants (textbook deployments), textbook registry, classes, enrollments, concept-map nodes and edges, per-learner posterior state, session logs, GLP signal rows, audit logs. Row-Level Security policies gate all reads and writes on Clerk JWT claims.
- **Content store — AWS S3.** Stores immutable textbook content (chapter HTML, video and animation assets, concept-map exports). Signed URLs serve content to authenticated users.
- **Product analytics — PostHog.** Captures user-event telemetry for the seven GLP component signals (timestamps, click streams, mode transitions). PostHog data is consumed by the bandit's within-session reward update and by the platform team's drift audit.
- **AI providers — OpenAI / Anthropic.** Called server-side by the Hub for Ask AI, Case Study facilitation, and Glimmer pre-grading. Never called client-side. The TEXTBOOK_ONLY constraint (`PEDAGOGY ARCHITECTURE.txt` §5) is enforced at the Hub's prompt-construction layer.

The data flow on a typical learner session:

1. Learner authenticates via Clerk → receives JWT.
2. Browser loads the textbook UI from Vercel-hosted Next.js.
3. Browser calls Hub API endpoints with the Clerk JWT in `Authorization: Bearer <token>`.
4. The Hub's API routes verify the JWT (via Clerk JWKS endpoint, or via Supabase's native Clerk integration).
5. The Hub reads the user's per-textbook access state from Supabase (RLS policy filters on the Clerk `sub` claim).
6. The Hub computes the mode selection via the Appendix D bandit (per-learner posterior in Supabase).
7. The Hub returns the mode selection and the next interaction payload.
8. The Hub instruments PostHog events as the session proceeds.
9. At session end, the Hub computes Y1..Y7, writes them to Supabase, and updates the per-learner posterior (Appendix D §E).
10. The Hub schedules the seven-day delayed probe via a Supabase scheduled job or Vercel cron `[verify]`.

---

## C. Tech stack — the canonical 2025–2026 choices

### C.1 Next.js

**Next.js 14+ App Router** ([Next.js documentation](https://nextjs.org/docs/app/api-reference/file-conventions/route)). The App Router pattern (file-system routing, React Server Components, server-side rendering by default, Route Handlers for API endpoints) is the canonical Next.js architecture as of 2025–2026. The Hub's API routes are implemented as Route Handlers in the `app/api/*` tree.

**Rationale for Next.js over alternatives:** The Hub serves both interactive UI (concept-map editor; per-textbook learner interface) and API endpoints (Hub APIs the textbook UIs call). Next.js handles both surfaces in one deployment with server-side rendering and React Server Components — the cost of running the same auth-checking, JWT-verification, and RLS-claim-extraction logic on every request is amortised because the same Next.js process handles the UI and the API. The alternative (separate React frontend + separate Express/Fastify backend) doubles the deployment surface without proportional benefit for the Hub's request mix.

### C.2 Clerk for identity

**Clerk** ([clerk.com](https://clerk.com)) is the identity provider. Clerk handles sign-in, sign-up, MFA, password reset, OAuth federation, and session management. Clerk issues signed JWTs that downstream services (Supabase, the Hub itself) verify against Clerk's JWKS endpoint.

**The 2025 canonical integration pattern with Supabase:** As of April 2025, [Clerk and Supabase officially deprecated the older JWT-template pattern](https://clerk.com/docs/guides/development/integrations/databases/supabase) (which required Clerk to share a Supabase JWT secret and rewrite JWTs to look like Supabase-issued JWTs) and switched to **Supabase's native third-party JWT verification**. In the new pattern:

- Clerk is registered with Supabase as a **third-party JWT issuer**.
- Clerk issues JWTs with the canonical `role: "authenticated"` claim (Supabase's RLS gate).
- Supabase verifies the Clerk JWT directly against Clerk's JWKS endpoint — no shared secret, no JWT rewriting.
- RLS policies on Supabase tables reference Clerk JWT claims via the standard Postgres JWT-claim functions.

**Why this matters for the Hub.** Under the old pattern, every Supabase request required Clerk to mint a new Supabase-shaped JWT — adding a network hop and shared-secret management. Under the new pattern, the Clerk JWT travels straight through from browser to Supabase, the Hub's API routes can read the same JWT, and the Supabase JWT secret is no longer shared with Clerk. The new pattern is the **2025+ canonical reference** and the Hub should run on it.

**Rationale for Clerk over Supabase Auth alone.** Supabase Auth is functional but Clerk's hosted UI, MFA infrastructure, and OAuth federation are more mature; the integration cost (now zero JWT-secret-sharing under the native pattern) is low; the failure mode of Supabase Auth being temporarily wedged is decoupled from data-layer Supabase availability. The split (Clerk for identity, Supabase for data) is the platform's "*Clerk handles who, Supabase handles what*" design decision.

### C.3 Supabase for application data

**Supabase** (managed Postgres + Row Level Security + Realtime + Storage) is the application database. All relational data lives in Supabase: users (mirrored from Clerk via webhook), tenants (textbook deployments), textbook registry, classes, concept-map nodes/edges, per-learner bandit state, session logs, GLP signal rows.

**Why Supabase rather than raw Postgres on RDS.** Three reasons:

1. **Row-Level Security gates on JWT claims.** Supabase's first-class RLS implementation lets the Hub express access policy as Postgres policies referencing Clerk JWT claims — `auth.jwt() ->> 'sub' = users.clerk_id` is the recurring pattern. The same policy enforces access for client-side queries (Supabase JS SDK from the browser) and server-side queries (Hub API routes). One source of truth for access.
2. **Realtime subscriptions for the editor.** The concept-map editor (Ch 8 / Ch 12) is a multi-user collaborative tool. Supabase Realtime delivers Postgres change-data-capture to subscribed clients with minimal engineering.
3. **Managed Postgres with the security retros published.** [Supabase's 2025 Security Retro](https://supabase.com/blog/supabase-security-2025-retro) and the [secret-key rotation guidance](https://supabase.com/docs/guides/troubleshooting/performing-administration-tasks-on-the-server-side-with-the-servicerole-secret-BYM4Fa) name the operational discipline the platform team commits to. The current platform default is the **new secret-key model** (replacing the older JWT-based service-role key), with automatic GitHub-public-leak detection and revocation.

### C.4 AWS S3 for content storage

**AWS S3** holds the immutable textbook content: chapter HTML, video and animation assets, concept-map JSON exports. The Hub mints signed URLs scoped to (user, textbook, expiration window) for content delivery.

**Why S3 rather than Supabase Storage.** The Hub may eventually serve content at multi-GB scale per textbook (video and animation assets in particular). S3's egress pricing and CloudFront integration are the standard production pattern; Supabase Storage is convenient for prototype-scale assets but is not the right tier for terabyte-scale media. The cost-collapse argument in Ch 9 (AI-generated video at $5/unit) means the content library will grow much faster than the application database, which justifies the split.

### C.5 PostHog for product analytics

**PostHog** captures user-event telemetry. The seven GLP component signals (Y1..Y7) are computed from PostHog event streams (timestamps, dwell time, scroll position, mode-transition events, hint requests). PostHog's session-recording feature is *not* used (the consent architecture in Ch 11 closes that off); only structured events are captured.

**Why PostHog rather than Mixpanel / Amplitude.** PostHog's open-source posture and self-hosting option support the "consent architecture" Ch 11 names — the platform commits to what data it collects and what it does not; self-hostable analytics keeps the commitment auditable. Mixpanel / Amplitude are closed third-party SaaS; PostHog can be deployed inside the Hub's own infrastructure if the deployment requires it.

---

## D. Auth architecture — the JWT flow, the CORS strategy, logout invalidation

### D.1 The JWT flow

The canonical pattern (under the 2025 native Clerk-Supabase integration):

1. **User signs in via Clerk's hosted UI.** Clerk issues a JWT signed by Clerk's private key. The JWT contains the standard Clerk claims (`sub` = Clerk user ID, `sid` = session ID, `iat`, `exp`, plus any custom claims the Hub configured) and the Supabase-required `role: "authenticated"` claim.
2. **The JWT is stored client-side** in Clerk's secure cookie / localStorage (depending on Clerk's chosen storage strategy).
3. **The browser includes the JWT** in every Hub API call as `Authorization: Bearer <jwt>`. The same JWT is included in every Supabase query (via the Supabase JS SDK's `setAuth(token)` method or the equivalent).
4. **The Hub API verifies the JWT** server-side by fetching Clerk's public keys from the JWKS endpoint and verifying the signature. The Hub can do this in its API route or via Clerk's official Node SDK.
5. **Supabase verifies the JWT** independently using its native Clerk integration: Supabase fetches Clerk's JWKS, verifies the JWT signature, and exposes the JWT claims to RLS policies via `auth.jwt()`.
6. **RLS policies filter data** based on the JWT claims. Example: `CREATE POLICY "users can read their own sessions" ON sessions FOR SELECT USING (auth.jwt() ->> 'sub' = clerk_user_id)`.

Two important properties:

- **No JWT rewriting.** The Clerk JWT travels unchanged from browser to Supabase.
- **No shared JWT secret.** Clerk's private signing key never leaves Clerk; Supabase verifies against Clerk's public key via JWKS.

### D.2 Logout invalidation

A subtle issue: JWTs are stateless. Logging out client-side (deleting the cookie) does not invalidate the JWT itself — the JWT remains valid until its `exp` timestamp.

The platform's logout strategy:

1. **Client-side logout.** Clerk's logout flow deletes the cookie / localStorage. The browser can no longer present the JWT.
2. **Clerk session invalidation.** Clerk's session management invalidates the session ID (`sid` claim) server-side. Subsequent Hub API calls that verify the JWT can check the `sid` against Clerk's session-status endpoint and reject revoked sessions.
3. **Short JWT lifetimes.** Clerk default JWT lifetime is short (1 minute by default, with auto-refresh). A revoked session's JWT expires fast.
4. **Audit logging.** The Hub logs every logout event with the user's Clerk ID and the session ID. Re-presentation of a revoked JWT is flagged.

Logout invalidation under stateless JWTs is *not* immediate-and-perfect; it is short-window-and-auditable. This is the trade the platform accepts for the simplicity of JWT-based auth.

### D.3 Dynamic CORS strategy

The Hub is a multi-tenant platform: textbook deployments may be served from per-tenant subdomains (cancer.medhavy.com, physics.medhavy.com) or per-tenant custom domains. The CORS allow-list cannot be static; it must be resolved at request time based on the tenant registry.

The canonical 2025 Next.js 14 App Router pattern for dynamic CORS ([Next.js docs](https://nextjs.org/docs/app/api-reference/file-conventions/route); [vercel/next.js discussion #52933](https://github.com/vercel/next.js/discussions/52933)):

- **Middleware-based dynamic CORS.** A `middleware.ts` file at the project root intercepts all requests. It reads the `Origin` header, queries the Supabase tenant registry for whether that origin is a registered tenant, and sets the `Access-Control-Allow-Origin` header dynamically.
- **Per-route handlers.** Each API route exports an `OPTIONS` handler that responds to preflight requests with the appropriate CORS headers. The Route Handler pattern (`app/api/.../route.ts`) supports per-route OPTIONS.
- **Strict origin matching, not wildcards.** The Hub does not respond with `Access-Control-Allow-Origin: *` for credentialed requests. It echoes the exact origin from the request, after verifying that origin is in the tenant registry.

The architectural reason for dynamic CORS: the platform is *opinionated* about which origins can call its APIs. A request from an unknown origin gets no CORS headers; the browser blocks the response. A request from a registered tenant gets the exact tenant's origin echoed. The tenant registry is the auth-adjacent control surface — and it is gated on the same Supabase RLS that gates user-data access.

### D.4 The TEXTBOOK_ONLY constraint at the auth layer

`PEDAGOGY ARCHITECTURE.txt` §5 names the constraint: institutional white-label deployments enforce `textbookOnly: true`, which means the AI cannot answer questions outside the indexed textbook content. The constraint is implemented at multiple layers:

- **Server-side prompt construction.** The Hub never passes the user's raw question to the LLM without RAG-grounding it in the current textbook. The grounding step is non-bypassable from the client.
- **Tenant-config flag.** `tenant.config.textbook_only = true` in Supabase. Reads of the flag happen on every LLM call; the value cannot be hot-overridden by the client.
- **Audit hook.** Every LLM call logs the tenant config it ran under. The platform team can verify post-hoc that the constraint was honoured.

---

## E. Textbook access decision tree

The runtime resolution of "does this user have access to this textbook?" — a load-bearing piece of the architecture.

The decision tree:

```
on access_request(user_id, textbook_id):
    # 1. Verify the JWT (handled at API-route entry; aborts on failure)
    
    # 2. Direct entitlement?
    if exists(user_textbook_entitlement(user_id, textbook_id)):
        return ALLOW
    
    # 3. Class enrollment?
    classes = enrolled_classes(user_id)
    for class in classes:
        if class.textbook_id == textbook_id:
            return ALLOW
    
    # 4. Tenant-wide free access?
    tenant = textbook_tenant(textbook_id)
    if tenant.access_policy == 'free':
        return ALLOW
    
    # 5. Trial / preview?
    if textbook.trial_enabled and not user.trial_consumed(textbook_id):
        record_trial_consumption(user_id, textbook_id)
        return ALLOW_TRIAL
    
    # 6. Default deny
    return DENY
```

Two implementation notes:

- **The decision tree is implemented as RLS on Supabase**, not as application logic on the Hub. The `textbook_access` view computes the decision; the application layer reads from the view. This means the access decision is enforced by Postgres regardless of which path of the application stack issued the read — a defense-in-depth move.
- **The trial logic is deliberately bounded.** A user can consume one trial per textbook. The trial entitlement is recorded as an audit event; the platform team can detect abuse patterns.

---

## F. Database schema — core tables, analytics tables, concept map tables

The full schema lives in `ARCHITECTURE.md` (currently absent — see flag #1). The appendix's role is to summarise the table families and the load-bearing relationships, not to reproduce DDL.

### F.1 Core tables

| Table | Key columns | Purpose |
|-------|-------------|---------|
| `users` | clerk_id (PK), email, display_name, created_at | Mirror of Clerk users. Populated by Clerk webhook on sign-up. |
| `tenants` | id (PK), slug, name, config (jsonb), access_policy | Textbook deployments. One tenant per institutional white-label or per public textbook. |
| `textbooks` | id (PK), tenant_id (FK), slug, title, version | Each textbook is one tenant's primary content. A tenant may host multiple textbooks (Cancer Biology + Physics Vol. 1 example). |
| `entitlements` | user_id, textbook_id, granted_at, source | Direct user-textbook access grants. |
| `classes` | id, tenant_id, textbook_id, instructor_id, name | Instructor-managed cohorts. |
| `enrollments` | user_id, class_id, role | Student / TA / observer roles in a class. |
| `sessions` | id, user_id, textbook_id, concept_id, mode, started_at, ended_at | Every learner session. |

### F.2 Analytics tables

| Table | Key columns | Purpose |
|-------|-------------|---------|
| `glp_signal_rows` | session_id, component (Y1..Y7), value, computed_at | The seven GLP component signals per session. Computed at session end. Drives the bandit's within-session reward update. |
| `delayed_probes` | id, session_id, scheduled_at, due_at, completed_at, accuracy | The seven-day delayed retrieval probe events. Drives the bandit's delayed-reward update (Appendix D §E.1). |
| `events` | id, user_id, type, payload (jsonb), occurred_at | Raw event stream. Indexed feed into PostHog and into the GLP signal computation. |
| `mval_log_entries` | id, author_id, what, why, how, environment, results, questions, created_at | The MVAL six-field analytical log (`MVAL.txt`). Used by the platform team for the drift audit (Appendix D §F). |

### F.3 Concept-map tables

| Table | Key columns | Purpose |
|-------|-------------|---------|
| `concept_nodes` | id, textbook_id, slug, title, bloom_level, mode_flags (bitmap) | One row per concept in the textbook's concept map. Mode flags constrain bandit arm eligibility (Appendix D §B.1). |
| `concept_edges` | from_id, to_id, edge_type | Prerequisite dependencies and other typed edges in the concept DAG. |
| `concept_outcomes` | id, concept_id, statement, bloom_level | One or more outcome statements per concept (Ch 8 deliverable). Drives item generation for the seven-day delayed probe. |
| `concept_assessments` | id, concept_id, type, payload (jsonb) | Quiz Me item templates, Case Study scenario specs, Glimmer rubrics. The "minimum viable content" for each mode per concept. |
| `bandit_posteriors` | user_id, textbook_id, concept_id, arm, mean, precision_matrix (bytea) | Per-learner per-arm Bayesian-regression posterior over reward function weights. The bandit's state lives here. |

The `bandit_posteriors` table is the load-bearing piece for Appendix D. Every session-end update writes a new posterior row (versioned by `updated_at`); the audit discipline reads the version history to detect drift.

---

## G. Key design decisions, defended

### G.1 Clerk for identity, Supabase for data

The split is principled rather than incidental:

- **Identity is a specialised problem.** MFA, OAuth federation, session revocation, password recovery, abuse detection — Clerk does these at production quality. Building them on top of Supabase Auth is not impossible but the engineering cost is non-trivial and the failure modes are dangerous.
- **Data access is a Postgres problem.** Supabase's RLS-on-Postgres is the cleanest way to enforce row-level access against JWT claims. Rebuilding the same on top of raw Postgres + custom middleware is the bolt-on failure (Ch 4) at the database layer.

The 2025 canonical integration pattern (§C.2 above) makes the split cheaper than ever — no shared secrets, no JWT rewriting, no per-request JWT minting.

### G.2 JWT-based auth vs. proxied sessions

The alternative to JWT-based auth: every API call to Supabase is proxied through the Hub, the Hub holds a stateful session (server-side cookie store), and the Hub makes Supabase calls under the service role key with `set_config('request.jwt.claims', ...)` to spoof the user context.

This pattern works but trades:

- **Pro:** Server-side session invalidation is immediate (the Hub forgets the session).
- **Con:** Every Supabase call requires an extra hop through the Hub; the Hub becomes a load-bearing intermediary; the service role key is used on every request (multiplying the attack surface if the Hub is compromised).

The platform's choice (JWT-based auth, native Clerk-Supabase integration) accepts the short-window logout-invalidation trade in exchange for direct browser → Supabase queries and minimised service-role-key usage. Under the [2025 Supabase security retro](https://supabase.com/blog/supabase-security-2025-retro), this is the **recommended pattern**.

### G.3 Dynamic CORS

Addressed in §D.3. The justification is multi-tenancy: a static allow-list cannot accommodate per-tenant custom domains; the tenant registry is the authoritative source of which origins are allowed; dynamic CORS reads the registry on every request.

### G.4 Service role key — usage and protection

The **Supabase service role key** (or, under the new model, the **secret key** — see [Supabase Service Role: Deep Dive & Secure Usage](https://supabase.com/docs/guides/troubleshooting/performing-administration-tasks-on-the-server-side-with-the-servicerole-secret-BYM4Fa)) is the privileged credential that bypasses RLS. It is used by the Hub's server-side jobs (the bandit posterior update, the scheduled delayed-probe trigger, the audit log writer, the Clerk webhook receiver).

**The 2025 security best practices** the platform commits to ([Supabase docs on API keys](https://supabase.com/docs/guides/api/api-keys); [Supabase security retro](https://supabase.com/blog/supabase-security-2025-retro)):

1. **Server-side only.** The service role key is never sent to the browser, never embedded in client code, never logged. The Hub's API routes are the only consumer.
2. **Environment-variable storage.** The key lives in the Hub's deployment environment (Vercel secrets, AWS Secrets Manager, or equivalent), never in source control.
3. **Periodic rotation.** Quarterly rotation as the baseline; immediate rotation on any suspected compromise.
4. **Use the new secret-key model.** The JWT-based service_role key (deprecated as of the 2025 Supabase security update) is replaced with the new secret-key model: secret keys cannot be used in the browser (matches on the `User-Agent` header), and public-GitHub-leak detection auto-revokes leaked keys.
5. **Audit-trail every privileged operation.** Every service-role-key call is logged with the operation, the user context it spoofed, and the result. The MVAL discipline applies.

The platform's defense is layered: RLS for user-scoped reads/writes (cannot be bypassed without the service role key); the service role key for platform-level jobs (used in narrow code paths under audit); environment-variable storage with rotation discipline (limits blast radius on compromise).

---

## H. API reference summary — five endpoint groups

The full spec lives in `API.md` (currently absent — see flag #1). The appendix should summarise the five top-level groups at the resolution a developer needs to plan.

### H.1 `/api/access` — access control

- `GET /api/access/textbook/:textbook_id` → returns `{allowed: bool, source: 'entitlement' | 'class' | 'trial' | 'free' | 'deny'}`. Runs the §E decision tree.
- `POST /api/access/trial/:textbook_id` → records a trial consumption; returns the trial entitlement.
- `GET /api/access/me` → returns the current user's full entitlement map.

### H.2 `/api/textbooks` — textbook registry

- `GET /api/textbooks` → list textbooks the current user can see.
- `GET /api/textbooks/:slug` → textbook metadata (title, version, table of contents, available modes).
- `GET /api/textbooks/:slug/concepts` → the concept map for the textbook.
- `GET /api/textbooks/:slug/concepts/:concept_id` → individual concept node, including prerequisite list and mode flags.

### H.3 `/api/classes` — class management

- `GET /api/classes` → list classes the current user is enrolled in or instructs.
- `POST /api/classes` → create a class (instructor scope).
- `POST /api/classes/:id/enroll` → enroll students.
- `GET /api/classes/:id/progress` → class-level dashboard data.

### H.4 `/api/analytics` — event capture and signal ingestion

- `POST /api/analytics/event` → ingest a single learner-interaction event. Forwarded to PostHog; written to Supabase `events`.
- `POST /api/analytics/session_end` → close a session; trigger Y1..Y7 computation; write to `glp_signal_rows`; trigger bandit posterior update.
- `GET /api/analytics/audit/weight_history` → platform-team-only endpoint; returns the bandit's reward-weight history for drift detection.

### H.5 `/api/memory` — per-learner GLP state

- `GET /api/memory/concepts` → per-learner mastery state across all concepts the learner has touched.
- `GET /api/memory/due` → Quiz Me due-today list for the learner (the Zeigarnik-closure UI variable Ch 6 names).
- `POST /api/memory/probe_response` → record a seven-day delayed-probe response; trigger bandit delayed-reward update.

---

## I. Concept-map editor workflow

The concept-map editor is the runtime instrument the Tic TOC design conversation (Ch 12) drives. The workflow:

1. **Pipeline.** The author (Charles Fadel type) starts a design session. The Hub creates a `tic_toc_session` row tied to the author's user ID and the target textbook.
2. **Session.** The Hub guides the author through the six design-conversation moves (`12-the-design-conversation_notes.md` §4): intake → learner profile → complexity threshold → evidence audit → four-layer specification → economics check → honest inventory. Each move's output is stored as a `tic_toc_artefact` row keyed to the session.
3. **Node review.** The Hub renders proposed concept nodes for author review. The author can edit, accept, reject, or split. Edits are versioned; rejections are logged with reason.
4. **Edge construction.** The Hub proposes prerequisite edges from the curriculum-design literature (`08-the-curriculum-design-layer_notes.md` §C.4 — BKT/DKT-derived heuristics on prerequisite identification). The author reviews edge-by-edge.
5. **Bloom-level and mode-flag assignment.** Per node. The Hub proposes defaults; the author confirms or overrides.
6. **Outcome statements.** Per node. The author writes the outcome statement; the Hub validates that the verb matches the Bloom level (an Apply outcome must use an apply-verb).
7. **Assessment specifications.** Per concept and per mode. The author authors Quiz Me item templates, Case Study scenario specs, Glimmer rubrics.
8. **Export to S3.** When the author marks the concept map complete, the Hub serialises it (concept nodes + edges + outcomes + assessments + Bloom levels + mode flags) as a versioned JSON document and writes it to S3. The corresponding Supabase rows (`concept_nodes`, `concept_edges`, etc.) are updated atomically.
9. **Audit gate.** Before the concept map goes live for learners, a faculty reviewer (or, in solo deployments, the author after a 24-hour cooling period) signs off. The signoff is recorded as an audit event.

The workflow is the runtime instantiation of the Tic TOC methodology Ch 12 specifies. The Hub's editor is the *instrument* (Ch 12's distinction); the resulting concept map populates the *platform* (the textbook that learners interact with).

---

## J. Cross-reference to existing pantry — cite by exact filename

- `medhavy-1.5-feature-roadmap-complete.md` — primary source for the platform-as-it-exists (Ask AI, Cancer Biology + Physics Vol. 1 deployments, Mixture-of-Experts routing, the Brutalist pipeline for Video and Animation production). Appendix should cite §"The platform as it exists today" and §"Appendix — Medhavy 2.0: the contextual bandit".
- `04-the-four-layers_notes.md` — primary source for the four-layer integration argument that maps onto the Hub's architecture (§B.1 above). The seven signals enumeration in §B of that note is the operational rationale for the analytics tables in §F.2 above.
- `12-the-design-conversation_notes.md` — primary source for the platform-vs-instrument distinction (§3 of that note), the six design-conversation moves the editor workflow implements (§4 of that note), and the worked-example labelling discipline.
- `PEDAGOGY ARCHITECTURE.txt` — primary source for the TEXTBOOK_ONLY constraint (§5 of that document), the cold-start `pedagogy.default` fallback (§4), and the per-tenant configuration of the bandit. Appendix should cite directly for the §D.4 constraint enforcement.
- `MVAL.txt` — primary source for the analytical-log discipline that the audit hooks in §G.4 implement. The six-field structure (WHAT/WHY/HOW/ENVIRONMENT/RESULTS/QUESTIONS) is the table-row schema for `mval_log_entries` in §F.2.
- Appendix C (GLP Technical Specification — separate appendix) supplies the Y1..Y7 component specifications; this appendix references but does not reproduce.
- Appendix D (Contextual Bandits — sibling appendix) supplies the bandit's mathematical formulation; this appendix specifies where the bandit's state is *stored* (`bandit_posteriors` table) but does not re-derive the algorithm.

---

## K. Targeted verification — the 2025–2026 canonical patterns

Three light verification checks confirmed the canonical patterns referenced in the appendix above:

1. **Clerk + Supabase JWT integration (April 2025+).** [Clerk's documentation](https://clerk.com/docs/guides/development/integrations/databases/supabase) and [Supabase's third-party Clerk integration docs](https://supabase.com/docs/guides/auth/third-party/clerk) both confirm the native pattern (Supabase verifies Clerk JWTs directly via JWKS, no shared secret). The older JWT-template pattern is deprecated as of April 1, 2025. The companion repository [clerk/clerk-supabase-nextjs](https://github.com/clerk/clerk-supabase-nextjs) provides the canonical Next.js integration sample.
2. **Dynamic CORS in Next.js 14+ App Router.** Confirmed via [Next.js docs on Route Handlers](https://nextjs.org/docs/app/api-reference/file-conventions/route), the [vercel/next.js GitHub discussion #52933](https://github.com/vercel/next.js/discussions/52933), and the [Next.js 14 CORS implementation patterns guide](https://www.dhiwise.com/post/nextjs-cors-implementing-cross-origin-resource-sharing). The middleware-based dynamic-origin pattern (origin echoed from a registry, not wildcarded) is the production-canonical approach for credentialed multi-tenant requests.
3. **Supabase service role key best practices (2025).** Confirmed via [Supabase API keys docs](https://supabase.com/docs/guides/api/api-keys), the [2025 Security Retro](https://supabase.com/blog/supabase-security-2025-retro), and the [service-role secret-key troubleshooting guide](https://supabase.com/docs/guides/troubleshooting/performing-administration-tasks-on-the-server-side-with-the-servicerole-secret-BYM4Fa). The current canonical pattern: secret-key model (replacing the older JWT-based service_role key), server-side-only, environment-variable storage, periodic rotation, public-GitHub-leak auto-revocation.

The patterns in §C, §D, and §G are aligned with these 2025–2026 production-canonical references.

---

## L. Gaps, flags, verify items

### L.1 Top flags for the appendix author

1. **`ARCHITECTURE.md` and `API.md` are missing from pantry.** TIKTOC names them; the files are not present. The §B–§I reconstruction above is pattern-derived, not document-derived. **Action requested:** confirm whether to copy from a private Medhavi repo into pantry, or approve this reconstruction.
2. **Specific table schemas, endpoint signatures, and routing rules are starting specifications, not deployed reality.** The appendix author should cross-check against the actual deployed code before publication.
3. **The MVAL misnomer in TIKTOC §App D carries no implication for Appendix E** — App E correctly treats MVAL as an analytical-log discipline.
4. **Vercel hosting assumption.** §B.1 names Vercel; the platform may run on a different Node hosting target. Verify before publication.
5. **The Cancer Biology Mixture-of-Experts router and Physics widget tool layer** are documented in `medhavy-1.5-feature-roadmap-complete.md` §"Ask AI"; the appendix should reference but not re-specify them — the implementation details live in the textbook deployments, not in the Hub itself.

### L.2 Open questions for the appendix to surface (not resolve)

- **Per-tenant database isolation.** Is the Hub one Postgres database with tenant_id-keyed rows (current assumption), or a Postgres-per-tenant pattern? The trade-off is operational complexity vs. blast-radius isolation. The appendix should flag the question.
- **Realtime subscriptions for the editor.** The §I workflow assumes the editor is multi-user collaborative; Supabase Realtime is the natural fit. If the editor is single-user-at-a-time (current Medhavy 1.5 reality), the Realtime layer is unused and the architecture simplifies.
- **The audit-log retention policy.** §F.2's `mval_log_entries` table grows linearly with platform use. The retention policy (90 days hot, 1 year warm, archived to S3 thereafter) is the standard pattern but should be explicitly committed.
- **The consent architecture's data-minimisation commitments** (Ch 11) constrain what `events` and `glp_signal_rows` can hold. The Hub's analytics pipeline has to honour those constraints at ingestion time, not at reporting time. The appendix should flag the constraint and reference Ch 11 for the substantive discussion.

### L.3 What would change the reading

The appendix's recommendations would substantively revise if:

- The deployed reality is a Postgres-per-tenant pattern rather than the multi-tenant single-database pattern §F implies. The schema specification in §F would need per-tenant scoping changes.
- The platform team adopts Supabase Auth as the primary identity (deprecating Clerk). The §C.2 / §D.1 design decision flips; the architecture simplifies but the MFA / OAuth maturity gap re-opens.
- The TEXTBOOK_ONLY constraint is relaxed for non-institutional deployments (per `PEDAGOGY ARCHITECTURE.txt` §5 — *"The general Medhavy platform may relax this constraint for other use cases"*). The §D.4 enforcement architecture needs a per-tenant on/off switch.

---

## M. Suggested appendix shape — section-by-section word allocation

Recommended internal allocation for the appendix author (target 3,500–4,500 words):

- §A Scope (~200 words)
- §B System context — diagram description and data flow (~700 words)
- §C Tech stack — Next.js, Clerk, Supabase, S3, PostHog (~700 words)
- §D Auth architecture — JWT flow, logout, CORS, TEXTBOOK_ONLY (~600 words)
- §E Textbook access decision tree (~300 words)
- §F Database schema summary — three table families (~500 words)
- §G Key design decisions, defended (~500 words)
- §H API reference summary — five endpoint groups (~400 words)
- §I Concept-map editor workflow (~300 words)
- §J–§L Cross-references + verification + flags + still-puzzling (~400 words)

Total: ~4,600 words. At the upper end of the 3,500–4,500 target; the appendix author may want to trim §C or §G depending on which audience (Charles vs. developer) the final draft leans toward.

---

## N. Connection to other appendices

- **Appendix A (Lexicon)** establishes the platform vocabulary the Hub's APIs are named in. The appendix's endpoint names (`/api/textbooks/:slug/concepts`) and table names (`concept_nodes`, `bandit_posteriors`) align with the Ch 12 / Appendix A lexicon.
- **Appendix B (Causal Knowledge Graph)** supplies the prior weights for the bandit's cold-start (Appendix D §D); those priors live in a Supabase table (the appendix should add `evidence_priors` to §F.3 if the deployment commits to durable storage of the Hattie-DAG-derived priors).
- **Appendix C (GLP Technical Specification)** specifies the Y1..Y7 components; this appendix's `glp_signal_rows` table is the storage layer for those components.
- **Appendix D (Contextual Bandits)** specifies the bandit's algorithm; this appendix's `bandit_posteriors` table is the bandit's persistent state. The two appendices are intentionally complementary — bandits specifies *what*, architecture specifies *where*.

---

*End of Appendix E research note. ~4,000 words. Next step: hand to Cowork for compilation as `books/medhavy/chapters/E-medhavi-hub-architecture.md`, after the author confirms whether the actual `ARCHITECTURE.md` and `API.md` documents can be copied into pantry to replace the reconstruction.*
