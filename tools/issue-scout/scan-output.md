Scan results (2026-10-16)

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