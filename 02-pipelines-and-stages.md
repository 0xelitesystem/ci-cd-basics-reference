# Pipelines and stages

A pipeline is an ordered sequence of automated stages that a code change passes through, where each stage must succeed before the next begins. It turns the informal steps of building and shipping into an explicit, repeatable flow. Stages are ordered so the fastest, cheapest checks run first and the slowest, most expensive run last, which is the principle called fail fast.

## What a stage is

A stage is one logical step in the pipeline, such as installing dependencies, running unit tests, building the application, or deploying to a staging environment. Each stage has a clear pass or fail result. If a stage fails, the pipeline stops and reports which stage broke and why, so a developer knows exactly where to look. Stages can contain multiple parallel jobs (for example, running tests on several versions of a language at once) that all must pass for the stage to pass.

## Fail fast ordering

Stages are deliberately ordered cheapest-and-fastest first. A lint check that takes five seconds runs before a unit test suite that takes two minutes, which runs before an integration test suite that takes ten minutes, which runs before a deploy. This way a change with an obvious formatting error fails in seconds rather than wasting twenty minutes of compute only to fail at the end. Fast feedback keeps developers in flow and keeps the pipeline cheap to run.

## Triggers and status

Pipelines are triggered by events: a push to a branch, a pull request being opened, a merge to the main branch, or a scheduled time. The pipeline reports a status back to the code host, usually a green check or a red X next to the commit or pull request. A common rule is that a pull request cannot be merged unless its pipeline is green. This makes the pipeline the enforced gate through which all changes must pass, rather than a suggestion developers can skip.
