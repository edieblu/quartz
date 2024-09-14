---
tags:
  - ✅
published: true
sr-due: 2025-08-15
sr-interval: 484
sr-ease: 250
---
⬅️ [[Missing Semester 08]]

## Continuous integration (CI)

Continuous integration, or CI, is an umbrella term for “stuff that runs whenever your code changes” - a.k.a. event-triggered actions. E.g CIs: Travis CI, Azure Pipelines, and GitHub Actions.

They all work in roughly the same way: you add a file to your repository that describes what should happen when various things happen to that repository (e.g. re-run the tests when there are code changes.

Dependabot: checks whether your dependencies are up-to-date and submits an automatic PR if they're not.

The badges in GitHub come from the CI as well: e.g test coverage, dependencies, documentaton versioning.

GitHub pages is a type of a CI action - it builds a blog from your markdown files (using Jeykll).