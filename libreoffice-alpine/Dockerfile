FROM alpine:3.9

LABEL maintainer="amir.mohtasebi@gmail.com"

RUN set -ex \
    && addgroup --system --gid 500 libreoffice \
    && adduser -S libreoffice -G libreoffice --uid 500

ENV GOSU_VERSION 1.10

RUN set -x \
    && apk --update add ca-certificates wget gnupg && rm -rf /var/cache/apk/ \
    && wget -O /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64" \
    && wget -O /usr/local/bin/gosu.asc "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64.asc" \
    && export GNUPGHOME="$(mktemp -d)" \
    && gpg --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
    && gpg --batch --verify /usr/local/bin/gosu.asc /usr/local/bin/gosu \
    && rm -r "$GNUPGHOME" /usr/local/bin/gosu.asc \
    && chmod +x /usr/local/bin/gosu \
    && gosu nobody true \
    && apk del ca-certificates wget

RUN set -x \
    && apk add --no-cache --purge -uU \
       libreoffice libreoffice-base libreoffice-lang-uk \
       ttf-freefont ttf-opensans ttf-ubuntu-font-family ttf-inconsolata \
       ttf-liberation ttf-dejavu \
       libstdc++ openjdk8-jre xvfb
