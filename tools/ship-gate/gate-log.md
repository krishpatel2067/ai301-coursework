# ship-gate log (one dated entry per run, by hand or through the hook)

## 2026-11-07 12:40 [hook] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (setup)
- manifest checks: none ran
- reasons quoted:
  - no PR text to check. The ship-gate stops gh pr create without --title and --body-file on purpose (that includes --help, --fill, and the interactive form). If this was the hook test, this stop is expected and nothing else needs doing.

## 2026-11-07 12:42 [hook] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (setup)
- manifest checks: none ran
- reasons quoted:
  - no PR text to check. The ship-gate stops gh pr create without --title and --body-file on purpose (that includes --help, --fill, and the interactive form). If this was the hook test, this stop is expected and nothing else needs doing.

## 2026-11-07 19:39 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (setup)
- manifest checks: none ran
- reasons quoted:
  - ship-manifest.md is still the template: the first table has no command yet. Put the original repo in the title, and list the two to four checks the project asks you to run before a PR, each with where you found it. If the project names no checks, write one row whose command is none, and say in Source where you looked.

## 2026-11-07 19:42 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (refusal)
- manifest checks: none ran
- reasons quoted:
  - your pr-precheck is not installed at /home/theca/repos/GitHub/Open Source/design-system/.claude/skills/pr-precheck. The ship-gate runs your unit 4 tool, so there's nothing to run yet: copy the whole skill/ folder from your Unit 4 materials to ~/.claude/skills/pr-precheck/ and write its four files, then run the ship-gate again.

## 2026-11-07 19:43 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (refusal)
- manifest checks: none ran
- reasons quoted:
  - your pr-precheck is not installed at /home/theca/repos/GitHub/Open Source/design-system/.claude/skills/pr-precheck. The ship-gate runs your unit 4 tool, so there's nothing to run yet: copy the whole skill/ folder from your Unit 4 materials to ~/.claude/skills/pr-precheck/ and write its four files, then run the ship-gate again.

## 2026-11-07 19:44 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (refusal)
- manifest checks: none ran
- reasons quoted:
  - your pr-precheck is not installed at /home/theca/repos/GitHub/Open Source/design-system/.claude/skills/pr-precheck. The ship-gate runs your unit 4 tool, so there's nothing to run yet: copy the whole skill/ folder from your Unit 4 materials to ~/.claude/skills/pr-precheck/ and write its four files, then run the ship-gate again.

## 2026-11-07 19:46 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (refusal)
- manifest checks: none ran
- reasons quoted:
  - your pr-precheck is not installed at .claude/skills/pr-precheck. The ship-gate runs your unit 4 tool, so there's nothing to run yet: copy the whole skill/ folder from your Unit 4 materials to ~/.claude/skills/pr-precheck/ and write its four files, then run the ship-gate again.

## 2026-11-07 19:47 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (setup)
- manifest checks: none ran
- reasons quoted:
  - pr-precheck's voice-guide.md is still your copy from unit 4, and there's no voice guide at .claude/voice-guard/voice-guide.md. The ship-gate reads the guide your voice guard uses. Move it there: run the commands in section 3 of INSTALL.md in your Unit 6 materials, from that folder.

## 2026-11-07 19:48 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (block)
- manifest checks:
  - working workflow: `N/A` -> FAILED (exit 127, 0s)
- reasons quoted:
  - the repo's own check `working workflow` failed: `N/A` exited 127. Output tail:
    
    /bin/sh: 1: N/A: not found
    Source of this check: `.github/act/README.md` names `act` - but projects can't be locally tested; manual testing required. Fix what it names. If it also fails on main for a reason your fix doesn't touch, move it to the second table of ship-manifest.md with a date and the reason, instead of deleting the row. Exit 127 means the command was not found. The ship-gate runs each row in a fresh shell at the top folder of your clone, not in your terminal where your virtual environment is active. Rewrite the row so it runs there: `uv run pytest` if the project uses uv, `.venv/bin/pytest` if you made a virtual environment, `npx eslint .` for an npm project.

## 2026-11-07 19:51 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (block)
- manifest checks:
  - working workflow: `echo 'N/A'` -> ok (0s)
- pr-precheck checks:
  - matches-plan [pass]: Diff is the single new file .github/workflows/autofill-time-spent.yaml, the plan's stated scope, with the planned triggers, token, constants and skip behavior.
  - tested [fail]: Test evidence file absent; Demo sections are placeholders ('[image to add directly on GitHub]'); no fork run links for the plan's four test cases; manifest check is just echo 'N/A'.
  - clean-diff [pass]: 104 insertions in one file with no debug output, dead code or unrelated edits.
  - follows-standards [pass]: PR template sections filled and disclosure present: 'I used Claude Opus 5.5 for planning and implementation, but I reviewed the final work myself.'
- reasons quoted:
  - your own pr-precheck rejected chore/8480-autofill-hours: verdict reject. The checks that did not pass, in your rubric's words:
      - tested [fail]: Test evidence file absent; Demo sections are placeholders ('[image to add directly on GitHub]'); no fork run links for the plan's four test cases; manifest check is just echo 'N/A'.
    Fix your branch. If a check asks for something this repo doesn't ask for, fix that check in your rubric instead, and say so in your Unit 7 Toolkit entry.

## 2026-11-07 20:08 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (block)
- manifest checks:
  - working workflow: `echo 'N/A'` -> ok (0s)
- pr-precheck checks:
  - matches-plan [pass]: Diff is one file, .github/workflows/autofill-time-spent.yaml, matching the plan's 'Only the new workflow file' scope, trigger, token, and skip decisions; the extra missing-field skip is minor.
  - tested [fail]: Plan lists 5 test cases and promises run links; PR has 3 screenshots, no run links, nothing for 'issue not on the board', and no disclosure of the shortfall.
  - clean-diff [pass]: Single new file, 104 insertions, no debug output, dead code, or unrelated hunks.
  - follows-standards [pass]: Description states 'Disclosure: I used Claude Opus 5.5 for planning and implementation' and fills the template sections with real content.
- reasons quoted:
  - your own pr-precheck rejected chore/8480-autofill-hours: verdict reject. The checks that did not pass, in your rubric's words:
      - tested [fail]: Plan lists 5 test cases and promises run links; PR has 3 screenshots, no run links, nothing for 'issue not on the board', and no disclosure of the shortfall.
    Fix your branch. If a check asks for something this repo doesn't ask for, fix that check in your rubric instead, and say so in your Unit 7 Toolkit entry.

## 2026-11-07 20:19 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: BLOCK (block)
- manifest checks:
  - working workflow: `echo 'N/A'` -> ok (0s)
- pr-precheck checks:
  - matches-plan [pass]: Diff is one new file, .github/workflows/autofill-time-spent.yaml, matching the plan's 'Only the new workflow file' scope, triggers, auth and skip cases.
  - tested [unclear]: Run links cover the plan's five cases, but no expected outcome is stated for any case and the links can't be verified from the package. The checklist claims unit tests were added and pass, while the manifest shows none were added or run.
  - clean-diff [pass]: 104-line single-file addition with no debug leftovers, dead code, commented-out code or unrelated hunks; core.info calls are the feature's logging.
  - follows-standards [pass]: Description ends with 'Disclosure: I used Claude Opus 5.5 for planning and implementation, but I reviewed the final work myself.' and all PR template sections are filled.
- reasons quoted:
  - your own pr-precheck rejected chore/8480-autofill-hours: verdict reject. The checks that did not pass, in your rubric's words:
      - tested [unclear]: Run links cover the plan's five cases, but no expected outcome is stated for any case and the links can't be verified from the package. The checklist claims unit tests were added and pass, while the manifest shows none were added or run.
    Fix your branch. If a check asks for something this repo doesn't ask for, fix that check in your rubric instead, and say so in your Unit 7 Toolkit entry.

## 2026-11-07 20:28 [manual] swisspost/design-system @ chore/8480-autofill-hours (base main)

- verdict: PASS
- fingerprints: head d12a07203e148900a03d357b4d4d8aeea606ef29 base 64056b31d1e31a588fb4aa2828e236745538d31e title 3afb803a04f6 body dbbe90915063 manifest 700816f96ff5 plan 94fa31958a6e evidence e3b0c44298fc issue 00adae6af1ca
- manifest checks:
  - working workflow: `echo 'N/A'` -> ok (0s)
- pr-precheck checks:
  - matches-plan [pass]: Diff is one file, .github/workflows/autofill-time-spent.yaml, matching the plan's 'Only the new workflow file' scope, trigger, auth and skip behavior; only extra is a missing-field guard in the same skip pattern.
  - tested [pass]: Description's Demo table gives fork run links and outputs for fill, skip-filled, skip-empty-Hours and not-on-project cases, covering the plan's test plan; manifest says manual testing required because act can't emit Projects events.
  - clean-diff [pass]: Single new file, 104 insertions, no debug prints, dead or commented-out code; only comment explains the first-project assumption.
  - follows-standards [pass]: Template sections filled with real content and N/A reasons; 'Disclosure: I used Claude Opus 5.5 for planning and implementation, but I reviewed the final work myself.'

