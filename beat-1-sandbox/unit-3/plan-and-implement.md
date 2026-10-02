# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

<!-- [Your GitHub username, exactly as it appears on your profile - no @, no
profile URL. Your comment upstream is identified by this name, and it is
the only thing that ties it to you. Several students may plan the same
house issue, so this is what keeps their comments off your score and
yours off theirs.] -->

`krishpatel2067`

**Plan comment**

<!-- [Link to the comment where you posted your plan on the issue. Use the comment's own
permalink. **Then paste the text of that comment underneath the link** — the pasted text is
what this field is graded on, so copy across what you actually posted.] -->

[Link](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68#issuecomment-5956223152)

````md
Successfully repro-ed the issue based on the comments above. I have a clear, targeted plan that involves adding a small guard against an empty list. Here are the details:

## Diagnosis

`KeywordSearcher.index(self, chunks: list[dict])` lacks a guard against an empty `chunks` array, causing the `tokenized_corpus` to be an empty list. The empty lists then gets passed to `BM25Okapi`, which doesn't handle the case of an empty list, leading to a corpus size of 0 and causing `ZeroDivisionError` when used as a divisor.

## Scope

Only involves touching:

- `rag/retriever/keyword_search.py` (specifically, the method `KeywordSearcher.index()`)
- `tests/unit/test_keyword_search.py` (to remove the `@pytest.mark.xfail` marker)

The issue only involves an edge case that single method, irrespective of how the edge case gets created, so the fix is a tightly scoped.

## Approach

1. Create a guard in `index()` after `self.chunks = chunks`.
   - If the parameter `chunks` is empty, log a warning and return immediately without ever tokenizing or calling the `BM25Okapi` constructor.
2. Confirm that setting `self.chunks = chunks` doesn't cause issues later on by tracking the use of `self.chunks` in the rest of the file. Since `search()` already guards against an empty `self.chunks`, allowing it to be empty is fine.
3. Remove the `@pytest.mark.xfail` marker above the `test_empty_index` in `test_keyword_search.py`, as required by the issue.

## Test

Currently, the only test that fails in `test_keyword_search.py` is `test_empty_index`, which tests exactly the edge case in question. I plan to run the test file after my change, and if the failing test passes, the change is successful. Since this is a unit-test-level failure, a higher-level or end-to-end test isn't required.

## Risks/Unknowns

While I'm certain that adding a guard that retains empty chunks won't cause any consequent issues in the RAG pipeline, there is a slim chance that the guard gets propagated to the end user in a non-user-friendly message (an unhandled error, etc.), depending on how the rest of the RAG pipeline and the frontend are built.
````

---

## Your branch

**Branch**

[The name of the branch you built the change on, exactly as it appears in your fork. The
naming shape is a type prefix, then the issue number, then a short description. **The issue
number in the branch name must be the number of the issue you claimed** — a name carrying
any other number does not satisfy this field.]

**Evidence**

[Your Unit 2 reproduction steps re-run against the built change: the before, then the
after. Paste both, including the commands you ran and their output.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

```plaintext
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 19/20 scored items
```

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->

Package: `pkg-20`
Rubric label: `reject`
Gold label: `reject`
Reasoning:
The candidate plan was solid but it didn't disclose AI use when the repo's contribution policy clearly requires it. The rubric looked at both the plan itself and thread highlights, the latter of which reveals the contributor's use of AI to propose a solution, which wasn't clearly disclosed in the plan. Hence, the rubric scored `reject`.

**Check rationale**

<!-- [Quote one check from the `rubric.md` you uploaded to `tools/plan-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->

Check: `ai-use-disclosure`
Evidence: Contribution policy, thread highlights
Passing conditions: If policy requires disclosing AI use, plan must do so if any AI use is mentioned in any of the evidence
Weight: required
Reasoning:
The rubric makes sure to enforce a match between the plan and repo contribution policy. It also adds thread highlights as evidence with explicit directions to search there too for any suspected AI use. Often times, contributors "leak" or casually mention AI use without firmly disclosing it. This rubric wording helps pick up on those subtle hints.

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

One tradeoff is that the `clear-plan` check is a bit too restrictive with the passing condition "Unambiguous steps, certainty expressed, files listed, approach followable." However, in reality (and as expressed in the evidence guide), there is often some uncertainty in real life. I started with approximating this uncertainty to 0 (like in an ideal case), and it worked out by leading me to 19/20 agreement right off the bat, so this is a trade-off I'm willing to accept given the sample. In a real-world grader, however, some degree of uncertainty would need to be allowed. Then, the harder question becomes how much, which can be answered by training on many more human-graded plans (certainly more than the 20 we have here!).

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
