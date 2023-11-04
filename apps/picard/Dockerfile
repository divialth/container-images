FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:f05d7788cba77fa193ce7f10fa1580eb77371cd3be527e6381361af9ed9ae782

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
