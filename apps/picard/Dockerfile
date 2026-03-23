FROM ghcr.io/linuxserver/baseimage-selkies:alpine323@sha256:90e6cc90973e951baa9a6f2739072e237e536288bf2fa50fa2a32581af66adb9

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
