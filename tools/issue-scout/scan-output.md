# Scan Output

## 2026-11-06 (Run 2; exclude claim comments by me)

Only #8480 is accepted. #379 and #380 are rejected, and both are already closed.

Ranked read-out

All three came in as direct URLs, so there was no search query or top-N ranking.

1. swisspost/design-system#8480: accept
- Maintainer active: pass. Recent commits reference issues or PRs, e.g. 2026-11-05 "fix(components): … (#8684)".
- Repo in use: pass. Pushed today, not archived, latest release 2026-10-20.
- Not worked on: pass. There are no assignees and no linked PRs. The only comments are yours (2026-10-22 and 2026-10-28), and a maintainer has not replied yet.
- AI policy: pass. I found no AI ban in .github and no root CONTRIBUTING.md, and the repo has a copilot-instructions.md. Silence passes under the rubric.
- Repo mature: pass. The repo was created in 2022 and has 181 stars.
- Scope feasible: pass. It asks for one workflow that fills Hours Spent (h) from the estimate when the field is empty and the issue is set to done.
- Fit: it is open, labelled good first issue, and has no assignees. I could not check whether it is locked, because gh does not expose that field.
- Difficulty: moderate. You have to find where the workflow lives. It probably means GitHub Projects v2 field automation. The "tbd" PR-template checkbox is an open edge, which you already asked about.
- Practical note: your claim comments are already on the issue, but the maintainer, oliverschuerch, has not answered in about two weeks. Waiting for their reply before building is worthwhile.

2. DCGM/semant-demo#379: reject
- Failed check: not-worked-on. It is assigned to omarekom and was fixed through PR #416, which closed it.
- Failed check: repo-mature. The repo has 7 stars, under the 100 required.
- Fit: the issue is closed.

3. DCGM/semant-demo#380: reject
- Failed check: not-worked-on. It is assigned to martinkostelnik, and a claim comment from Pratham2511 sits in the thread (2026-10-16).
- Failed check: repo-mature. The repo has 7 stars, under the 100 required.
- Fit: the issue is closed. A maintainer also said CI is not set up for external PRs (tracked in #393).

Scan-notes friction: the rubric treats "other than mine" as the only exception for claim comments, which works for #8480. The two semant-demo issues were already closed, and "open" is only in the fit profile, not the rubric. Consider adding an issue-open required check.

```json
[
  {
    "item": "https://github.com/swisspost/design-system/issues/8480",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "2026-11-05 commit 'fix(components): ... (#8684)'; commits within days and linked to issues/PRs"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "pushed 2026-11-07, not archived, latest release 2026-10-20"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "no assignees, no linked PRs; only comments are the user's own"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no AI ban found in .github; no CONTRIBUTING AI section; copilot-instructions.md present"},
      {"name": "repo-mature", "grade": "pass", "evidence": "created 2022-02-23, 181 stars"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "one workflow: autofill Hours Spent from Hours estimate when empty on done"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/DCGM/semant-demo/issues/379",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "2026-11-06 merges of PR #603/#604 referencing #596"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "pushed 2026-11-07, not archived, release v0.1.31 on 2026-11-03"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "assignee omarekom; closed via PR #416"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no AI ban found in CONTRIBUTING.md"},
      {"name": "repo-mature", "grade": "fail", "evidence": "7 stars (<100)"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "single bug with repro and root cause in popover close handling"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/DCGM/semant-demo/issues/380",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "2026-11-06 merges of PR #603/#604 referencing #596"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "pushed 2026-11-07, not archived, release v0.1.31 on 2026-11-03"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "assignee martinkostelnik; Pratham2511 claim comment 2026-10-16; issue closed"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no AI ban found in CONTRIBUTING.md"},
      {"name": "repo-mature", "grade": "fail", "evidence": "7 stars (<100)"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "one piece of work: sort tags and add a lightweight suggestion in AnnotationPopover"}
    ],
    "verdict": "reject"
  }
]
```

## 2026-11-06 (Run 1; rubric scope patch)

None of the three issues is acceptable under the rubric as written. The direct run skipped search and ranking.

Rejected, nearest miss first

1. swisspost/design-system#8480 ("Create a workflow to autofill the hours field") fails not-worked-on.
   - It is open, has no assignees, is unlocked, and carries the good first issue label.
   - The repo is healthy. The newest commit is from 2026-11-05 and most recent commits cite issue numbers. The repo has 181 stars, was created in 2022, and its latest release is 2026-10-20. CONTRIBUTING.md says nothing about AI, and silence passes.
   - The scope is one workflow, so it passes.
   - The failure is that two claim comments rom 2026-10-22 and 2026-10-28. Both are yours (krishpatel2067), and neither has had a maintainer reply. The rubric reads a claim comment as someone else beon it and doesn't separate out your own
   - Rubric tension: this is the case scan-notes.md is for. The check should probably exclude the candidate's own comments, or treat an unanswered claim t override it.
2. DCGM/semant-demo#379 fails not-worked-on and repo-mature. It is closed and assigned to omarekom, with a closed       linked PR (#416). The repo has 7 stars, b
3. DCGM/semant-demo#380 fails the same two checks. It is closed and assigned to martinkostelnik, and there is a claim   comment from Pratham2511. A maintainer saed yet and pointed to #393. It also has aclosed linked PR (#430). The repo has 7 stars.                                                                    
Your fit profile requires an open issue with no assignees. #379 and #380 break both rules, though fit never changes averdict.

```json
[
  {
    "item": "https://github.com/swisspost/design-system/issues/8480",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Latest default-branch commit 2026-11-05; recent commits cite issues/PRs (#868x, #8767)"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "pushed 2026-11-07, not archived, latest release 2026-10-20"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "No assignees or linked PRs, but claim comments on 2026-10-22 and 2026-10-28 (within a month; both by krishpatel2067, unanswered)"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI mention; silence passes"},
      {"name": "repo-mature", "grade": "pass", "evidence": "Created 2022-02-23, 181 stars"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "One GitHub workflow: autofill 'Time Spent (h)' from 'Hours' when empty on done"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/DCGM/semant-
    "checks": [
      {"name": "maintainer-active", "grade": 2026-11-06 referencing #596 and mergedPRs"},
      {"name": "repo-in-use", "grade": "pass1-07, not archived, release v0.1.31 on2026-11-03"},
      {"name": "not-worked-on", "grade": "faarekom; issue closed 2026-10-20; closedlinked PR #416"},
      {"name": "policy-allows-ai", "grade": TING.md has no AI ban (AI mentions are onlyabout test fakes)"},
      {"name": "repo-mature", "grade": "fail); created 2025-05-14"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "One bug with repro and root cause in AnnotationPopover
close handling"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/DCGM/semant-demo/issues/380",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Commits 2026-11-06 referencing #596 and merged     PRs"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "pushed 2026-11-07, not archived, release v0.1.31 on      2026-11-03"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "Assignee martinkostelnik; closed 2026-10-19; claim     comment 2026-10-16; closed linked PR #430"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI ban"},                          {"name": "repo-mature", "grade": "fail)"},
      {"name": "scope-feasible", "grade": "pass", "evidence": "One feature: alphabetical sort plus tag suggestion in AnnotationPopover"}
    ],
    "verdict": "reject"
  }
]
```

## 2026-10-16

The scan found 92 unique issues from the two queries. 92 survived the ranking filters, and I graded the top 5. Ties on 0 comments and the "docs:" title preference were broken by the sort order I used (updatedAt, then URL), so the order among tied results is arbitrary.

Accepted (in fit order)

1. DCGM/semant-demo#379 ("Creating new tag from selection in bugged"). Query 1 surfaced it. It ranked on 0 comments with no title prefix. It's a tight-scoped bug in a Vue and Python repo, labelled bug and good first issue.
2. DCGM/semant-demo#380 ("Sort and suggest tags in the text-selection popover"). Query 1 surfaced it. It ranked on 0 comments. It's labelled enhancement and backend, so it's more feature than fix. That fits your profile less well than #379 but doesn't change the verdict.

Rejected

- Ordixian/Kaguya#4 (a docs issue, which was the top-ranked title). It failed repo-in-use because there's no GitHub release. It also failed maintainer-active because 0 of the 4 issues are closed and there are no comments.
- SoroScan/soroscan#1634 (docs: fix broken documentation cross-links). It failed not-worked-on because open PR #1637 ("docs: fix broken internal links") cross-references it. It also failed repo-in-use because there's no release.
- 4EYES44/Nopecha-extension-python#12 (README cleanup). It failed repo-in-use because the last push was 2025-12-12 and there's no release. It also failed maintainer-active because 0 of its 21 issues are closed.

Friction for scan-notes.md
- Query 2 has a typo (javacript). I ran it as written, and GitHub still returned results, but you should fix it. Query 2 contributed none of the top 5.
- The "latest release within a year" check rejects small repos that never cut GitHub releases. Kaguya mentions "Release 2.13.0" in a commit but has no release object.
- Several top results are brand-new repos where every commit and issue is dated the same day. The ranking filters can't see that.
- #379 and #380 were both filed minutes before the scan. The maintainer-active check passes on closed-issue volume and fresh commits, but you haven't seen a first response to an outside contributor.
- If you take #379, claim it upstream with a comment first, as scope.md requires.


```json
[
  {
    "item": "https://github.com/DCGM/semant-demo/issues/379",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "153 of 232 issues closed; latest commit 2026-10-16 merges issue-249 branch"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "not archived; pushed 2026-10-16; latest release 2026-10-16"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "no assignees, 0 comments, no linked or cross-referenced PRs"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI ban; AGENTS.md exists for coding agents"},
      {"name": "scope-fits", "grade": "pass", "evidence": "labels bug + good first issue; Vue/Python repo, fix-type"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/DCGM/semant-demo/issues/380",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "153 of 232 issues closed; latest commit 2026-10-16"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "not archived; pushed 2026-10-16; latest release 2026-10-16"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "no assignees, 0 comments, no linked or cross-referenced PRs"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI ban; AGENTS.md exists for coding agents"},
      {"name": "scope-fits", "grade": "unclear", "evidence": "labelled good first issue + backend + enhancement; feature-type, weaker fit to docs/fix profile"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/SoroScan/soroscan/issues/1634",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "981 of 1034 issues closed; commits 2026-10-12"},
      {"name": "repo-in-use", "grade": "fail", "evidence": "pushed 2026-10-16 but releases/latest returns 404 (no release)"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "open PR #1637 'docs: fix broken internal links' cross-references the issue"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI ban; AGENTS.md present"},
      {"name": "scope-fits", "grade": "pass", "evidence": "labels documentation + good first issue; docs fits profile"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/Ordixian/Kaguya/issues/4",
    "checks": [
      {"name": "maintainer-active", "grade": "fail", "evidence": "0 of 4 issues closed, no comments on the issue; commits not linked to issues"},
      {"name": "repo-in-use", "grade": "fail", "evidence": "pushed 2026-10-16 but releases/latest returns 404 (no release)"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "no assignees, 0 comments, no linked PRs"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI mention"},
      {"name": "scope-fits", "grade": "pass", "evidence": "good first issue; docs walkthrough fits profile"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/4EYES44/Nopecha-extension-python/issues/12",
    "checks": [
      {"name": "maintainer-active", "grade": "fail", "evidence": "0 of 21 issues closed; last commit 2025-12-12"},
      {"name": "repo-in-use", "grade": "fail", "evidence": "last push 2025-12-12 (over 6 months ago); no release"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "no assignees, 0 comments, no linked PRs"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no CONTRIBUTING.md or AI policy found; silence passes"},
      {"name": "scope-fits", "grade": "pass", "evidence": "documentation + good first issue; README cleanup fits profile"}
    ],
    "verdict": "reject"
  }
]
```