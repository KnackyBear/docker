
FROM debian:sid-slim
LABEL maintainer="Julien Vinet <contact@julienvinet.dev>" app="devbox"

# Install basement tools
RUN apt-get update && apt-get install -y  \
    curl \
    tar \
    git \
    --no-install-recommends

# Install tools for developer (add yours here)
RUN apt-get install -y \
    nodejs \
    npm \
    grunt \
    python3-minimal \
    python3-pip \
    jq \
    --no-install-recommends

# Install and configure go
RUN curl -k https://dl.google.com/go/go1.12.9.linux-amd64.tar.gz -o go1.12.9.linux-amd64.tar.gz && \
    tar -C /usr/local -zxvf go1.12.9.linux-amd64.tar.gz && \
    mkdir -p $HOME/go && \
    rm -f go1.12.9.linux-amd64.tar.gz

ENV PATH=/usr/local/go/bin:$PATH

RUN mkdir -p /build/ && chmod -R 775 /build
WORKDIR /build/