# Artifacts, environments, and gates

An artifact is the concrete output a pipeline builds once and then reuses, an environment is a place that artifact runs (such as staging or production), and a gate is a condition that must be met before a change moves from one environment to the next. Together they let you build a change a single time, promote that exact build through increasingly production-like environments, and require checks or approvals at each step.

## Artifacts

An artifact is the packaged result of a build: a compiled binary, a container image, a zipped bundle, or an installable package. The key rule is build once, deploy many. You build the artifact a single time, then deploy that identical artifact to staging and later to production, rather than rebuilding at each step. Rebuilding risks producing a slightly different output (different dependency versions, different timestamps), so the thing you tested in staging might not be the thing that reaches production. A stored, versioned artifact guarantees you ship exactly what you verified.

## Environments

Environments are separate places to run the software, each closer to real. A typical progression is development (a throwaway place for testing changes), staging (a near-copy of production used for final verification), and production (where real users are). Promoting an artifact through these environments in order lets problems surface in a low-stakes place first. Each environment has its own configuration and data, but runs the same artifact, so differences in behavior point to configuration rather than to the code itself.

## Gates

A gate is a required condition between stages or environments. Automated gates include all tests passing, security scans finding no critical issues, or code coverage staying above a threshold. Manual gates include a human approval before deploying to production, common in continuous delivery. Gates are where you encode your risk tolerance: a low-stakes internal tool might gate only on tests, while a payment system might require passing tests, a security scan, and two human approvals before anything reaches production. Gates keep known-bad changes from advancing.
