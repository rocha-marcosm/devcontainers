ARG VARIANT="jammy"

FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# Install OS packages
RUN apt update && export DEBIAN_FRONTEND=noninteractive \
    && apt -y install \
    wget \
    unzip \
    # terraform \
    # direnv \
    && rm -rf /var/lib/apt/lists/*

ARG TERRAFORM_VERSION="1.5.5"
ARG TERRAGRUNT_VERSION="0.55.13"
ARG TERRAFORM_DOCS_VERSION="0.17.0"
#Terraform
RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -P /tmp/ \
    && unzip /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /usr/local/bin/ \
    && rm -f /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
# Terragrunt
RUN wget https://github.com/gruntwork-io/terragrunt/releases/download/v${TERRAGRUNT_VERSION}/terragrunt_linux_amd64 -P /tmp/ \
    && mv /tmp/terragrunt_linux_amd64 /usr/local/bin/terragrunt \
    && chmod +x /usr/local/bin/terragrunt
# Terraform-docs
RUN wget https://terraform-docs.io/dl/v${TERRAFORM_DOCS_VERSION}/terraform-docs-v${TERRAFORM_DOCS_VERSION}-$(uname)-amd64.tar.gz -P /tmp/ \
    && tar -xvf /tmp/terraform-docs-v${TERRAFORM_DOCS_VERSION}-$(uname)-amd64.tar.gz -C /usr/local/bin/ \
    && chmod +x /usr/local/bin/terraform-docs \
    && rm -f /tmp/terraform-docs-v${TERRAFORM_DOCS_VERSION}-$(uname)-amd64.tar.gz