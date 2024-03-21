# Fix base image version
#FROM python:3.7-alpine3.10 as builder
FROM python:3.13.0a5-alpine3.19 as builder

# Set tools versions to latest official release
ENV YQ_VERSION=v4.40.2

# Install required packages in a single layer
RUN apk add --no-cache \
        git \
        unzip \
        groff \
        build-base \
        libffi-dev \
        cmake \
        jq \
        curl \
        git \
        openssh \
        gnupg \
#       py3-pip \
    && pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir deepdiff tabulate gitpython

# Install yq
RUN curl -LO "https://github.com/mikefarah/yq/releases/download/${YQ_VERSION}/yq_linux_amd64" \
    && chmod o+x yq_linux_amd64 \
    && mkdir /usr/local/bin/yq \
    && mv yq_linux_amd64 /usr/local/bin/yq

# Create a non-root user
RUN adduser -D user1
USER user1

# Set the working directory
# WORKDIR /app
