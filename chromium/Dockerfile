# Run Chromium in a container
# Thanks to Jess Frazelle for her dockerfile !
# I have just add some stuff to work with wayland
#
#	docker run -d \
#		--net host \
#		-v /etc/localtime:/etc/localtime:ro \
#		-v /etc/passwd:/etc/passwd:ro \
#		-e "DISPLAY=unix${DISPLAY}" \
#		-v "${HOME}:${HOME}" \
#		-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
#		-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
#		-v /dev/shm:/dev/shm \
#   -v /etc/hosts:/etc/hosts \
#		--security-opt seccomp:/etc/docker/seccomp/chrome.json \
#		--device /dev/snd \
#		--device /dev/dri \
#		--device /dev/video0 \
#		-u $(id -u):$(id -g) \
#		--name chromium \
#		jnvinet/chromium
#
# seccomp profile can be downloaded on Jess github :
#   wget https://raw.githubusercontent.com/jfrazelle/dotfiles/master/etc/docker/seccomp/chrome.json -O ~/chrome.json
#
# WARNING !! To work, chromium need unprivileged namespace in kernel conf.
# You can enable it with systctl
#   sysctl kernel.unprivileged_userns_clone=1
#
# Or permanently with :
#   echo 'kernel.unprivileged_userns_clone=1' > /etc/sysctl.d/userns.conf
#

# Base docker image
FROM debian:sid-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

# Get list of versions at https://dl.google.com/widevine-cdm/versions.txt
ARG WIDEVINE_VERSION=4.10.1582.2

# Install Chromium
RUN apt-get update && apt-get install -y \
      chromium \
      chromium-l10n \
      fonts-liberation \
      fonts-roboto \
      hicolor-icon-theme \
      libexif-dev \
      libgl1-mesa-dri \
      libgl1-mesa-glx \
      libpulse0 \
      libpango1.0-0 \
      libv4l-0 \
      fonts-symbola \
      libcanberra-gtk-module \
      gnome-themes-standard \
      wget \
      unzip \
      --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* 

# Download latest version of libwindevine.co for Netflix compatibility (not working)
RUN mkdir -p /opt/google/chrome/WidevineCdm/ \
  && wget -q --no-check-certificate https://dl.google.com/widevine-cdm/${WIDEVINE_VERSION}-linux-x64.zip -O /opt/google/chrome/WidevineCdm/${WIDEVINE_VERSION}-linux-x64.zip \
  && unzip -qq /opt/google/chrome/WidevineCdm/${WIDEVINE_VERSION}-linux-x64.zip -d /opt/google/chrome/WidevineCdm/ \
  && chmod 644 /opt/google/chrome/WidevineCdm/libwidevinecdm.so \
  && ln -sf /opt/google/chrome/WidevineCdm/ /usr/lib/chromium/WidevineCdm \
  && rm -f /opt/google/chrome/WidevineCdm/${WIDEVINE_VERSION}-linux-x64.zip

# Asian fonts cuz I need it
RUN mkdir -p /usr/share/fonts/opentype/adobe-source-han-sans && \
	wget -q --no-check-certificate https://github.com/adobe-fonts/source-han-sans/releases/download/2.001R/SourceHanSans.ttc -O /usr/share/fonts/opentype/adobe-source-han-sans/SourceHanSans.ttc && \
	fc-cache -f -v

ENTRYPOINT [ "/usr/bin/chromium" ]