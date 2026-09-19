# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

<!-- [The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.] -->

[_Issue 68_](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68)

**Verdict output**

<!-- [Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.] -->

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```plaintext
All three issues share repo-level facts (same repo), so I'll cover those once, then per-issue checks.

Repo-level (applies to all three):
- maintainer-active: pass — response-rate sample of 30 recent issues shows only ~1/30 got a collaborator reply (well under 20%), but the fallback condition holds: last commit was 2026-09-16 (3 days ago, within 3 months) and commits are explicitly linked to issue numbers (e.g. "issue #155", "#149", "#24" in commit messages).
- repo-in-use: pass — not archived, last push 2026-09-16 (today: 2026-09-19). No formal releases exist, but this is a course project repo (not a distributed package), so the release-date sub-condition doesn't apply the way it would to a library.
- policy-allows-ai: pass — docs/CONTRIBUTING.md contains no mention of AI, Claude, Copilot, or generative tooling at all; silence passes per the rubric guide.

Per-issue:

┌────────────────────────┬──────────────────────────┬──────────────────────────────────────────────────┬─────────┐
│         Issue          │      not-worked-on       │              scope-fits (preferred)              │ Verdict │
├────────────────────────┼──────────────────────────┼──────────────────────────────────────────────────┼─────────┤
│ #68 (BM25              │ pass — no assignees, no  │ pass — good first issue+tier-1, Python, tight    │ accept  │
│ ZeroDivisionError)     │ comments, no linked PRs  │ repro, 2–4h estimate                             │         │
├────────────────────────┼──────────────────────────┼──────────────────────────────────────────────────┼─────────┤
│ #54 (resume section    │ pass — no assignees, no  │ pass — good first issue+tier-1, Python, has      │ accept  │
│ regex)                 │ comments, no linked PRs  │ runnable repro script                            │         │
├────────────────────────┼──────────────────────────┼──────────────────────────────────────────────────┼─────────┤
│ #12 (snapshot tests    │ pass — no assignees, no  │ pass — good first issue+tier-1, Python, but more │         │
│ for prompts)           │ comments, no linked PRs  │  open-ended (design a snapshot/versioning        │ accept  │
│                        │                          │ scheme), 3–5h                                    │         │
└────────────────────────┴──────────────────────────┴──────────────────────────────────────────────────┴─────────┘

Ranked for your fit (never contributed to OSS, want a clean small start; strongest in Python)

1. #68 — BM25 ZeroDivisionError — smallest, most mechanical fix: guard index() against an empty corpus, unskip one xfail test. Clearest bug, clearest done-condition.
2. #54 — resume section detection regex — also has a runnable repro script and a fixed test list, slightly more reasoning about regex/whitespace behavior.
3. #12 — snapshot tests for prompt templates — good first issue too, but it's an enhancement requiring you to design the versioning/snapshot approach yourself rather than fix a pinned bug, more ambiguity for a first PR.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Last commit 2026-09-16 (3 days before today), commit messages reference issue numbers (e.g. '#155', '#149', '#24')"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "isArchived: false, pushedAt: 2026-09-16T21:48:27Z"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "assignees: [], comments: [], no PRs in repo reference #68"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "docs/CONTRIBUTING.md has no mention of AI/generative tooling"},
      {"name": "scope-fits", "grade": "pass", "evidence": "labels include 'good first issue' and 'tier-1'; Python bug fix matches fit profile"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Last commit 2026-09-16, commits linked to issue numbers"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "isArchived: false, pushedAt: 2026-09-16T21:48:27Z"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "assignees: [], comments: [], no PRs reference #54"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "docs/CONTRIBUTING.md has no mention of AI/generative tooling"},
      {"name": "scope-fits", "grade": "pass", "evidence": "labels include 'good first issue' and 'tier-1'; Python bug fix with runnable repro, matches fit profile"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/12",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Last commit 2026-09-16, commits linked to issue numbers"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "isArchived: false, pushedAt: 2026-09-16T21:48:27Z"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "assignees: [], comments: [], no PRs reference #12"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "docs/CONTRIBUTING.md has no mention of AI/generative tooling"},
      {"name": "scope-fits", "grade": "pass", "evidence": "labels include 'good first issue' and 'tier-1'; Python test-writing task, matches fit profile but more open-ended design work"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

```plaintext
agreement: 12/20 scored items
agreement: 3/8 scored items
agreement: 2/5 scored items
agreement: 0/1 scored items
agreement: 0/1 scored items
agreement: 0/1 scored items
agreement: 1/1 scored items
agreement: 15/20 scored items
agreement: 2/3 scored items
agreement: 1/1 scored items
agreement: 16/20 scored items
agreement: 1/2 scored items
agreement: 1/1 scored items
agreement: 15/20 scored items
agreement: 3/5 scored items
agreement: 1/2 scored items
agreement: 1/1 scored items
agreement: 18/20 scored items
agreement: 1/1 scored items
agreement: 19/20 scored items
```

**Issue analysis**

<!-- [One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.] -->

**Issue**: `issue-01`
**Rubric decision**: `accept`
**Gold label**: `accept`
**Reasoning**: all required categories (`maintainer-active`, `repo-in-use`, `not-worked-on`, `policy-allows-ai`) passed since the repo indeed has an active maintainer (a comment on #16275 within 33 days), the repo is in active use (latest release is 2026-07-31), no one has worked on it (no assignees, claim comments, linked PRs), and AI use is allowed ("generative AI tools welcome").

**Check rationale**

<!-- [One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.] -->

**Name**: `policy-allows-ai`
**Evidence**: `CONTRIBUTION.md` > "Generative AI" section
**Pass condition**: AI _must not_ be banned, but permitted use with conditions is ok
**Weight**: required
**Reasoning**: Pointing specifically to `CONTRIBUTION.md` then to a "Generative AI" section works since those are standard filenames/section names for contributor-oriented AI use info. AI shouldn't be banned because this course requires AI-assisted contribution, but using the tool responsibly is needed - both in this course and in OSS, so conditions are fine. The weight is required since this check should be used to filter issues.

**Trade-offs**

<!-- [What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

While this `policy-allows-ai` check didn't throw off my rubric from the gold labels, there is a small edge case that it will miss: a highly restrictive AI-use policy whose adherence takes a long time, is tedious, etc. For example, one may require that all prompts and responses be explicitly disclosed along with the model and a link to the chat. This sort of bookkeeping overhead would disqualify an issue (or repo entirely) in my mind, which is difficult to codify in a rubric.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

<!-- [Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.] -->

1. Issue 68 falls within my available time (2-4 hours), and it a relatively contained and specific error: zero-division due to an empty index.
2. The verdict correctly identified that the maintainers were active and the repo is in use (as per this course structure!) and that no one has worked on this issue yet, the policy implicitly allows AI, and the scope fits my preferences. I'm satisfied by the rubric's performance. The only thing I grasped that the rubric did not was an intuitive comfort with the issue since I understood how I'd go about fixing it without even looking at the repo yet.
3. If there's a cap on the number of people on a certain issue, I think Issue 68 might be somewhat difficult to claim since it's a "good first issue" and among the easier-seeming ones in its label.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
