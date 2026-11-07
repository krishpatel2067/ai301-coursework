Here's the plan. New contributor here, so I've listed my assumptions below. Happy to adjust before I
start.

**Analysis**

No workflow under `.github/workflows/` touches the Projects board, so nothing copies the "Hours"
estimate into "Time Spent (h)" when an issue is done.

**Proposed Solution**

Add one new workflow, `.github/workflows/autofill-time-spent.yaml` (`.yaml` matches the other
workflows). When an issue is closed (moved to Done), it will:

1. Find the issue's item on the Projects v2 board.
2. Read its "Time Spent (h)" and "Hours" values.
3. If "Time Spent (h)" is filled, do nothing. If it's empty, set it to the "Hours" value.

Decisions:

- **Trigger:** `issues: closed`, plus `workflow_dispatch` (takes an issue number) for manual runs
  and testing. Actions has no trigger for Projects v2 item changes, so closing the issue is the
  closest signal to "set to done".
- **Auth:** the default `GITHUB_TOKEN` can't write to an org-level Projects v2 board, so the
  workflow needs a token with the `project` scope. I will use `SWISSPOSTDEVS_ACCESS_TOKEN` secret
  since other workflows use that (happy to change it if you want).
- **IDs:** nothing hardcoded. The script looks up the project, item and field IDs by name at run
  time.
- **Field names:** "Time Spent (h)" and "Hours". Both are constants at the top of the script, so a
  rename is a one-line change.
- **Implementation:** `actions/github-script` (already used in `label-stale-review-prs.yaml`) with
  GraphQL calls, rather than using the raw `gh api`.
- **Skipped:** if the item isn't on the board, or "Hours" is empty, log a message and exit without
  failing.

**Scope**

Only the new workflow file. No other files, no production code. The "(tbd)" PR template checkbox is
left out; happy to do it as a follow-up if wanted.

**Implementation Plan**

1. Create `.github/workflows/autofill-time-spent.yaml` with the trigger above, minimal
   `permissions`, and the token secret.
2. Write the script: query the issue's project item and the two field values; stop if "Time Spent
   (h)" is filled; otherwise run the `updateProjectV2ItemFieldValue` mutation with the "Hours"
   value.
3. Test in my fork. `act` can't emit Projects events, so I'll make a personal Projects v2 board with
   the same two fields and my own token as a secret, then run via `workflow_dispatch` and by closing
   a test issue. Cases:
   - "Time spent (h)" empty, "Hours" not empty (fill)
   - "Time spent (h)" not empty, "Hours" not empty (skip)
   - "Time spent (h)" not empty, "Hours" empty (skip)
   - "Time spent (h)" empty, "Hours" empty (skip)
   - issue not on the board (skip).

   Run links will come in the PR.
