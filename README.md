# Guide

This repository contains code style guides and continuous integration workflows.

> It is a living document, and will be updated as we learn more about what works and what doesn't.

---

| **Table of Contents**             |
| --------------------------------- |
| [Go - style guide](style/go.md)   |
| [Lint - customized linter](#lint) |
| [Hooks - git hooks](#lint)        |
| [CI - reference ](#ci)            |
| [Build - script/makefile](#build) |
| [Badge](badge/README.md)         |

---

## Lint

| File                                | Description                             |
| ----------------------------------- | --------------------------------------- |
| [.golangci.yml](lint/.golangci.yml) | Linting configuration for golangci-lint |

## Hooks

git hooks for pre-commit.

| File                                 | Description                       |
| ------------------------------------ | --------------------------------- |
| [hooks/pre-commit](hooks/pre-commit) | Pre-commit hook for golangci-lint |

## CI

[ci](/ci/) directory contains the workflows for testing, linting, building and deploy the code.

| Workflow      | Description                       |
| ------------- | --------------------------------- |
| ci/github-lib | Build, lint and test (SonarCloud) |

Copy the workflow you want to use into your repository:

```sh
cp -a ci/github-lib/. <myrepo>/.github
```

> __SONAR_TOKEN__ is required in most workflows.  
> Token already exists in the our organization secrets.

SonarCloud not supported direct initialize a new repo.  
First init repo in SonarCloud after that go to the administation -> Analysis Method -> Disable automatic analysis. And just restart the failed workflow.

## Build

[build](/build/) directory contains the building scripts. Change project variables in build file.

| File                                             | Description                  |
| ------------------------------------------------ | ---------------------------- |
| [build/Makefile](build/Makefile)                 | Build script for Go projects |
| [build/.goreleaser.yaml](build/.goreleaser.yaml) | Goreleaser script            |
