# Example pipeline outline

Here is a concrete pipeline outline you can adapt to most projects. It runs on every pull request and on every merge to the main branch, ordered so the cheapest checks fail fast and deployment happens only after everything upstream is green. Read it top to bottom: each stage must pass before the next runs.

## The stages

```
Trigger: push to a pull request, or merge to main

Stage 1  Setup
  - check out the code
  - install dependencies (from a lockfile, for reproducibility)
  - restore cached dependencies if unchanged

Stage 2  Lint and format   (seconds)
  - run the linter
  - check code formatting
  - fail the pipeline on any violation

Stage 3  Unit tests         (seconds to a minute)
  - run the fast, isolated test suite
  - report pass/fail back to the pull request

Stage 4  Build              (a minute or two)
  - compile or bundle the application
  - produce a versioned artifact (for example, a container image tagged with the commit)
  - store the artifact in a registry

Stage 5  Integration tests  (several minutes)
  - start the app from the built artifact
  - run tests that hit real dependencies (database, API)

Stage 6  Deploy to staging  (only on merge to main)
  - deploy the stored artifact to the staging environment
  - run smoke tests against staging

Gate     Manual approval    (continuous delivery)
  - a person reviews staging and approves the production release
  - omit this gate for continuous deployment

Stage 7  Deploy to production
  - deploy the same artifact to production
  - run smoke tests; roll back automatically if they fail
```

## How to read it

Notice three things. First, the ordering is fail fast: lint and unit tests (seconds) run before the build and integration tests (minutes), so cheap mistakes stop the pipeline early. Second, the artifact built in Stage 4 is the exact one deployed in Stages 6 and 7; nothing is rebuilt. Third, the manual approval gate before production is what makes this continuous delivery. Remove that gate and it becomes continuous deployment. Start smaller than this (Stages 1 through 4 alone are a solid beginning) and add stages as your confidence and test coverage grow.
