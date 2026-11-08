# Authentication & authorization design

> **Proposed design, NOT an audit of running code.** The existing application has not been imported.

## Components
- **Supabase Auth:** handles login, registration, password resets, email verification, short-lived access JWTs and refresh sessions.
- **Frontend:** existing UI framework; uses an appropriately configured Supabase client. Route guards are UX only, not authorization.
- **Backend / Supabase Edge Functions:** independently validate each caller and authorize operations by role AND company/tenant.
- **PostgreSQL RLS:** default-deny access to candidate, employer, vacancy and application records. Enforce tenant boundaries at the database.
- **Private Supabase Storage:** CVs, consent documents and attachments in private buckets; short-lived signed URLs only after authorization.
- **Server-side integrations:** OpenAI requests and n8n hooks run from trusted backend code and never receive browser-accessible secret keys.

## Request flow
1. Candidate, employer or recruiter submits credentials over HTTPS to Supabase Auth.
2. Auth returns a session with an access token and refresh-token lifecycle managed by the SDK.
3. An authenticated request carries its access token; server code verifies the identity and performs authorization.
4. Database requests run as the user where RLS applies; privileged jobs use separately authenticated service actions with scoped checks and audit logs.
5. Refresh sessions are rotated/revoked using the provider's supported flows. Logout clears the client session and revokes refresh credentials according to configuration.

## Access matrix (requirements to implement)
| Role | Own profile | Own applications | Employer vacancies | Candidate shortlists | Administration |
|---|---|---|---|---|---|
| Candidate | own | own | public/published | no | no |
| Employer | own | no | own company | only authorized applicants | no |
| Recruiter | own | assigned scope | assigned scope | assigned scope | no |
| Admin | admin scope | authorized only | authorized only | authorized only | audited |

Do not trust user-editable profile fields or client-supplied company IDs to determine authorization. Establish roles/memberships server-side in controlled tables, with RLS and policy tests.

## Credentials
- Passwords must be managed by Supabase Auth, never stored in application tables or logged.
- Publishable/anon key is not a secret; it does **not** grant unrestricted database access.
- Supabase secret/service-role key bypasses RLS and must remain server-side with tightly limited usage.
- OpenAI API keys and n8n signing secrets remain server-side in managed environment secrets.
- Do not log bearer tokens, cookies, CV text, candidate PII or webhook signing secrets.
- Verify webhook signatures, timestamps and replay protection; use idempotency keys for automation.
- Configure authorized redirect URLs, email verification, rate limits, MFA for privileged users, and secure session/cookie settings as appropriate.

## Tests before production
- Unauthenticated requests denied by default.
- Cross-tenant candidates/applications inaccessible.
- Employer cannot read other employers' candidate records.
- Candidate cannot elevate role or change tenant.
- Private document URLs inaccessible without authorization.
- Expired/forged tokens and unsigned webhooks rejected.
- Audit events contain metadata but not raw sensitive contents.

## Current findings
Repository contained no application files at foundation creation. No claim is made about deployed authentication, token storage or RLS posture.
