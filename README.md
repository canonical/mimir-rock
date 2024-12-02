# mimir-rock

[![Open a PR to OCI Factory](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-oci-factory.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-oci-factory.yaml)
[![Publish to GHCR:dev](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-dev.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-dev.yaml)
[![Update rock](https://github.com/canonical/mimir-rock/actions/workflows/rock-update.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-update.yaml)

[Rocks](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/) for [Mimir](https://grafana.com/oss/mimir/).  
This repository holds all the necessary files to build rocks for the upstream versions we support. The Mimir rock is used by the [mimir-k8s-operator](https://github.com/canonical/mimir-k8s-operator) charm.

The rocks on this repository are built with [OCI Factory](https://github.com/canonical/oci-factory/), which also takes care of periodically rebuilding the images.

New versions of the rock are tested using [`goss`](https://github.com/goss-org/goss) (for the actual validation) and [`noctua`](https://github.com/lucabello/noctua) (to run the actual command).

Automation takes care of:
* validating PRs, by simply trying to build the rock;
* pulling upstream releases, creating a PR with the necessary files to be manually reviewed;
* on PRs, validate the added (or modified) rocks by running them in a Kubernetes pod and testing them with `goss`;
* releasing to GHCR at [ghcr.io/canonical/mimir:dev](https://ghcr.io/canonical/mimir:dev), when merging to main, for development purposes.

