FROM debian:bookworm-slim AS base

RUN apt-get update \
  && apt-get install -y \
  ca-certificates \
  git \
  zip \
  unzip \
  curl \
  wget \
  host \
  jq \
  make \
  sudo \
  moreutils \
  gnupg2 \
  openssh-client \
  && rm -rf /var/cache/apt/archives

FROM base AS ko

ARG KO_VERSION=0.15.2
ARG KO_OS=Linux
ARG KO_ARCH=x86_64

RUN curl -sSfL "https://github.com/ko-build/ko/releases/download/v${KO_VERSION}/ko_${KO_VERSION}_${KO_OS}_${KO_ARCH}.tar.gz" > ko.tar.gz \
  && tar -xzvf ko.tar.gz \
  && mv ko /usr/local/bin/ko \
  && rm ko.tar.gz

FROM base AS kubectl

ARG KUBECTL_VERSION=1.29.3

RUN curl -LO "https://dl.k8s.io/release/v${KUBECTL_VERSION}/bin/linux/amd64/kubectl" \
  && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
  && rm kubectl

FROM base AS helm

ARG HELM_VERSION=3.14.3

RUN curl -sSfL "https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz" > helm.tar.gz \
  && tar -xzvf helm.tar.gz \
  && mv linux-amd64/helm /usr/local/bin/helm \
  && rm -rf linux-amd64 helm.tar.gz

FROM base AS docker

ARG DOCKER_VERSION=24.0.6

RUN curl -fsSL https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKER_VERSION}.tgz -o docker.tar.gz \
  && tar -xzvf docker.tar.gz \
  && mv docker/docker /usr/local/bin \
  && rm -r docker docker.tar.gz

FROM base AS terraform

ARG TERRAFORM_VERSION=1.7.5

RUN curl -fsSL https://releases.hashicorp.com/terraform/$TERRAFORM_VERSION/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform.zip \
  && unzip terraform.zip \
  && mv terraform /usr/local/bin \
  && rm -r terraform.zip

FROM base AS final

COPY --from=ko /usr/local/bin/ko /usr/local/bin
COPY --from=docker /usr/local/bin/docker /usr/local/bin
COPY --from=kubectl /usr/local/bin/kubectl /usr/local/bin
COPY --from=helm /usr/local/bin/helm /usr/local/bin
COPY --from=terraform /usr/local/bin/terraform /usr/local/bin
