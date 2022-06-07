# Actions
A collection of reusable github actions for facilitating CI/CD at MyOme.

[How to use](#how-to-use)  
[Docker workflows](#docker)  
[Python workflows](#python)

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

## Docker  

### build-and-push-to-shr-ecr:  

&emsp;**Inputs**   
&emsp;`dockerfile`: dockerfile to build (defaults to "Dockerfile")  
&emsp;`build_context`: build context for docker build command (defaults to ".")

&emsp;**Secrets**   
&emsp;`aws-access-key-id`: SHR_ECR_CI_ACCESS_KEY_ID as stored in secrets manager  
&emsp;`aws-secret-access-key`: SHR_ECR_CI_SECRET_ACCESS_KEY as stored in secrets manager  

## Nextflow  

### nextflow-smoke-test:  

&emsp;**Inputs**  
&emsp;`config`: Workflow config file (defaults to "workflow/nextflow_smoke_test.config")  
&emsp;`entry`: Entry point for specific workflow (defaults to "command_line")  

&emsp;**Secrets**   
&emsp;`aws-access-key-id`: SHR_S3_FLOWS_CI_ACCESS_KEY_ID as stored in secrets manager  
&emsp;`aws-secret-access-key`: SHR_S3_FLOWS_CI_SECRET_ACCESS_KEY as stored in secrets manager  

### tag-and-ship-nf-workflow:  

&emsp;**Inputs**  
&emsp;`bucket`: AWS s3 bucket to ship workflow to (defaults to "myome-shr-flows")  
&emsp;`region`: AWS region where target bucket exists (defaults to "us-east-2")  

&emsp;**Secrets**   
&emsp;`aws-access-key-id`: SHR_S3_FLOWS_CI_ACCESS_KEY_ID as stored in secrets manager  
&emsp;`aws-secret-access-key`: SHR_S3_FLOWS_CI_SECRET_ACCESS_KEY as stored in secrets manager  

## Python  
### bandit: *code security checks*
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: bandit flags (defaults to "-r")  
&emsp;`py-version`: version of python to use (defaults to "3.x")  

### black: *code formatting*
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: black flags  
&emsp;`py-version`: version of python to use (defaults to "3.x")  

### flake8: *style guide enforcement*  
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: flake8 flags  

### mypy: *static type checking*
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: mypy flags (defaults to "-v")  

### publish: *upload packages to Myome SHR pypi*
&emsp;**Inputs**   
&emsp;`py-version`: version of python to use (defaults to "3.x")  

&emsp;**Secrets**   
&emsp;`pypi-pw`: SHR_PYPI_CICD_UPLOAD_PWD stored as Github secret  

### pylint: *static code analysis*
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: pylint flags  

### pytest: *test code runner*
&emsp;**Inputs**  
&emsp;`src`: source directory (defaults to ".")  
&emsp;`options`: pytest flags (defaults to "-v")  

<br/>

## References
- https://docs.github.com/en/actions/learn-github-actions/reusing-workflows
- https://bandit.readthedocs.io/en/latest/
- https://black.readthedocs.io/en/stable/
- https://flake8.pycqa.org/en/latest/
- https://mypy.readthedocs.io/en/stable/
- https://pylint.org/
- https://docs.pytest.org/
