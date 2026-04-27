# Contributing Guide

Thank you for your interest in contributing to this project. We welcome contributions of all kinds — bug reports, documentation improvements, new features, and dataset integrations.

## Getting Started

Before submitting a contribution, please take a moment to read through this guide to ensure a smooth review process.

1. **Fork** the repository and create your branch from `main`.
2. **Clone** your fork locally and install dependencies as described in the README.
3. Make your changes, then **test** them locally before submitting.

## Types of Contributions

**Bug Reports**
Open an issue using the Bug Report template. Include a clear description of the problem, steps to reproduce, and your environment details (OS, Python version, etc.).

**Feature Requests**
Open an issue using the Feature Request template. Describe the use case and why the feature would be valuable to other users.

**Pull Requests**
We accept pull requests for bug fixes, documentation updates, and new features. Please link your PR to the relevant issue if one exists.

## Pull Request Guidelines

- Keep changes focused. One PR should address one concern.
- Write clear commit messages in the imperative mood (e.g., `Add support for SMILES batch processing`).
- Update documentation and docstrings if your change affects the public API.
- Ensure all existing tests pass before submitting.

## Code Style

This project follows [PEP 8](https://pep8.org/) for Python code. We recommend using `black` for formatting and `ruff` for linting before committing.

```bash
pip install black ruff
black .
ruff check .
```

## Reporting Security Issues

Please do **not** open a public issue for security vulnerabilities. Instead, contact us directly at the email address listed in the repository profile.

## License

By contributing to this project, you agree that your contributions will be licensed under the same license as this repository.
