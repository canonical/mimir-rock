# mimir-rock

[![Open a PR to OCI Factory](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-oci-factory.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-oci-factory.yaml)
[![Publish to GHCR:dev](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-dev.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-release-dev.yaml)
[![Update rock](https://github.com/canonical/mimir-rock/actions/workflows/rock-update.yaml/badge.svg)](https://github.com/canonical/mimir-rock/actions/workflows/rock-update.yaml)

[Rocks](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/) for [Mimir](https://grafana.com/oss/mimir/).  
This repository holds all the necessary files to build rocks for the upstream versions we support. The Mimir rock is used by the [mimir-k8s-operator](https://github.com/canonical/mimir-k8s-operator) charm.

The rocks on this repository are built with [OCI Factory](https://github.com/canonical/oci-factory/), which also takes care of periodically rebuilding the images.

**How do I interact with this repo?** This repo uses [`just`](https://github.com/casey/just) to easily run some commands:
```
∮ just
Available recipes:
    clean version               # `rockcraft clean` for a specific version
    pack version                # Pack a rock of a specific version
    run version=latest_version  # Run a rock and open a shell into it with `kgoss`
    test version=latest_version # Test the rock with `kgoss`
```

Automation takes care of:
* validating PRs, by simply trying to build the rock;
* pulling upstream releases, creating a PR with the necessary files to be manually reviewed;
* on PRs, validate the added (or modified) rocks by running `kgoss`;
* releasing to GHCR at [ghcr.io/canonical/mimir:dev](https://ghcr.io/canonical/mimir:dev), when merging to main, for development purposes.

