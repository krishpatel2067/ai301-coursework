Here's the plan. New contributor here, so I've listed my assumptions as questions below. Happy to
adjust before I start.

**Analysis**

No workflow under `.github/workflows/` touches the Projects board, so nothing copies the "Hours"
estimate into "Time Spent (h)" when an issue is done.

**Proposed Solution**

Add one new workflow, `.github/workflows/autofill-time-spent.yaml` (`.yaml` to match the other
workflows). When an issue is closed (moved to Done), it will:

1. Find the issue's item on the Projects v2 board.
2. Read its "Time Spent (h)" and "Hours" values.
3. If "Time Spent (h)" is filled, do nothing. If it's empty, set it to the "Hours" value.

Decisions (questions for maintainers marked with ❓):

- **Trigger:** `issues: closed`, plus `workflow_dispatch` (takes an issue number) for manual runs and
  testing. Actions has no trigger for Projects v2 item changes, so closing the issue is the closest
  signal to "set to done". ❓ Does the board move items to Done on close?
- **Auth:** the default `GITHUB_TOKEN` can't write to an org-level Projects v2 board, so the
  workflow needs a token with the `project` scope. ❓ Can the existing `SWISSPOSTDEVS_ACCESS_TOKEN`
  secret be used, or should a new one be added? I can't add secrets myself.
- **IDs:** nothing hardcoded. The script looks up the project, item and field IDs by name at run
  time. ❓ Which project number should it use?
- **Field names:** "Time Spent (h)" (the issue's checklist wording; the intro says "Hours Spent
  (h)") and "Hours". Both are constants at the top of the script, so a rename is a one-line change.
  ❓ Confirm the exact names.
- **Implementation:** `actions/github-script` (already used in `label-stale-review-prs.yaml`) with
  GraphQL calls, rather than shelling out to `gh api`.
- **Skipped:** if the item isn't on the board, or "Hours" is empty, log a message and exit without
  failing.

**Scope**

Only the new workflow file. No other files, no production code. The "(tbd)" PR template checkbox is
left out; happy to do it as a follow-up if wanted.

**Implementation Plan**

1. Create `.github/workflows/autofill-time-spent.yaml` with the trigger above, minimal
   `permissions`, and the token secret.
2. Write the script: query the issue's project item and the two field values; stop if "Time Spent
   (h)" is filled; otherwise run the `updateProjectV2ItemFieldValue` mutation with the "Hours" value.
3. Test in my fork. `act` can't emit Projects events, so I'll make a personal Projects v2 board with
   the same two fields and my own token as a secret, then run via `workflow_dispatch` and by closing
   a test issue. Cases: empty (gets filled), filled (unchanged), "Hours" empty (skipped), issue not
   on the board (skipped). Run links go in the PR.
