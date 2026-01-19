## 📚 Development Workflow

### Installing Dependencies

```bash
# Install all dependencies (including dev dependencies)
uv sync

# Install without dev dependencies
uv sync --no-dev

# Add new dependencies
uv add requests pandas

# Add dev dependencies
uv add --dev pytest-mock
```

### Running Tasks

This project uses **nox** for task automation. All common development tasks are available as nox sessions:

```bash
# Format code with Ruff
uv run nox -s fmt

# Run linters (Ruff + ty)
uv run nox -s lint -- --ruff --ty

# Run only ty
uv run nox -s lint -- --ty

# Run only Ruff linter
uv run nox -s lint -- --ruff

# Run tests with coverage (75% minimum required)
uv run nox -s test

# Run tests with JUnit XML output (for CI)
uv run nox -s test -- --junitxml=results.xml
```

You can also run tools directly:

```bash
# Run pytest directly
uv run pytest

# Run specific test file
uv run pytest tests/tools/test__logger.py

# Format with Ruff
uv run ruff format .

# Lint with Ruff
uv run ruff check . --fix

# Type check with ty
uv run ty check
```

### Pre-commit Hooks

Pre-commit hooks automatically run code quality checks before each commit:

```bash
# Install hooks
uv run pre-commit install

# Run manually on all files
uv run pre-commit run --all-files
```

Configured hooks:
- Ruff formatting and linting
- JSON, YAML, TOML validation
- Trailing whitespace removal
- End-of-file fixer
- Private key detection
- Dockerfile linting with hadolint

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
