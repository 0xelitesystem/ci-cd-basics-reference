# What to automate first

Automate your tests first, then your build, then your linting and formatting checks. Tests are the highest-value automation because they catch behavior regressions that would otherwise reach users. A build check confirms the code even assembles into something shippable. Lint and format checks catch style and simple mistakes cheaply. In that order, each layer you add makes the pipeline more useful without depending on the ones above it.

## Tests first

Automated tests are the reason CI provides confidence, so they come first. Running the test suite on every change means a broken feature is caught by a machine within minutes, not by a user next week. Start with the tests you already have, even a small suite, and run them on every push and every pull request. Unit tests (fast, isolated checks of individual functions) go early in the pipeline; slower integration and end-to-end tests come later. If you automate only one thing, automate running the tests.

## Build next

A build stage compiles or bundles the code into the form it actually ships in, and its value is proving that the change produces a working, deployable output. Code can pass unit tests yet fail to build because of a missing dependency, a type error, or a bad import. Automating the build catches those failures before they block a release. For interpreted languages with no compile step, the equivalent is installing dependencies cleanly and packaging the application, which still surfaces broken dependency and configuration problems early.

## Lint and format last

Linting checks code for likely bugs and questionable patterns, and formatting checks enforce a consistent style. These are cheap to run and worth automating, but they come last in priority because a lint warning rarely breaks production the way a failing test or build does. Automating them removes style debates from code review and catches a class of small errors (unused variables, undefined names) automatically. Because they run in seconds, place them early in the pipeline order even though they are lower in adoption priority: cheap checks first, high-value checks first to add.
