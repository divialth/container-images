FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:2935e56f9962140ec8099d7b659788ef6b90c3df0f992e5eeaa8ccc2a084cd40

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard
# renovate: datasource=repology depName=alpine_edge/picard versioning=loose
ENV PICARD_VERSION="2.9.2-r0"

RUN \
    echo "**** install packages ****" && \
    apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community \
    picard="${PICARD_VERSION}" && \
    echo "**** cleanup ****" && \
    rm -rf \
    /tmp/*

# add local files
COPY ./root /

# ports and volumes
EXPOSE 3000

VOLUME /config
