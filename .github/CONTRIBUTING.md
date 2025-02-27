# Contributing to poethepoet

So you'd like to contribute? Awesome! Here are some things worth knowing.

## Reporting a bug / requesting a feature / asking a question

Go [open an issue](https://github.com/nat-n/poethepoet/issues) and I'll probably reply soon.

## Contributing code

### Preface

If you're willing to contribute your ideas and effort to making poethepoet better, then that's awesome and I'm grateful. I don't have all the answers to it's particularly important for this project to benefit from diverse perspective and technical expertise.

However please be aware that a lot of thought has gone into the architecture of poethepoet, and whilst I know it's not perfect, and I am very interested in alternative perspectives, I do have strong (and I hope reasonable) opinions about how certain things should. This particularly applies to naming and internal APIs. There is a lot to consider in terms of making sure the tool stays simple, flexible, and performant. So please don't be offended if there is some push back.

### Development process

1. If your planned changes entail non-trivial UI or internal API changes then it's a good idea to bring them up for discussion as a GitHub issue first.

2. Fork and clone the repo, and create a feature or bugfix branch off of the _development_ branch.

3. Double check that you're starting from the _development_ branch, and not from the the _main_ branch.

4. Run `poetry install` to setup your development environment. ([install poetry](https://python-poetry.org/docs/#installation))

5. Do your code

6. If you've added a feature then before it can be including in a release we will need:
  a. a feature test along the same lines as the examples in the tests dir,
  b. documentation in the form of a readme section.

5. Run `poe check` to check that you haven't broken anything that will block the CI pipeline.

6. Create a commit with a clear commit message that describes the commit contents. If you like to commit often, consider squashing your commits before continuing.

7. Open a PR on GitHub.

### Pull requests

There isn't currently a pull request template, but please try and be descriptive about what problem you're solving and how, and reference related issues.

In some cases it might be acceptable to merge code to _development_ to make a pre-release from it without including full automated tests and documentation. However this is a special case, because it blocks further releases from the _development_ branch until the tests an docs are there.

### Branching model

This project implements something like git flow.

_TL;DR_ branch off of _development_ for new features, or _main_ for minor bug fixes or doc improvements.

We like to keep a clean history, so squash-rebase merges are preferred for the _development_ or _main_ branches.

### Overview of branches

#### Historic branches

- **main** the primary branch containing released code and up to date docs.
- **development** in progress and pre-released features that are expected to be included in a release when ready.


#### Working branches

- **hotfix/<description>** branches for minor/urgent bug fixes from main
- **feature/<description>** branches for new feature development from development
- **bugfix/<description>** for new bug fixes from development
- **doc/<description>** branches for documentation changes

### How to add a new feature

1. Create your branch from _development_
  ```
  git fetch
  git checkout origin/development
  git checkout -b feature/my_new_feature
  ```
2. Create a pull request back to _development_

### How to add a hot fix

1. Create your branch from _main_
  ```
  git fetch
  git checkout origin/main
  git checkout -b feature/my_new_feature
  ```
2. Create a pull request back to _main_, and one to _development_

### How to create pre-release

1. From the head of the _development_ branch, create release commit that bumps the version in `pyproject.toml` and `__version__.py` (there's a test to ensure these are in sync).
2. Create a release (and tag) on GitHub, following the existing convention for naming and release notes format, and the GitHub CI will do the rest.

### How to create release

1. Create a branch off of _development_ like **release/1.0.0** and add a commit to bump the version in `pyproject.toml` and `__version__.py`.
2. Merge it into both _main_ and _release_
3. Create a GitHub release from the head of main, following the existing convention for naming and release notes format, and the GitHub CI will do the rest.
