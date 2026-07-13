# CI vs CD vs CD

CI is continuous integration, and CD stands for two related but distinct things: continuous delivery and continuous deployment. Continuous integration is about merging and verifying code changes often. Continuous delivery is about always having a build that is ready to release. Continuous deployment is about releasing every passing change automatically. They stack on top of each other, and most teams adopt them in that order.

## Continuous integration

Continuous integration means developers merge their work into a shared branch frequently, often several times a day, and each merge triggers an automated build and test run. The goal is to catch integration problems while they are small. When ten people each work for a week and merge at the end, conflicts and broken assumptions pile up. When everyone integrates small changes constantly and a machine checks each one, breakage is caught within minutes and traced to a single change. CI is the foundation the rest builds on.

## Continuous delivery

Continuous delivery extends CI so that every change which passes the pipeline results in a release-ready artifact. The software is always in a deployable state, but the actual push to production is triggered by a person clicking a button. This keeps a human decision point for timing (say, avoiding a Friday-evening release) while guaranteeing the build itself is already tested and packaged. Delivery removes the scramble of preparing a release; the release is prepared continuously.

## Continuous deployment

Continuous deployment removes even the button. Every change that passes every automated check goes to production with no human step. This demands real confidence in the test suite and in automated rollback, because nothing stands between a merge and live users except the pipeline. Many teams practice continuous delivery (ready on demand) without continuous deployment (automatic to production). The distinction matters: the two share the letters CD but describe different levels of automation and trust.
