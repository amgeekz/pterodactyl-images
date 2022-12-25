FROM        node:19-bullseye-slim

LABEL       author="AmGeekz" maintainer="admin@amgeekz.site"
LABEL       org.opencontainers.image.source="https://github.com/amgeekz/pterodactyl-images"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         apt-get update \
            && apt-get -y install --no-install-recommends curl ffmpeg imagemagick iproute2 git sqlite3 python3 tzdata ca-certificates dnsutils build-essential libtool locales \
            && npm -g install npm@latest \
            && npm install nodemon
            && yarn install
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container container \
            && locale-gen en_US.UTF-8

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
