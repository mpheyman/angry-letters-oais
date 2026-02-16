Use this when a change touches Postgres schema, queries, or migrations.

## Requirements
- Propose migration(s) in `migrations/` (small, focused).
- Provide rollback notes if destructive.
- Provide validation queries (before/after).
- Confirm Docker-first workflow (how to run migrations locally + in CI).

## Output format
### MigrationPlan
- **Files**:
  - `migrations/XXXX_description.sql`: …
- **Validation**:
  - `SELECT …`: expected …
- **Rollback**:
  - …

