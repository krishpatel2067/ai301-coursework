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

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
paste the output here, including the closing JSON block
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

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

While this `policy-allows-ai` check didn't throw off my rubric from the gold labels, there is a small edge case that it will miss: a highly restrictive AI-use policy whose adherence takes a long time, is tedious, etc. For example, one may require that all prompts and responses be explicitly disclosed along with the model and a link to the chat. This sort of bookkeeping overhead would disqualify an issue (or repo entirely) in my mind, which is difficult to codify in a rubric.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
