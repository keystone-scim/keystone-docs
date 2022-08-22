# Getting Started

## Pull the Container Image

The *Keystone* image is hosted on GHCR (GitHub Container Registry). To pull
its latest version locally, run the following `docker` command:

```shell
docker pull ghcr.io/keystone-scim/keystone:latest
```

For a full image versions list, refer to the
[package information on GitHub](https://github.com/keystone-scim/keystone/pkgs/container/keystone).


## Where to Run Keystone

You can run *Keystone* in pretty much any container runtime environment.  *Keystone*
is entirely stateless, so you can deploy anywhere from a single Docker container
to replicated Kubernetes Deployment (see [Kubernetes example](https://github.com/keystone-scim/keystone/tree/main/deploy/kubernetes)
in *Keystone*'s GitHub repo).

Ready to run it?  Head over to the [Configuration Guide](./configuration.md).