I invoked issue-select by mistake. You asked for issue-scout, and issue-select's scope only allows the Path Review repo. I'm loading issue-scout now.

● Skill(issue-scout)
Successfully loaded skill

  Ran 2 shell commands

Direct mode. I'll gather evidence for all three.

  Ran 3 shell commands

I graded all three in direct mode, so there was no search or ranking step. One of the three is accepted: Ocelot-Social #3330, a Vue bug fix. Logixia #113 and Loopi #79 are rejected.

Ranked read-out

Accepted

1. Ocelot-Social #3330 (HTTP 500 on a deleted user's profile instead of a 404)
   - It fits your profile: a tightly scoped bug fix in the Vue webapp with a good first issue label.
   - Caveats the rubric doesn't catch:
     - The issue is stale. It was imported from Human-Connection in 2020 and last updated in January 2021.
     - Its code pointer (webapp/pages/profile/_id/_slug.vue#L358) refers to the old repo, so check that the bug still reproduces before claiming it.
     - The one cross-referenced PR (#3140) is closed and unrelated.

Rejected

- Logixia #113 (README Log search snippet fix) fails repo-mature. The repo has 6 stars, below the 100 minimum. Everything else passed, and it would be a good docs-style fit otherwise. It also has a stated prerequisite: a broken re-export must be fixed on main first.
- Loopi #79 (prevent infinite loops) fails two checks:
  - not-worked-on: open PR #102 says "Fixes #79" and was opened 2026-02-25. It isn't formally linked, but the thread and cross-references count.
  - maintainer-active: the last commit was 2026-06-09, about 4 months ago, so over the 3-month limit.

All three issues have no assignees, none of the three CONTRIBUTING.md files mentions AI, and no repo is archived. I treated that silence on AI as a pass, per the evidence guide.

```json
[
  {
    "item": "https://github.com/Ocelot-Social-Community/Ocelot-Social/issues/3330",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Latest default-branch commits 2026-10-16, all PR-linked (e.g. #10558, #10553)"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "Not archived; pushedAt 2026-10-16; latest release 3.21.1 on 2026-10-13"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "No assignees; only linked PR #3140 is closed (<=1 allowed); only comment is a 2020 member comment"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI/generative section; silence passes"},
      {"name": "repo-mature", "grade": "pass", "evidence": "Created 2020-10-04; 115 stars"},
      {"name": "scope-fits", "grade": "pass", "evidence": "Labels: good first issue, bug; Vue webapp bug fix matches profile"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/Logixia/logixia/issues/113",
    "checks": [
      {"name": "maintainer-active", "grade": "pass", "evidence": "Commits 2026-10-09 by webcoderspeed, PR-linked (#151-#153)"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "Not archived; pushedAt 2026-10-12; release v1.12.5 on 2026-10-09"},
      {"name": "not-worked-on", "grade": "pass", "evidence": "No assignees, no comments, no linked PRs"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI section; silence passes"},
      {"name": "repo-mature", "grade": "fail", "evidence": "stargazerCount 6 (<100); created 2025-09-09"},
      {"name": "scope-fits", "grade": "pass", "evidence": "Labels: documentation, good first issue, hacktoberfest; README docs fix"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/Dyan-Dev/loopi/issues/79",
    "checks": [
      {"name": "maintainer-active", "grade": "fail", "evidence": "Newest default-branch commit 2026-06-09, ~4 months before today (>3 months)"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "Not archived; pushedAt 2026-06-09 (<6 months); release v1.10.4 on 2026-06-09"},
      {"name": "not-worked-on", "grade": "fail", "evidence": "Open PR #102 'fix: add cycle detection...' says 'Fixes #79' (opened 2026-02-25)"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI section; silence passes"},
      {"name": "repo-mature", "grade": "pass", "evidence": "Created 2025-09-17; 197 stars"},
      {"name": "scope-fits", "grade": "pass", "evidence": "Labels: bug, good first issue, help wanted; bounded fix in a JS/TS app"}
    ],
    "verdict": "reject"
  }
]
```