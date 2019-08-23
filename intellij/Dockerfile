#
# docker run -d \
#		--net host \
#		-v /etc/localtime:/etc/localtime:ro \
#		-v /etc/passwd:/etc/passwd:ro \
#		-v "${HOME}:${HOME}" \
#		-e "DISPLAY=unix${DISPLAY}" \
#		-u $(id -u):$(id -g) \
#		--name intellij \
#		jnvinet/intellij "$@"
#

FROM openjdk:8
LABEL maintainer="Julien Vinet <contact@julienvinet.dev>" app="intellij"

ENV LANG C.UTF-8

# Base install
RUN apt-get update && apt-get install -y \
    libxtst6 \
    libgl1-mesa-dri \
    libgl1-mesa-glx \
    fonts-roboto \
    hicolor-icon-theme \
    libcanberra-gtk-module \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

# Install IntelliJ Community
RUN set -ex && \
	wget https://download-cf.jetbrains.com/idea/ideaIC-2019.1.1-no-jbr.tar.gz && \
	tar -xf ideaIC-2019.1.1-no-jbr.tar.gz && \
	rm ideaIC-2019.1.1-no-jbr.tar.gz

ENTRYPOINT ["/idea-IC-191.6707.61/bin/idea.sh"]