FROM rockylinux/rockylinux:8@sha256:e8a49c5403b687db05d4d67333fa45808fbe74f36e683cec7abb1f7d0f2338c6

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
