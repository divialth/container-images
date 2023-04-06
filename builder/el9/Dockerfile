FROM rockylinux/rockylinux:9

USER root

RUN yum install -y rpm-build rpm-sign python3-devel systemd-rpm-macros && \
    yum clean all
