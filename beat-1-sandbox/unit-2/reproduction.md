# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

<!-- [Your GitHub username, exactly as it appears on your profile — no `@`, no profile URL. Your
comments upstream are identified by this name.] -->

_krishpatel2067_

---

## Posted upstream

**Claim comment**

<!-- [Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.] -->

[Claim comment](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68#issuecomment-5847004532)

Claim comment text:

```md
Hi, I'd like to address this bug as my first contribution.

From my understanding:

1. `KeywordSearcher.index()` receives can empty list `[]`.
2. It passes the empty list to the `rank-bm25` library.
3. `rank-bm25` raises a `ZeroDivisionError`.

Proper behavior: no `ZeroDivisionError`; mirror `search()`'s approach: separately handle the empty case.

My next steps:

1. Repro the bug by triggering the `index()` empty case and get the `ZeroDivisionError` in question.
2. If the repro is successful, I'll start working on a fix - most likely a conditional handler that catches the empty case before it reaches `rank-bm25`.
3. I'll ensure the fix passes all tests and CI before posting here.

Will follow up soon with repro details.
```

**Reproduction comment**

<!-- [Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.] -->

[Repro comment](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68#issuecomment-5847296523)

Repro comment text:

```md
I've successfully reproduced the `ZeroDivisionError` bug.

How to reproduce:

Directly call `KeywordSearcher.index()` with an empty list:
```

python -c 'from rag.retriever.keyword_search import KeywordSearcher; searcher = KeywordSearcher(); searcher.index([])'

```

Output:

```

Traceback (most recent call last):
File "<string>", line 1, in <module>
File "{system path}/pathreview-ai301-fa26-s1/rag/retriever/keyword_search.py", line 25, in index
self.bm25 = BM25Okapi(tokenized_corpus)
^^^^^^^^^^^^^^^^^^^^^^^^^^^
File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 83, in **init**
super().**init**(corpus, tokenizer)
File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 27, in **init**
nd = self.\_initialize(corpus)
^^^^^^^^^^^^^^^^^^^^^^^^
File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 52, in \_initialize
self.avgdl = num_doc / self.corpus_size
~~~~~~~~^~~~~~~~~~~~~~~~~~
ZeroDivisionError: division by zero

```

Note: I replaced the path before the repo directory with `{system path}`.

Expected output: a warning that the index is empty, just like `search()`.

Run the **control** (non-empty index):

```

python -c 'from rag.retriever.keyword_search import KeywordSearcher; searcher = KeywordSearcher(); searcher.index([{ "text": "test" }])'

```

Output:

```

2026-09-26 10:53:05 [info ] keyword_index_built chunk_count=1

```

Lines up with the issue: `ZeroDivisionError` when passing in an empty list to `KeywordSearcher.index()`.

Environment details:

- Windows 11 25H2 (arm64)
- Ubuntu 24.04 on WSL2
- Python 3.12.3
- `rank-bm25` 0.2.2
- Repo at commit `f89c06f`
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68#issuecomment-5847296523
```

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

```
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 18/20 scored items
agreement: 2/2 scored items
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 1/1 scored items
agreement: 20/20 scored items
```

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->

**Package**: `pkg-04`
**Rubric label**: `reject`
**Gold label**: `reject`
**Reasoning**:
The rubric correctly rejected the package because the repro comment just claimed it reproduced the bug without providing any evidence. This me-too-only comment doesn't help much. Though the rubric didn't pick up on this, both the comment and repro comments are also overly casual and unprofessional.

**Check rationale**

<!-- [Quote one check from the `rubric.md` you uploaded to `tools/repro-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->

**Check**: `discloses-ai`
**Evidence**: repo AI_POLICY.md, repro comment
**Pass condition**: repro or claim comment must disclose AI use (or the lack thereof) if the repo explicitly requires AI use disclosure ("AI is welcome" is not a disclosure requirement, but "AI use must be disclosed" is)
**Weight**: `required`
**Reasoning**:
This check was tough to nail: too lose and it'd incorrectly pass `pkg-20`, too strict and it'd incorrectly reject `pkg-03`. I specifically included the two quoted examples to show the skill what counts as a repo-mandated AI disclosure requirement versus an adjacent AI statement. The check also requires some mention of AI use in the cliam or repro comment even if it's "I didn't use AI" if an AI disclosure policy exists.

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

The rubric uses no preferred checks, which allows it match the gold labels on all 20 packages, but a more comprehensive rubric deployed in the real world would need some preferred checks. One important such check is professionalism, which is favorable to have but doesn't disqualify a repro if the fundamentals are there - it only serves to favor repros that are written in a professional voice than a casual one. This is something my rubric doesn't do, which is an acceptable at this incipient stage of my contribution journey.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
