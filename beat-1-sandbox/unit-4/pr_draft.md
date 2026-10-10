# fix: keyword search issues a warning on empty index instead of unhandled `ZeroDivisionError`

## Summary

<!-- One paragraph describing what this PR does and why -->

Before, calling `KeywordSearcher.index()` with parameter `chunks` led to an unhandled `ZeroDivisionError` emitted from the `rank-bm25` library. This PR guards against an empty corpus ever reaching the `rank-bm25` library, preventing the exception. Logs a warning, matching search()'s existing empty-index handling.

## Issue

Closes #68

## Changes

<!-- Bullet list of the specific changes made -->

- Added an empty-index guard to `KeywordSearcher.index()` after the existing `self.chunks = chunks` line. When triggered, it logs a warning and returns early.
- Updated `KeywordSearcher.index()` docstring to reflect this change.
- Removed the `@pytest.mark.xfail` marker above `test_empty_index`, as required.

## Testing

<!-- How did you verify your changes? -->

Reran the repro steps after my change.

Input:

```bash
python -c 'from rag.retriever.keyword_search import KeywordSearcher; searcher = KeywordSearcher(); searcher.index([])'
```

Output before:

```plaintext
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "{system path}/pathreview-ai301-fa26-s1/rag/retriever/keyword_search.py", line 25, in index
    self.bm25 = BM25Okapi(tokenized_corpus)
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 83, in __init__
    super().__init__(corpus, tokenizer)
  File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 27, in __init__
    nd = self._initialize(corpus)
         ^^^^^^^^^^^^^^^^^^^^^^^^
  File "{system path}/pathreview-ai301-fa26-s1/.venv/lib/python3.12/site-packages/rank_bm25.py", line 52, in _initialize
    self.avgdl = num_doc / self.corpus_size
                 ~~~~~~~~^~~~~~~~~~~~~~~~~~
ZeroDivisionError: division by zero
```

_Note: I replaced the path before the repo directory with `{system path}`._

Output after:

```plaintext
2026-10-10 10:52:31 [warning  ] keyword_search_empty_chunks
```

- [ ] **CI is green on this PR (all five jobs)** — required for review
- [x] Unit tests pass (`make test-unit`)
- [x] Integration tests pass (`make test-integration`)
- [x] Linter passes (`make lint`)
- [ ] Type checker passes (`make typecheck`)
- [ ] New/updated tests cover the changes
- [x] If this fixes a seeded bug: removed its `@pytest.mark.xfail` marker (and any
      matching suppression in `pyproject.toml`)

Note:

- Type checker errored for me before and after making the change. I checked off that box since my change didn't introduce any new type-checking errors.
- My fix didn't require any new or updated tests - it simply required removing the `xfail` marker.

## Screenshots / Demo

<!-- If applicable, add screenshots or a link to a demo video -->

**N/A**

The original issue and my change involved the business logic layer, which can be easily tested in the terminal (see Testing above) without an end-to-end UI test.

## Notes for Reviewers

<!-- Anything the reviewer should pay particular attention to -->

- I did not use AI for this change since I was able to locate the bug and knew the implementation specifics on my own.
- One thing that wasn't in the plan but is in this PR is that I updated the `KeywordSearch.index()` docstring. Oversight in my plan; but the change was worth it.

---

## Commits (not to post)

```plaintext
2617713 (HEAD -> fix/68-zero-division-error, origin/fix/68-zero-division-error) test(rag): remove xfail marker for test_empty_index as per issue requirement
2dc721b fix(rag): add a guard to return with warning if chunks list is empty in index()
```

## Diff (not to post)

```diff
diff --git a/rag/retriever/keyword_search.py b/rag/retriever/keyword_search.py
index bad161f..9501fc9 100644
--- a/rag/retriever/keyword_search.py
+++ b/rag/retriever/keyword_search.py
@@ -15,12 +15,18 @@ class KeywordSearcher:
         self.chunks = []

     def index(self, chunks: list[dict]) -> None:
-        """Build BM25 index from chunks.
+        """Build BM25 index from chunks. Returns early without building
+        the index if chunks list is empty.

         Args:
             chunks: List of chunk dicts with 'text' field
         """
         self.chunks = chunks
+
+        if not chunks:
+            logger.warning("keyword_search_empty_chunks")
+            return
+
         tokenized_corpus = [self._tokenize(chunk["text"]) for chunk in chunks]
         self.bm25 = BM25Okapi(tokenized_corpus)
         logger.info("keyword_index_built", chunk_count=len(chunks))
diff --git a/tests/unit/test_keyword_search.py b/tests/unit/test_keyword_search.py
index 6d2d326..a43047f 100644
--- a/tests/unit/test_keyword_search.py
+++ b/tests/unit/test_keyword_search.py
@@ -131,10 +131,6 @@ class TestKeywordSearcher:
         assert result["source"] == "readme"
         assert result["custom"] == "value"

-    @pytest.mark.xfail(
-        strict=True,
-        reason="issue #68 (manifest H-01): BM25 keyword search raises ZeroDivisionError on an empty index",
-    )
     def test_empty_index(self, searcher):
         """Test searching on empty index."""
         searcher.index([])
```
