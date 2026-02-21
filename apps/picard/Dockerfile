FROM ghcr.io/linuxserver/baseimage-selkies:alpine323@sha256:cb32bacc652e66c0f6a0b727f986334110f717bcd4323a5b83a1228fc19dd104

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard
# renovate: datasource=repology depName=alpine_3_23/picard versioning=loose
ENV PICARD_VERSION="2.13.3_git20251006-r0"

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
