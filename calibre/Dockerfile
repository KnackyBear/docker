FROM debian:sid
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

RUN apt-get update && apt-get install -y \
	--no-install-recommends \
	curl \
	xdg-utils \
	xz-utils \
	libcanberra-gtk-module \
	gnome-themes-standard \
	python3 \
	python-pyqt5 \
	libnss3

RUN curl -k https://download.calibre-ebook.com/4.9.1/calibre-4.9.1-x86_64.txz --output calibre.txz

RUN mkdir -p /opt/calibre && \
	rm -rf /opt/calibre/* && \
	tar xvf calibre.txz -C /opt/calibre && \
	/opt/calibre/calibre_postinstall

ENTRYPOINT [ "calibre" ]