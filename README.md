# jupyter-notebook

Jupyter Docker Stacks are a set of ready-to-run [Docker images](https://quay.io/organization/jupyter) containing Jupyter applications and interactive computing tools.
You can use a stack image to do any of the following (and more):

- Start a personal Jupyter Server with the JupyterLab frontend (default)
- Run JupyterLab for a team using JupyterHub
- Start a personal Jupyter Server with the Jupyter Notebook frontend in a local Docker container
- Write your own project Dockerfile

## Quick Start

You can [try a relatively recent build of the quay.io/jupyter/base-notebook image on mybinder.org](https://mybinder.org/v2/gh/jupyter/docker-stacks/main?urlpath=lab/tree/README.ipynb).
Otherwise, the examples below may help you get started if you [have Docker installed](https://docs.docker.com/get-started/get-docker/),
know [which Docker image](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html) you want to use, and want to launch a single Jupyter Application in a container.

The [User Guide on ReadTheDocs](https://jupyter-docker-stacks.readthedocs.io/en/latest/) describes additional uses and features in detail.

```{note}
Since `2023-10-20` our images are only pushed to `Quay.io` registry.
Older images are available on Docker Hub, but they will no longer be updated.
```

### Example

This command pulls the `jupyter/scipy-notebook` image tagged `2024-11-19` from Quay.io if it is not already present on the local host.
It then starts a container running a Jupyter Server with the JupyterLab frontend and exposes the container's internal port `8888` to port `10000` of the host machine:

```bash
docker run -p 10000:8888 quay.io/jupyter/scipy-notebook:2024-11-19
```

You can modify the port on which the container's port is exposed by [changing the value of the `-p` option](https://docs.docker.com/engine/containers/run/#exposed-ports) to `-p 8888:8888`.

Visiting `http://<hostname>:10000/?token=<token>` in a browser loads JupyterLab,
where:

- The `hostname` is the name of the computer running Docker
- The `token` is the secret token printed in the console.

The container remains intact for restart after the Server exits.

## Resources

- [Documentation on ReadTheDocs](https://jupyter-docker-stacks.readthedocs.io/en/latest/)
- [Issue Tracker on GitHub](https://github.com/jupyter/docker-stacks/issues)
- [Jupyter Discourse Forum](https://discourse.jupyter.org/)
- [Jupyter Website](https://jupyter.org)
- [Images on Quay.io](https://quay.io/organization/jupyter)
