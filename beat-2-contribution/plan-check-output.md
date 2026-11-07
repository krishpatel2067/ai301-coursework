# Plan Check Output

## 2026-11-07 (Run 1)

Verdict: reject. The plan builds the opposite of what the issue asks for, and it leaves out the
trigger and auth details a builder would need.

I read both drafts against issue #8480, your two claim comments, and the repo's CONTRIBUTING.md and
.github/ contents. No maintainer has replied on the thread.

Checks

- ai-use-disclosure: pass. CONTRIBUTING.md has no AI or disclosure requirement.
  .github/copilot-instructions.md exists, but it isn't a contributor disclosure rule.
- tight-scope: pass. The plan adds one new file under .github/workflows/ and explicitly rules out
  production code.
- clear-plan: fail.
  - The filename is only an "e.g.".
  - "Runs when a GitHub project item is edited" is not a concrete trigger. The issue says "whenever
    an issue is set to done", and the plan never mentions Done.
  - It doesn't say how the workflow authenticates to a Projects v2 board, or how it finds the
    project and field IDs. Those are the hard parts of this task.
  - act can't simulate Projects v2 events, so step 3 doesn't give a way to check the result.
- correct-cause: fail. The direction is reversed.
  - The issue says: if Time Spent (h) is empty, copy the value from the Hours estimation field. If
    it's filled, do nothing.
  - Your plan says: if Hours is empty, fill it from Time spent (h).
  - It also treats the missing workflow as the cause, with no sign it read the issue's logic. Your
    repro only shows that no such workflow exists.

Voice-guide notes (.claude/voice-guard/voice-guide.md)

- Be Concise: "Here is my plan:" and "I will add" could be "Here's the plan:" and "Will add". This
  is minor.
- Use Contractions Appropriately: the all-caps "NOT" is emphasis. Your guide marks emphasis as
  _not_.
- Typo: "changing anything out the .github/workflows/ folder" should read "outside".
- Thread awareness: your claim comment asked whether to include the PR-template checkbox, and the
  plan doesn't answer it. It doesn't note that there's been no maintainer reply either.
- Posting: per scope.md, plan-comment.md stays off the thread even once the plan is accepted.

Procedure gaps (feedback on your skill files)

- procedure.md is written for eval bundles and says live mode "may be slightly different". It never
  says where to find thread highlights or repro evidence in live mode.
- SKILL.md expects the repro evidence to be your posted repro comment on the issue. There isn't one
  on the thread, so I used repro-draft.md instead.
- The rubric has no check for test-plan quality or for honesty about unknowns. The evidence guide
  describes both, but the rubric never uses them, so they didn't affect this verdict.

```json
{
  "item": "https://github.com/swisspost/design-system/issues/8480",
  "checks": [
    {
      "name": "ai-use-disclosure",
      "grade": "pass",
      "evidence": "CONTRIBUTING.md has no AI/disclosure requirement; no AI policy file."
    },
    {
      "name": "tight-scope",
      "grade": "pass",
      "evidence": "One new file in .github/workflows/; production code explicitly excluded."
    },
    {
      "name": "clear-plan",
      "grade": "fail",
      "evidence": "Filename is 'e.g.'; trigger is vague 'project item edited' (issue says set to done); no auth, project ID or field ID handling; `act` can't test Projects v2 events."
    },
    {
      "name": "correct-cause",
      "grade": "fail",
      "evidence": "Issue: if 'Time Spent (h)' is empty, copy from 'Hours' estimate. Plan fills 'Hours' from 'Time spent (h)', the reverse."
    }
  ],
  "verdict": "reject"
}
```
