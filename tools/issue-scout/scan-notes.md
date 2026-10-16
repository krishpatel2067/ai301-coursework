# Scan Notes

## 2026-10-16

- Observations:
  - All top 5 issue repos have < 10 stars (by, proxy very little traffic)
  - Several were brand new repos
  - I would most likely not contribute to any 5 of the repos
  - Release-within-1-year requirement sank 3 of the 5
  - The at-least-20%-comment-count requirement a bit too harsh: sank 1 of the 5
  - repo-in-use counting last push/commit (not merge) sank 1 of the 5
- Changes:
  - Add required rubric check `repo-mature` for >= 100 stars and repo age >= 6 months
  - Allow merges to count within the 6-month-back window
  - Make maintainer-active solely based on merges from issues (not comment count)
