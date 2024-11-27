# syntax=docker/dockerfile:1.7.0

ARG REGISTRY=quay.io
ARG OWNER=jupyter
ARG PYTHON_VERSION=3.11.10
ARG TAG=python-${PYTHON_VERSION}
ARG BASE_IMAGE=${REGISTRY}/${OWNER}/docker-stacks-foundation:${TAG}

FROM $BASE_IMAGE

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        fonts-liberation \
        pandoc \
        run-one \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER ${NB_UID}

WORKDIR /tmp

ARG NOTEBOOK_VERSION=7.2.2

RUN <<EOF
#!/bin/bash
mamba install --yes \
    jupyterlab \
    notebook>=${NOTEBOOK_VERSION}
jupyter server --generate-config
mamba clean --all -f -y
jupyter lab clean
rm -rf "/home/${NB_USER}/.cache/yarn"
fix-permissions "${CONDA_DIR}"
fix-permissions "/home/${NB_USER}"
EOF

ENV JUPYTER_PORT=8888
EXPOSE $JUPYTER_PORT

COPY start-notebook.py start-notebook.sh start-singleuser.py start-singleuser.sh /usr/local/bin/
COPY jupyter_server_config.py docker_healthcheck.py /etc/jupyter/

USER root

RUN fix-permissions /etc/jupyter/

USER ${NB_UID}

WORKDIR "${HOME}"

CMD ["start-notebook.py"]
