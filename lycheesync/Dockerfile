ARG VERSION=latest
FROM linuxserver/lychee:$VERSION
LABEL maintainer="julien.vinet@gmail.com"

# installations
ENV LIBRARY_PATH=/lib:/usr/lib
RUN \
    echo "**** install packages ****" && \
    apk add --no-cache \
            build-base \
            git \
            python3-dev \
            jpeg-dev \
            zlib-dev \
            curl \
            jq && \ 
    echo "**** install pip ****" && \
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py | python3 && \
    echo "**** install lycheesync ****" && \
    mkdir -p /config/lycheesync/ && \
    git clone https://github.com/jnvinet/lycheesync.git && \
    cd lycheesync && \
    pip3 install -r requirements.txt && \
    echo "**** cleanup ****" && \
    rm -rf \
        /tmp/*

COPY /root/ /


# volumes
VOLUME /sources