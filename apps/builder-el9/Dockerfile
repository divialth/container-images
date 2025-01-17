FROM rockylinux/rockylinux:9@sha256:149fd31d916038eb1084d0e051537e279d7afcd5de0b365254e8fa3c3ef12bad

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel systemd-rpm-macros && \
    yum clean all
