ARG VARIANT="jammy"

FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# Install OS packages
RUN apt update && export DEBIAN_FRONTEND=noninteractive \
    && apt -y install \
    wget \
    unzip \
    pip

USER vscode

RUN python3 -m pip install --user ansible ansible-lint
