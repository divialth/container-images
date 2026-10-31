FROM ghcr.io/linuxserver/baseimage-alpine:3.23@sha256:36dfe19d24ed7fb4e9e380005f8187fe620f113162f960194a90594013c9fcfb

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# renovate: datasource=repology depName=alpine_3_23/dante-server versioning=loose
ENV DANTE_VERSION="1.4.4-r0"

RUN \
    echo "**** install packages ****" && \
    apk add --no-cache \
    dante-server="${DANTE_VERSION}" && \
    echo "**** cleanup ****" && \
    rm -rf \
    /tmp/*

# copy local files
COPY ./apps/dante-server/root /

# ports and volumes
EXPOSE 1080

VOLUME /config
