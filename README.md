# Black

Black is an opinionated Python code formatter. It enforces a single, consistent style across all Python code it touches, eliminating debates over formatting and producing minimal diffs for cleaner code review. Black parses Python source into an AST, reformats it according to its rules, and writes the result back -- guaranteeing that the semantics of your code are preserved.

## Running Tests

### Setup

1. Clone the repository and `cd` into it.

2. Install Black in editable mode with its development dependencies:

   ```sh
   pip install -e ".[d]"
   ```

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

### Test data cases

Formatting test cases live in `tests/data/cases/`. Each file typically contains Python source that Black is expected to format. Some files include flags as comments on the first line (e.g. `# flags: --preview`) to control which Black options are used during the test.
