FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:6db482f789f8093b9632398cf8671f8534f52ea4c9b2628587d9bbe35d1ab660

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
