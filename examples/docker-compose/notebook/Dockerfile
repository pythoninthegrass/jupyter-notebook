# syntax=docker/dockerfile:1.7.0

FROM ghcr.io/pythoninthegrass/jupyter-notebook:latest

USER root

# Add permanent apt-get installs and other root commands here
# e.g., RUN apt-get install --yes --no-install-recommends npm nodejs

USER ${NB_UID}

# Switch back to jovyan to avoid accidental container runs as root
# Add permanent mamba/pip/conda installs, data files, other user libs here
# e.g., RUN pip install --no-cache-dir flake8
