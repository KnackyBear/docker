#
#	docker run --rm -it \
#		-v /etc/hosts:/etc/hosts \
#		--name hostess \
#		jnvinet/hostess "$@"
#
# Credits : https://github.com/cbednarski/hostess

FROM debian:sid-slim
LABEL maintainer="Julien Vinet <contact@julienvinet.dev>" app="hostess"

# Install basement tools
RUN apt-get update && apt-get install -y  \
    curl \
    tar \
    git \
    --no-install-recommends

# Install and configure go
RUN curl -k https://dl.google.com/go/go1.12.9.linux-amd64.tar.gz -o go1.12.9.linux-amd64.tar.gz && \
    tar -C /usr/local -zxvf go1.12.9.linux-amd64.tar.gz && \
    mkdir -p $HOME/go

ENV PATH=/usr/local/go/bin:$PATH

# Install hostess
RUN git config --global http.sslVerify false && \
    go get github.com/cbednarski/hostess/cmd/hostess && \
    mv $HOME/go/bin/hostess /usr/bin

# Cleanup
RUN rm -rf /usr/local/go && \
    rm -rf $HOME/go && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["hostess"]