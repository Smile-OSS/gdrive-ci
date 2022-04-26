FROM golang:alpine

LABEL maintainer "Serhii Boremchuk <sebor@smile.fr>"
LABEL version="v1.0.0"

USER root
ENV HOME '/root'

RUN apk add --update --no-cache \
  bash \
  binutils \
  ca-certificates \
  coreutils \
  curl \
  findutils \
  git \
  libuser \
  linux-headers \
  openssl \
  openssh \
  util-linux \
  zlib-dev \
  && rm -rf /var/cache/apk/*

# change default shell from ash to bash
RUN sed -i -e "s/bin\/ash/bin\/bash/" /etc/passwd

# Setup SSH client
RUN mkdir -p ${HOME}/.ssh
## Skip host key verification
RUN echo "Host *" >> ${HOME}/.ssh/config && \
    echo "    StrictHostKeyChecking no" >> ${HOME}/.ssh/config

# Set working directory
WORKDIR ${HOME}

RUN go install github.com/prasmussen/gdrive@2.1.1
