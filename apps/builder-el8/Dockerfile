FROM rockylinux:8@sha256:d5a5e761584609184c7609b4ecdc9ecf13be048fa80299cff10519d52e734ac7

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
