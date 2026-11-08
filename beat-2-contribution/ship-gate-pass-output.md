# Ship Gate Pass Output

ship-gate: swisspost/design-system @ chore/8480-autofill-hours against main; voice guide read from .claude/voice-guard/voice-guide.md; your pr-precheck copy at .claude/skills/pr-precheck/voice-guide.md isn't linked to it (the unit 6 `ln -sf` line fixes that)
ship-gate: repo check 1/1 `working workflow`: echo 'N/A'
ship-gate: repo check 1/1 `working workflow`: ok (0s)
ship-gate: running your pr-precheck in live mode on chore/8480-autofill-hours (one sonnet call)...
ship-gate: PASS. chore/8480-autofill-hours passed your manifest's checks and your pr-precheck. Open the PR through Claude Code within 30 minutes, without changing anything, and the ship-gate lets it through without running again.
  repo check working workflow: ok (0s)
  matches-plan [pass]: Diff is one file, .github/workflows/autofill-time-spent.yaml, matching the plan's 'Only the new workflow file' scope, trigger, auth and skip behavior; only extra is a missing-field guard in the same skip pattern.
  tested [pass]: Description's Demo table gives fork run links and outputs for fill, skip-filled, skip-empty-Hours and not-on-project cases, covering the plan's test plan; manifest says manual testing required because act can't emit Projects events.
  clean-diff [pass]: Single new file, 104 insertions, no debug prints, dead or commented-out code; only comment explains the first-project assumption.
  follows-standards [pass]: Template sections filled with real content and N/A reasons; 'Disclosure: I used Claude Opus 5.5 for planning and implementation, but I reviewed the final work myself.'

  - **Trigger:** `issues: closed` plus `workflow_dispatch`.
  - **Auth:** `SWISSPOSTDEVS_ACCESS_TOKEN`.
  - **Field names:** constants at the top of the script.
  - **IDs:** looked up at run time.
  - **Skips:** logged without failing.
  - **Tooling:** `actions/github-script`.
  - **Left out:** the "(tbd)" template checkbox, and the description says so.

  One small addition isn't in the plan or the description: a skip when the project has no "Time Spent (h)" field. It follows the plan's "log and exit without failing" pattern and widens nothing, so it doesn't count as drift. Add one line to the description anyway.
- **tested: pass.** `act` can't emit Projects events, and the manifest records manual testing as required. The description has a table of fork runs with outputs and run links:
  - "Time Spent (h)" filled: skip.
  - "Hours" empty: skip.
  - Fill case: set 2.067.
  - Not on a project: skip.

  That covers all five cases in the plan's test plan, with observable outputs. The test-evidence file is absent, but the same proof is in the description. I couldn't open the run links, since I may not fetch anything.
- **clean-diff: pass.** The diff is one new file. It has no debug output, dead code or commented-out code. The single comment explains a design choice.
- **follows-standards: pass.** The template sections are filled with real content, and N/A items are explained. The AI disclosure is present ("I used Claude Opus 5.5 … reviewed the final work myself"), as `scope.md` requires. The issue thread was unavailable, and no maintainer direction was available to check against.

**Verdict:** `accept`, since every required check passes.

**Fix before posting (doesn't change the verdict)**
- The checklist ticks "✔️ Existing unit tests pass locally". Per the manifest, no test commands were run, because they were moved to the second table as irrelevant. Either run `pnpm test` and keep the tick, or change the line to N/A. Otherwise it claims something the evidence doesn't show.
- Add the missing-field skip to the Description bullets.

**Voice-guide notes**
- **Emojis:** the headings and checklist keep the template's emojis (📄 🚀 🔮 ✅ 🛠️ and others). Your "never post emojis" rule is broken, though the template supplies them.
- **Conciseness:** drop "Happy to adjust anything if you have suggestions." and the qualifier "as far as I know".
- **Typos:** "Time Spent(h)" is missing a space, and "logs and return early" has a tense mismatch.
- **Title:** the H1 repeats the PR title at the top of the description. Remove it.
