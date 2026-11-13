# CI/CD Basics

A plain-language reference on continuous integration and continuous delivery/deployment: the practice of automatically building, testing, and shipping code so that changes reach production safely and often. It covers what CI, CD (delivery), and CD (deployment) actually mean, how a pipeline is organized into stages, what to automate first, what artifacts are, and how environments and gates keep bad changes out.

## The core idea

CI/CD is the practice of automatically integrating, testing, and shipping code changes through a repeatable pipeline instead of doing those steps by hand. Continuous integration means every change is merged and verified against the whole codebase frequently, so problems surface early. Continuous delivery means the pipeline always produces a release-ready build that a person can deploy on demand, and continuous deployment goes one step further by pushing every passing change to production automatically. The point is to make releasing small, frequent, and boring instead of large, rare, and risky.

## What is inside

- [01-ci-vs-cd-vs-cd.md](01-ci-vs-cd-vs-cd.md) what integration, delivery, and deployment each mean and how they differ.
- [02-pipelines-and-stages.md](02-pipelines-and-stages.md) how a pipeline is built from ordered stages that fail fast.
- [03-what-to-automate-first.md](03-what-to-automate-first.md) tests, build, and lint, in the order worth adding them.
- [04-artifacts-environments-gates.md](04-artifacts-environments-gates.md) build outputs, promotion between environments, and approval gates.
- [05-example-pipeline-outline.md](05-example-pipeline-outline.md) a concrete stage-by-stage pipeline you can adapt.

## The stance

This reference treats CI/CD as a discipline for shrinking the cost and risk of change, not a specific tool. Start with automated tests on every commit, add build and lint, then grow toward automated delivery only when the safety checks are trustworthy. Automate the boring, repeatable parts so humans decide only what genuinely needs judgment.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright RBL Industries LLC 2026.
