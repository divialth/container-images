FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine321@sha256:ba920e148c4e5a56c4be83bb7cd27e4767b958293db9a3805d433d3b6862bb9c

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard
# renovate: datasource=repology depName=alpine_3_21/picard versioning=loose
ENV PICARD_VERSION="2.12.3-r0"

RUN \
    echo "**** install packages ****" && \
    apk add --no-cache \
    picard="${PICARD_VERSION}" && \
    echo "**** cleanup ****" && \
    rm -rf \
    /tmp/*

# add local files
COPY ./apps/picard/root /

# ports and volumes
EXPOSE 3000

VOLUME /config
