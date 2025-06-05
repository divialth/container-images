FROM rockylinux/rockylinux:9@sha256:91bbb8eb52ca462611c1f9ce5c4cede4172a31bfe64f336e82f29648694a3cfe

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel systemd-rpm-macros && \
    yum clean all
