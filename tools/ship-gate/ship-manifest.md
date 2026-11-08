# Ship manifest: swisspost/design-system

## Must pass before a ship

| Check            | Command     | Source                                                                                              |
| ---------------- | ----------- | --------------------------------------------------------------------------------------------------- |
| working tests    | `pnpm test` | `CONTRIBUTING.md`                                                                                   |
| working workflow | echo 'N/A'  | `.github/act/README.md` names `act` - but projects can't be locally tested; manual testing required |

## Excluded, with a dated reason

| Check      | Command                               | Date       | Why it doesn't count against this PR                         |
| ---------- | ------------------------------------- | ---------- | ------------------------------------------------------------ |
| tests pass | `pnpm [package shortname]:test`       | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:unit`       | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:unit:watch` | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:e2e`        | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:e2e:watch`  | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:snapshots`  | 2026-11-07 | GitHub workflow creation touches none of the production code |
| tests pass | `pnpm [package shortname]:tdd`        | 2026-11-07 | GitHub workflow creation touches none of the production code |
