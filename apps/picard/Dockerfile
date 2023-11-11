FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:d93d6cec2abb0a613b58b734e646e32aa4cf9d34d9144154540a7e9ab82c3600

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard
# renovate: datasource=repology depName=alpine_edge/picard versioning=loose
ENV PICARD_VERSION="2.10-r0"

RUN \
    echo "**** install packages ****" && \
    apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community \
    picard="${PICARD_VERSION}" && \
    echo "**** cleanup ****" && \
    rm -rf \
    /tmp/*

# add local files
COPY ./apps/picard/root /

# ports and volumes
EXPOSE 3000

VOLUME /config
