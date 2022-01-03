# Actions
A collection of reusable github actions for python

<br/>

## How to use
In your .github/workflows directory, create a yaml file (such as main.yaml). Add a job for each desired workflow with the `uses` keyword. Use the `with` keyword to pass any desired variables.

Example:

```
on: [push]

jobs:
  lint:
    uses: myome/actions/.github/workflows/pylint.yaml@main
    with:
      src: "src"
  black:
    uses: myome/actions/.github/workflows/black.yaml@main
    with:
      src: "src"
      py-version: "3.9"
```

<br/>

## Available workflows

### bandit: *code security checks*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** bandit flags (defaults to "-r")
  - **py-version:** version of python to use (defaults to "3.x")

### black: *code formatting*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** black flags
  - **py-version:** version of python to use (defaults to "3.x")

### flake8: *style guide enforcement*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** flake8 flags

### mypy: *static type checking*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** mypy flags (defaults to "-v")

### publish: *push packages to pypi*
&emsp;inputs:
  - **py-version:** version of python to use (defaults to "3.x")

### pylint: *static code analysis*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** pylint flags

### pytest: *test code runner*
&emsp;inputs:
  - **src:** source directory (defaults to ".")
  - **options:** pytest flags (defaults to "-v")

<br/>

## References
- https://docs.github.com/en/actions/learn-github-actions/reusing-workflows
- https://bandit.readthedocs.io/en/latest/
- https://black.readthedocs.io/en/stable/
- https://flake8.pycqa.org/en/latest/
- https://mypy.readthedocs.io/en/stable/
- https://pylint.org/
- https://docs.pytest.org/
