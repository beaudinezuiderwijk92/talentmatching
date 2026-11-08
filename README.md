# Talent Matching Recruitment — AI Recruitment Automation 2.0

Status: **project foundation / specifications only**. No production application, database or deployed integrations are included yet.

## Mission
Evolve the *existing* Talent Matching Recruitment website into a secure, AI-assisted recruitment platform. Preserve its identity and working functionality. Do not build a parallel replacement before the current website source is imported and audited.

## Modules (planned)
1. Recruitment dashboard — candidates, vacancies, applications, funnel metrics and notifications.
2. Candidate CRM — profiles, experience, education, skills, consent, communication and Kanban.
3. Employer portal — companies, vacancies, shortlists, interviews and status.
4. AI tools — CV parsing, explainable job-related matching and recruiter assistant.
5. Automation — Supabase Edge Functions, verified n8n webhooks, notifications and follow-ups.
6. Operations — audit logs, data retention, data export/deletion, tests, and deployment.

## Proposed stack (pending existing-code audit)
- Reuse existing frontend stack; Vercel only if compatible with current project.
- Supabase Auth, PostgreSQL, private Storage, RLS and Realtime.
- Server-side OpenAI API access; n8n via authenticated webhooks.
- GitHub Actions for lint, types, tests, builds and Playwright.

## Important
This repository was empty when initialized. The existing website code and branding assets have **not** been imported, so there is no authentication implementation to audit yet. See [architecture/authentication.md](docs/architecture/authentication.md), [roadmap.md](docs/roadmap.md), and [integration checklist](docs/existing-site-integration.md).

**Security:** Never commit secrets, CVs, candidate records, API keys, production database dumps or personally identifiable information.
**AI:** Recommendations are decision support, not automatic hiring/rejection. Require human review and explainable job-related criteria.

## Next required input
Locate/export the existing website source, identify hosting, Supabase project and existing authentication implementation, then integrate into this repository on a feature branch.
