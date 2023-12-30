FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:d6777751843692ca3b0d302b0984efa33a9053d8a2b77ffea54c1b518743f6a3

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard
# renovate: datasource=repology depName=alpine_3_18/picard versioning=loose
ENV PICARD_VERSION="2.8.5-r2"

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
