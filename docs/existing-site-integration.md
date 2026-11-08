# Integration with existing website — required before coding UI

The pre-existing Talent Matching Recruitment website was **not present** in the connected GitHub repositories. This repo is a newly initialized project home, not a replacement website.

## Inventory to collect
- Source code repository or ZIP, primary domain and hosting/deployment provider.
- Framework, package manager, design tokens, logos, assets and UI components.
- Auth providers, session strategies, login/register routes and middleware.
- Supabase project identification, migrations, database tables, RLS and Storage buckets.
- Existing candidate/employer flows and third-party integrations.
- Environment variable **names only**, never production secret values.

## Procedure
1. Import source to a reviewed branch with no keys or private personal data.
2. Audit dependencies and behavior; record findings with file paths and line numbers.
3. Propose minimal modifications that reuse existing UI and database.
4. Implement incrementally with migrations, rollback plans and automated tests.
5. Review privacy/security impact before processing real candidate CVs.

## Data protection
Recruitment and AI profiling can have significant effects. Establish lawful basis and transparency, purpose limits, role-restricted access, retention, human review and a DPIA where required. Assess applicable EU AI Act obligations before deployment; do not treat AI matching scores as objective or autonomous hiring decisions.
