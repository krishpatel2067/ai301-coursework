# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

<!-- [Link to the pull request you opened. It must be the pull request's own page on the Path
Review repo, not your fork's branch page.] -->

**Branch**

<!-- [The name of the branch the pull request comes from, exactly as it appears in your fork.
The naming shape is a type prefix, then the issue number, then a short description. **The
issue number in the branch name must be the number of the issue the pull request fixes** —
a name carrying any other number does not satisfy this field.] -->

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

```plaintext
agreement: 19/20 scored items
```

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->

**Package**: `pkg-01`
**Rubric label**: `reject`
**Gold label**: `reject`
**Explanation**:

The rubric rejected the PR because it was visibly deviating from the required pull-request template (e.g. no "Closes ####" line). This kind of direct check against some information (like the repo guidelines) was easy for the rubric to evaluate on.

**Check rationale**

<!-- [Quote one check from the `rubric.md` you uploaded to `tools/pr-precheck/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->

**Check**: `tested`
**Evidence**: Issue, repro evidence, candidate plan, PR
**Passing condition**: PR must show that the change works, either through an automated testing suite or manually. The tests must match the test plan in the candidate plan.
**Weight**: `required`
**Explanation**:

This check specifically revolves around testing since many repos require all its existing test to pass (or at least no new fails) because of the PR. The check also allows for manual testing since not all PRs revolve around changes that can be automatically tested. For example, a UI change often requires manual testing. In that case, the rubric simply relies on the tests' thoroughness and convergence with the test plan.

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

The rubric has a good heuristic for determining what a clean diff looks like. Similar to a human, it can easily see that a few files targeted to the same files that the plan lists in its scope is a clean diff. However, just like a human looking at the PR only, the rubric cannot verify whether the diff reflects a working change or introduces some silent bug, especially one that requires a much broader context on the repo than the diff provides. However, this is acceptable not just because it matches human grading already (surpassing it is not the goal), but also because that sort of check against an insidious bug should have been part of the candidate plan (which this tool does not grade, rather the tool uses it as ground truth). Ideally, the previous week's tool (`plan-check`) should've caught this, but it is often the case that bugs do slip through and new issues have to be created.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
