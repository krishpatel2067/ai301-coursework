# Plan

<!-- Replace this file with your unit-3 plan: the same `plan.md` your
plan-check run graded.

Keep the deviations heading below, and fill it before you submit. It is
graded on being answered, not on there being deviations to report. -->

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

## Deviations

<!-- [What changed between the plan you posted and the change you built, and
why. If nothing changed, say so in your own words - "nothing changed;
the plan held" earns these points in full. Leaving this blank does not.] -->

The only thing that changed from the plan I posted and the change I built is documentation. I opted to change the `KeywordSearcher.index` to mention that no index is built if the provided `chunks` list is empty. It was necessary to ensure documentation was up to date with the change. I should have mentioned it in my plan for consistency and trust purposes.
