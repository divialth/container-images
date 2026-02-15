FROM ghcr.io/linuxserver/baseimage-alpine:3.23@sha256:c6aaa0e75c5656898d476586736748c18c57ea2443a586e566601e289b74c7ed

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build.version="Version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="divialth"

# renovate: datasource=github-releases depName=snail007/goproxy
ENV GOPROXY_VERSION="v15.2"
ENV GOPROXY_MODE="auto"
ENV GOPROXY_ARGS="http -p :8080"
ENV GOPROXY_INSTANCES_DIR="/config/instances.d"
ENV GOPROXY_STRICT_ARGS="true"

# hadolint ignore=DL3018
RUN \
    echo "**** install runtime dependencies ****" && \
    apk add --no-cache \
    ca-certificates && \
    echo "**** download goproxy binary ****" && \
    apk add --no-cache --virtual=.fetch-deps \
    curl tar && \
    case "$(apk --print-arch)" in \
        x86_64) GOARCH="amd64" ;; \
        aarch64) GOARCH="arm64-v8" ;; \
        *) echo "Unsupported Alpine arch: $(apk --print-arch)" && exit 1 ;; \
    esac && \
    curl -fsSL \
        "https://github.com/snail007/goproxy/releases/download/${GOPROXY_VERSION}/proxy-linux-${GOARCH}.tar.gz" \
        -o /tmp/proxy.tar.gz && \
    mkdir -p /tmp/goproxy /defaults/proxy && \
    tar -xzf /tmp/proxy.tar.gz -C /tmp/goproxy && \
    cp -f /tmp/goproxy/blocked /defaults/proxy/blocked && \
    cp -f /tmp/goproxy/direct /defaults/proxy/direct && \
    cp -f /tmp/goproxy/proxy /usr/local/bin/proxy && \
    chmod 0755 /usr/local/bin/proxy && \
    apk del --no-network .fetch-deps && \
    echo "**** cleanup ****" && \
    rm -rf \
    /tmp/*

# copy local files
COPY ./apps/goproxy/root /

# ports and volumes
EXPOSE 8080

VOLUME /config
