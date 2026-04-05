# Black

Black is an opinionated Python code formatter. It enforces a single, consistent style across all Python code it touches, eliminating debates over formatting and producing minimal diffs for cleaner code review. Black parses Python source into an AST, reformats it according to its rules, and writes the result back -- guaranteeing that the semantics of your code are preserved.

## Running Tests

### Setup

1. Clone the repository and `cd` into it.

2. Install Black with its development dependencies:

   ```sh
   pip install -e ".[d]"
   ```

   If editable mode fails, ensure the Hatchling build backend is installed first:

   ```sh
   pip install hatchling hatch-vcs hatch-fancy-pypi-readme
   pip install -e ".[d]"
   ```

   If editable mode still doesn't work, install normally instead:

   ```sh
   pip install ".[d]"
   ```

   Note that with a non-editable install, you'll need to re-run `pip install .` after any source changes for them to take effect.

3. Install test dependencies:

   ```sh
   pip install pytest
   ```

### Running the test suite

Run all tests:

```sh
python -m pytest tests/
```

Run a specific test file:

```sh
python -m pytest tests/test_format.py
```

Run tests matching a keyword:

```sh
python -m pytest tests/ -k "some_keyword"
```

Add `-x` to stop on the first failure, or `-v` for verbose output:

```sh
python -m pytest tests/ -x -v
```

### Debugging tests

If Black is installed in editable mode (`pip install -e`), you can debug without rebuilding after source changes.

Drop into pdb when a test fails:

```sh
python -m pytest tests/test_format.py -k "some_keyword" -x --pdb
```

Drop into pdb at the start of a test:

```sh
python -m pytest tests/test_format.py -k "some_keyword" -x --trace
```

You can also add `breakpoint()` anywhere in the Black source under `src/black/` and it will be hit when the test exercises that code path.

### Test data cases

Formatting test cases live in `tests/data/cases/`. Each file typically contains Python source that Black is expected to format. Some files include flags as comments on the first line (e.g. `# flags: --preview`) to control which Black options are used during the test.
