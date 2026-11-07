# Repro Check Output

## 2026-11-07 (Run 2)

Scope. Issue #8480 is open with no assignee and no stranger's claim. Your two comments on it are the only ones, so the claim stands. I couldn't confirm that your scout graded this issue, because ~/.claude/skills/issue-scout/ and scan-output.md don't exist on this machine. Check that you have that evidence trail.

Checks
- has-evidence: pass. #8480 is a task ("Create a workflow to autofill the hours field"), not a bug, so the bug-only condition doesn't apply. The tree and search output are pasted verbatim anyway.
- right-target: pass. Same reason: no version numbers or bug output to match. The report targets the right thing, which is whether any workflow in .github/workflows/ fills the hours field.
- followable-comms: pass.
  - The steps are followable: look in .github/workflows/, then search the repo for "hours".
  - The claim's goal (implement the workflow, asking about the optional "tbd" PR template checkbox) is realistic.
- discloses-ai: pass. I found no AI-use disclosure requirement. CONTRIBUTING.md has no AI, LLM or disclosure language, and the repo root has no AI policy file. I only listed the root, so I didn't look in .github/.

Verdict: accept, because every check passes under your rubric.

Tensions, not graded
- A repro report is the wrong shape here. "I've reproduced the issue" doesn't fit a feature request.
- The evidence is thin. Searching repo files can't show that the GitHub Project has no automation. Project built-in workflows live outside the repo. The report also searches "hours", while the issue names the field Time Spent (h) and Hours Spent (h). I'd search those names too, and say plainly that you can't see Project settings.
- Consider a rubric fix. A check for whether the evidence supports the claim would catch this. At the moment, both bug-only checks pass automatically for non-bug issues.

Voice guide
- Who I am in threads: the claim has no experience level, no reason for choosing this repo, and no next steps. For example: "First-time contributor, long-time user of the design system. Next: plan the workflow once confirmed."
- Minimal Unnecessary Qualifiers: the report says "just the design-system repo cloned…" and "just…" is a qualifier. Cut it.
- Be Concise: the report's "Hi" greeting and "I'd like to implement the workflow if this issue is still open" can be shortened to "Happy to implement this if still open."
- Never-post list: no violations (no emojis, deadlines or loaded tone).
- Posted history: the claim is already posted, along with a follow-up ping on 2026-10-28 that has had no reply for 10 days. If the maintainer doesn't respond, consider posting the repro now. It adds new information to the thread.


```json
{
  "item": "https://github.com/swisspost/design-system/issues/8480",
  "checks": [
    {"name": "has-evidence", "grade": "pass", "evidence": "Issue is a task, not a bug (bug-only check n/a); tree and search output are pasted verbatim."},
    {"name": "right-target", "grade": "pass", "evidence": "Not a bug issue (n/a); report checks .github/workflows/ for hours-autofill, matching the issue's ask."},
    {"name": "followable-comms", "grade": "pass", "evidence": "Two concrete steps (inspect .github/workflows/, search 'hours'); claim goal is to implement the workflow, which is realistic."},
    {"name": "discloses-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI/disclosure language and no AI policy file at repo root; no disclosure required."}
  ],
  "verdict": "accept"
}
```

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