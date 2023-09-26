FROM ghcr.io/linuxserver/baseimage-kasmvnc:alpine318@sha256:e83e2e637882fba9e59773a5e05259229e71e6186e1a65f117bc72b44219c416

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# title
ENV TITLE=Picard

RUN \
  echo "**** install packages ****" && \
  apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community \
    picard && \
  echo "**** cleanup ****" && \
  rm -rf \
    /tmp/*

# add local files
COPY ./root /

# ports and volumes
EXPOSE 3000

VOLUME /config
