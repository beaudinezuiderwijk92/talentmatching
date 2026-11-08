# Delivery roadmap

## Phase 0 — existing website audit (blocker)
- [ ] Import or connect existing Talent Matching website source.
- [ ] Identify existing components, branding, database, hosting, integrations and auth flow.
- [ ] Capture current working workflows and baseline test results.
- [ ] Map candidate data, lawful processing basis, consent requirements and retention.

## Phase 1 — foundation
- [ ] Database migrations and tenant relationships.
- [ ] Supabase Auth + role membership model + RLS policies and tests.
- [ ] Private Storage and candidate document access policy.
- [ ] Server-side secrets and environment configuration.

## Phase 2 — recruitment CRM
- [ ] Candidate/profile records, employer/company records and vacancies.
- [ ] Applications, recruiter assignment, Kanban and activity history.
- [ ] Dashboards and realtime notifications.

## Phase 3 — AI intelligence
- [ ] Secure uploads and CV parsing.
- [ ] Job-related criteria extraction and explainable match scores.
- [ ] Recruiter-reviewed shortlists and assistant tools.
- [ ] Accuracy, bias, privacy and human-oversight evaluation.

## Phase 4 — automation
- [ ] n8n signed webhooks, idempotency and retry strategy.
- [ ] Candidate confirmations, reminders and recruiter notifications.
- [ ] Workflow logs, monitoring and error recovery.

## Phase 5 — production
- [ ] TypeScript/lint/unit/integration/Playwright checks.
- [ ] Pen-test/security review, retention/deletion/export checks.
- [ ] Staging deployment and production rollout with rollback.

**Definition of done:** real data-backed features, tested security and RLS, documented integrations, no regressions to existing site. No fake production data, fabricated metrics or automatic candidate rejection.
