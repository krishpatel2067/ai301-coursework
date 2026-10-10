# Test Evidence

Note: I replaced the path before the repo directory with `{system path}`.

## Repro Steps

### Input

```bash
python -c 'from rag.retriever.keyword_search import KeywordSearcher; searcher = KeywordSearcher(); searcher.index([])'
```

### Output

Before:

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

After:

```plaintext
2026-10-10 10:52:31 [warning  ] keyword_search_empty_chunks
```

## `make test-unit`

Before:

```plaintext
.venv/bin/pytest tests/unit -v -m unit
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-9.1.1, pluggy-1.6.0 -- {system path}/pathreview-ai301-fa26-s1/.venv/bin/python
cachedir: .pytest_cache
hypothesis profile 'default'
benchmark: 5.3.0 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
rootdir: {system path}/pathreview-ai301-fa26-s1
configfile: pyproject.toml
plugins: anyio-4.15.1, pytest_httpserver-1.1.5, hypothesis-6.168.1, benchmark-5.3.0, asyncio-1.4.0, cov-7.1.0
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 428 items

{...}
================= 375 passed, 53 xfailed, 4 warnings in 7.15s ==================
```

Note `{...}` has all the test details, removed for concision.

After:

```plaintext
.venv/bin/pytest tests/unit -v -m unit
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-9.1.1, pluggy-1.6.0 -- {system path}/pathreview-ai301-fa26-s1/.venv/bin/python
cachedir: .pytest_cache
hypothesis profile 'default'
benchmark: 5.3.0 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
rootdir: {system path}/pathreview-ai301-fa26-s1
configfile: pyproject.toml
plugins: anyio-4.15.1, pytest_httpserver-1.1.5, hypothesis-6.168.1, benchmark-5.3.0, asyncio-1.4.0, cov-7.1.0
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 428 items

{...}
================= 376 passed, 52 xfailed, 3 warnings in 6.39s ==================
```

## `make test-integration`

Before:

```plaintext
.venv/bin/pytest tests/integration -v -m integration
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-9.1.1, pluggy-1.6.0 -- {system path}/pathreview-ai301-fa26-s1/.venv/bin/python
cachedir: .pytest_cache
hypothesis profile 'default'
benchmark: 5.3.0 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
rootdir: {system path}/pathreview-ai301-fa26-s1
configfile: pyproject.toml
plugins: anyio-4.15.1, pytest_httpserver-1.1.5, hypothesis-6.168.1, benchmark-5.3.0, asyncio-1.4.0, cov-7.1.0
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 0 items

============================ no tests ran in 0.07s =============================
```

After:

```plaintext
.venv/bin/pytest tests/integration -v -m integration
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-9.1.1, pluggy-1.6.0 -- {system path}/pathreview-ai301-fa26-s1/.venv/bin/python
cachedir: .pytest_cache
hypothesis profile 'default'
benchmark: 5.3.0 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
rootdir: {system path}/pathreview-ai301-fa26-s1
configfile: pyproject.toml
plugins: anyio-4.15.1, pytest_httpserver-1.1.5, hypothesis-6.168.1, benchmark-5.3.0, asyncio-1.4.0, cov-7.1.0
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collecting ... collected 0 items

============================ no tests ran in 0.08s =============================
```

## `make lint`

Before:

```plaintext
.venv/bin/ruff check .
All checks passed!
```

After:

```plaintext
.venv/bin/ruff check .
All checks passed!
```

## `make typecheck`

Before:

```plaintext
.venv/bin/mypy api/ core/ ingestion/ rag/ agent/ safety/
.venv/lib/python3.12/site-packages/numpy/__init__.pyi:737: error: Type statement is only supported in Python 3.12 and greater  [syntax]
Found 1 error in 1 file (errors prevented further checking)
```

After:

```plaintext
.venv/bin/mypy api/ core/ ingestion/ rag/ agent/ safety/
.venv/lib/python3.12/site-packages/numpy/__init__.pyi:737: error: Type statement is only supported in Python 3.12 and greater  [syntax]
Found 1 error in 1 file (errors prevented further checking)
```
