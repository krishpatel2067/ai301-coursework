# Contribution: Create a workflow to autofill the hours field

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in the
repository is not read. **Keep every section header below under its exact name** — the format
criteria grade exactly that. Your course repo link is the whole submission: no tool files and no
evidence uploads are part of Assignment 5.

**Contribution Number:** 1 **Student:** Krish A. Patel **GitHub Username:** krishpatel2067
**Issue:** https://github.com/swisspost/design-system/issues/8480 **Pull Request:** [GitHub PR link,
once opened]

One repository, built across units 5 to 8, telling the whole story of your real contribution. Fill
it as you work, not at the end — the sections below ask for evidence that is far easier to write
down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it just
numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull Request, ends with a Toolkit
block: which tool did that phase's work and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change because of them. Together the blocks
are the thread the rubric's Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than reconstructing them later.

A Toolkit block looks like this (copy it into each story section and fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work, starting below: what you built
or changed that week, what broke, and what you changed because of it. The blocks tell the story
where it happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each one in the week it belongs to.

**Unit 5: repurposing and refitting `issue-select` to `issue-scout`**

Knowing that there are hundreds of issues to fit my taste profile, I tightened my profile, shedding
extra languages and technologies, adding the types of issues I wanted (docs or fix), and mandating
several key issue characteristics. On the first scan, I realized that many of top candidates were
from brand new repos with very few stars, if any (and I want to contribute to a repository with real
current impact). To address this shortcoming, one major change I made was adding a rubric check
`repo-mature` to mandate >= 100 stars and repo age >= 6 months.

**Unit 6: adding a voice guard and repo-memory file**

Despite the instructions, I chose to install the voice guard at the repo-level, not at the
user-level, to avoid having stale skills / other files in my `~/.claude/`. In the future, if I end
up having to copy-paste the voice guard multiple times, I will strongly consider making it
user-level. But until then, I feel more comfortable with repo-level.

The voice guard passed my claim draft on the first try, which makes sense since my claim comment was
short and avoided a lot of the rejection qualities outlined in `voice-guide.md`.

The repo-memory file was fairly simple to write. The only difficult part was outlining the testing
process since I the repo instructed me to use `act`, which I had no former experience with. Some
quick research unblocked me, but I'll confirm with Claude whether my commands outlined are sound.

**Unit 7: dealing with a strict ship gate**

The ship gate was quite strict because it relied on a `pr-precheck`'s rubric I had designed for
user-facing bug-related PRs, so it could not adjust with my non-user-facing feature-related PR. For
example, since the PR involved creating a GitHub workflow dealing with GitHub projects, the repo's
recommendation of `act` for locally testing workflows didn't apply. So, I had to put `echo "N/A"` in
the ship gate manifest to reflect that I had to manually test my feature (the `echo` so the hook
doesn't exit with "command not found"). I also modified my `pr-precheck` rubric to allow "N/A" for
automated testing with a stated reason, further reflecting that real world contribution is messier
and full of exceptions than sandbox contribution.

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it drafted, what you did with
the draft.]

---

## Why I Chose This Issue

I mainly used the
[Issue Selection site](https://open-source-issue-tracker.onrender.com/?language=Python&language=JavaScript&language=TypeScript&tag=easy&tag=good+first+issue&page=23)
to find my issue. The scan did not help in this respect since it surfaced issues that I didn't
prefer, either due to difficulty, low repo star count, etc. This issue fits my profile because it is
very tightly scoped yet still contains an opportunity for me to learn. Ironically, it doesn't
involve Python or JavaScript, my original preferred language when looking for an issue. Nonetheless,
this issue is a great opportunity for me to learn GitHub workflow syntax and perhaps GraphQL.

Originally, my scout rejected the issue since it saw my own claim comments and thought someone was
already working on the issue. I adjusted the scout rubric to exclude myself when considering claim
comments (as well as open PRs and assignees), and the scout accepted this issue. This was one
shortcoming I found with the scout in the wild, an edge case that I didn't run into in the sandbox,
where claim comments were more formal and posted after the rubric run. Now that I patched the edge
case, it should work a bit better in the wild, though it could run into other problems that I
haven't come across or anticipated yet.

**Claim comment**: https://github.com/swisspost/design-system/issues/8480#issuecomment-6330381566

**Toolkit**

- Tool: `issue-scout` - used it to objectively confirm my issue pick fits my preferences
- What it produced: verdict: pass on this issue, reject on others
- Difficulties: due to overly strict wording, it rejected issues with my own claim comment
- What changed: patched the problem noted above by excluding myself/my comments/PRs in the
  `not-worked-on` check

---

## Understanding the Issue

**Problem Description**

What is missing: a GitHub workflow to automatically fill the "Hours" field based on the "Time Spent
(h)" field (check repro steps for confirmation of this).

**Expected Behavior**

There should be a GitHub workflow that auto-fills the "Hours" field based on the "Time Spent (h)"
field.

**Current Behavior**

There is currently no GitHub workflow in `.github/workflows/` that auto-fills the "Hours" field
based on the "Time Spent (h)" field.

**Affected Components**

Only `.github/workflows/`.

**Toolkit**

- Tool: no tool used to understand the issue
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Reproduction Process

**Environment Setup**

No specific environment needed - just the `design-system` repo cloned locally and open in a text
editor.

**Steps to Reproduce**

1. Look at all the files in `.github/workflows/`. None indicate they are to autofill the "hours"
   field.
2. Perform a repo-wide search on "hours". Nothing shows up.

**Reproduction Evidence**

- **Commit showing reproduction:** none
- **Screenshots/logs:**

Files in `.github/workflows/` via `tree`:

```plaintext
├── build-documentation.yaml
├── build-tokens.yaml
├── create-token-pr.yaml
├── deploy-documentation.yaml
├── dry-run-publish.yaml
├── e2e-tests.yaml
├── fetch-icons-v9.yaml
├── fetch-icons.yaml
├── label-stale-review-prs.yaml
├── lint.yaml
├── playwright-tests.yml
├── pr-title-lint.yaml
├── release-documentation.yaml
├── release.yaml
├── scripts
│   ├── check-packages-on-npm.mjs
│   ├── icons.mjs
│   └── validate-icons.mjs
├── snapshot-tests.yaml
├── sonar-analysis.yaml
├── stale.yaml
├── unit-tests.yaml
├── validate-icon-downloads.yaml
└── visual-tests.yaml

2 directories, 23 files
```

Search results from step 2:

```plaintext
6 results - 4 files

apps/documentation/src/stories/misc/migration-guide/migrationv9-10.component.ts:
  1074                                <code-block
  1075:                                 code=${`<!-- template.html -->\n<ngb-timepicker\n  [(ngModel)]="appointmentTime"\n  [seconds]="true"\n  [spinners]="true"\n  [meridian]="false"\n  [hourStep]="1"\n  [minuteStep]="5"\n  [secondStep]="10"\n  [readonlyInputs]="false"\n></ngb-timepicker>`}
  1076                                ></code-block>

  1100                                  <li>
  1101:                                   <strong>Step behavior (<code>hourStep</code>,
  1102                                    <code>minuteStep</code>, <code>secondStep</code>):</strong>

packages/icons/src/icons/post/report.json:
  13129            "Express 24/7",
  13130:           "Expressed 24 hours a day",
  13131            "Espresso 24 ore su 24",

packages/internet-header/CHANGELOG.md:
  801
  802: - Sanitized hours fields in footer against XSS "Incomplete multi-character sanitization" issue. (by [@imagoiq](https://github.com/imagoiq) with [#2807](https://github.com/swisspost/design-system/pull/2807))
  803

```

- **My findings:** There is no existing GitHub workflow (or something similar) to autofill the
  "hours" field in the associated GitHub project.

**Toolkit**

- Tool: `repro-check` - used to check my repro draft against the issue.
- What it produced: initially it failed before the rubric adjustment, but afterwards, it passed.
- Difficulties: it initially failed because it didn't recognize that a full environment info wasn't
  necessary in this edge-case issue and a lack of version numbers isn't a weakness in this issue
- What changed: adjusted the rubric checks `has-evidence` and `right-target` to apply to only
  bug-related issues, leading to a pass

---

## Solution Approach

**Analysis**

No workflow under `.github/workflows/` touches the Projects board, so nothing copies the "Hours"
estimate into "Time Spent (h)" when an issue is done.

**Proposed Solution**

Add one new workflow, `.github/workflows/autofill-time-spent.yaml` (`.yaml` matches the other
workflows). When an issue is closed (moved to Done), it will:

1. Find the issue's item on the Projects v2 board.
2. Read its "Time Spent (h)" and "Hours" values.
3. If "Time Spent (h)" is filled, do nothing. If it's empty, set it to the "Hours" value.

Decisions:

- **Trigger:** `issues: closed`, plus `workflow_dispatch` (takes an issue number) for manual runs
  and testing. Actions has no trigger for Projects v2 item changes, so closing the issue is the
  closest signal to "set to done".
- **Auth:** the default `GITHUB_TOKEN` can't write to an org-level Projects v2 board, so the
  workflow needs a token with the `project` scope. I will use `SWISSPOSTDEVS_ACCESS_TOKEN` secret
  since other workflows use that (happy to change it if you want).
- **IDs:** nothing hardcoded. The script looks up the project, item and field IDs by name at run
  time.
- **Field names:** "Time Spent (h)" and "Hours". Both are constants at the top of the script, so a
  rename is a one-line change.
- **Implementation:** `actions/github-script` (already used in `label-stale-review-prs.yaml`) with
  GraphQL calls, rather than using the raw `gh api`.
- **Skipped:** if the item isn't on the board, or "Hours" is empty, log a message and exit without
  failing.

**Scope**

Only the new workflow file. No other files, no production code. The "(tbd)" PR template checkbox is
left out; happy to do it as a follow-up if wanted.

**Implementation Plan**

1. Create `.github/workflows/autofill-time-spent.yaml` with the trigger above, minimal
   `permissions`, and the token secret.
2. Write the script: query the issue's project item and the two field values; stop if "Time Spent
   (h)" is filled; otherwise run the `updateProjectV2ItemFieldValue` mutation with the "Hours"
   value.
3. Test in my fork. `act` can't emit Projects events, so I'll make a personal Projects v2 board with
   the same two fields and my own token as a secret, then run via `workflow_dispatch` and by closing
   a test issue. Cases:
   - empty (gets filled)
   - filled (unchanged)
   - "Hours" empty (skipped)
   - issue not on the board (skipped).

   Run links will come in the PR.

[Record deviations here as they happen: what changed mid-build and why. A recorded deviation is
honest work; silent drift is not.]

**Toolkit**

- Tool: `plan-check` - used to check whether my plan and plan comment are ready to post.
- What it produced: it rejected my plan twice reasonably; after overhauling my plan, it accepted.
- Difficulties: it rejected my plan the first time due to getting the direction of the "Hours" ->
  "Time Spent (h)" wrong, then it rejected the second time due to my plan being vague and
  technically inaccurate.
- What changed: I used Claude to get more accurate technical details on the solution and added those
  details to my plan.

---

## Testing Strategy

Since this issue was a non-user-facing feature request, the pre-implementation testing was minimal
to none. However, I manually tested my implementation by creating a test GitHub project and various
GitHub issues as follows:

- "Time spent (h)" empty, "Hours" not empty -> fill "Time Spent (h)"
- "Time spent (h)" not empty, "Hours" not empty -> skip
- "Time spent (h)" not empty, "Hours" empty -> skip
- "Time spent (h)" empty, "Hours" empty -> skip
- no project tied to issue -> skip

My manual testing yielded these expected results both after closing an issue (automatic trigger) and
clicking "Run workflow" and entering the issue number.

Note: I did not have to touch the production tests since I only worked in the `.github/` folder, not
production code.

**Toolkit**

- Tool: some `Claude Code Opus 5.5` to provide info on setting up my testing.
- What it produced: corrections to my assumptions (e.g. PATs, not fine-grained tokens) and things to
  watch out for (e.g. updating `main` to update workflow).
- Difficulties: initially hard-coded project name incorrectly skipped the field fill.
- What changed: I had Claude update the workflow to derive the project name from the event issue
  (see Implementation Notes), which works for any linked project, wether on my fork or upstream.

---

## Implementation Notes

**2026-11-07**

Built the initial workflow in `.github/workflows/autofill-time-spent.yaml`.

**2026-11-07**

Reduced over-engineering by assuming that event issue is only part of 1 project (reasonable since
the org has a single project).

**2026-11-07**

Substituted hard coded project with event issue's linked project, if any.

**2026-11-07**

Switched `github-script` to v9 (latest) from v7 (using deprecated Node 20).

**2026-11-07**

Opted for the commit SHA for `github-script` v9 rather than the tagged object SHA for improved
security.

**Toolkit**

- Tool: `Claude Code Opus 5.5` to generate `autofill-time-spent.yaml` based on my plan.
- What it produced: the initial script and the subsequent revisions listed above.
- Difficulties: due to gaps in my plan, it over-engineered project searching by assuming an issue
  can appear in multiple projects.
- What changed: I re-prompted Claude to assume up to 1 project per issue to simplify the script.

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The status is a fact you record, never a
grade: the PR is graded as opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the Toolkit blocks above are full of
them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story already shows you using: the doc
you followed to set the environment up, the thread that explained the bug, the person who answered
you. One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
