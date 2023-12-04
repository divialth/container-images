FROM rockylinux:9@sha256:c944604c0c759f5d164ffbdf0bbab2fac582b739938937403c067ab634a0518a

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel systemd-rpm-macros && \
    yum clean all
