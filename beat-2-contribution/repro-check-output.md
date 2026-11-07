# Repro Check Output

## 2026-11-07 (Run 1)

Verdict: reject. has-evidence fails, so the package isn't ready to post.

Scope check: Issue #8480 is in a public repo (swisspost/design-system) and is open with no assignee. The only claim on it is yours, so no stranger's claim blocks you. The thread has no reproduction yet, so you wouldn't be duplicating anyone.

Checks
- has-evidence: fail. The environment section says "No specific environment needed", and the commit line says "Commit showing reproduction: none". There's no OS, no tool versions, and no commit SHA or branch for the repo state you inspected. The tree and search output are verbatim, but the rubric needs the environment info too.
- right-target: pass, with a caveat.
  - The issue has no version numbers.
  - It's a feature request ("Create a workflow to autofill the hours field"). Your evidence of absence (no matching workflow) is the right behavior to show.
  - The caveat is that you only searched "hours". The issue's field names are Hours Spent (h), Time Spent (h) and Hours, and a workflow would likely use pojectV2. Your search doesn't rule that out.Searching for those would make the absence claim solid.
- followable-comms: pass.
  - Both steps are followable.
  - The claim's goals are realistic. It asksmplate checkbox marked "tbd".
  - Step 1's "None indicate…" is subjective, so naming the files you read would help.
- discloses-ai: pass.
  - AI_POLICY.md isn't in the repo root or .github/.
  - CONTRIBUTING.md has no AI-use or disclos
  - .github/copilot-instructions.md exists but isn't a contributor disclosure rule.

Voice-guide notes
- Who I am in threads:
  - The claim has no experience level, no reason for choosing this repo, and no next steps.
  - The repro has no next steps either. Someorkflow" would fit.
- Concise: "I've reproduced the issue" is a mismatch for a feature request. "Confirmed: no existing workflow fills the hours field" is shorter and more accurate.
- Never post: I found no emojis, deadlines or abbreviations.

Other things to know
- claim-draft.md is identical to the claim y22. You've pinged twice (10-22 and 10-28)with no maintainer reply.
- I couldn't find claim-draft.md having anytt it. Reply only if you have new information.

To fix before posting: add the OS, git versid broaden the search to the field names above (case-insensitive).

```json
{
  "item": "https://github.com/swisspost/design-system/issues/8480",
  "checks": [
    {"name": "has-evidence", "grade": "fail", "evidence": "Environment: \"No specific environment needed\"; \"Commit showing reproduction: none\" - no OS, tool versions, or repo commit recorded"},
    {"name": "right-target", "grade": "pass", "evidence": "Issue has no version numbers; tree output shows no hours-autofill workflow in .github/workflows/ (caveat: search only covered \"hours\", not \"Time Spent\"/projectV2)"},
    {"name": "followable-comms", "grade": "pass", "evidence": "Two-step repro is followable; claim goal (ask about 'tbd' PR template checkbox) is realistic"},
    {"name": "discloses-ai", "grade": "pass", "evidence": "No AI_POLICY.md; CONTRIBUTING.md has no AI-use disclosure requirement"}
  ],
  "verdict": "reject"
}
```