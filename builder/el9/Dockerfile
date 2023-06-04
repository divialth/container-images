FROM rockylinux/rockylinux:9@sha256:3387f6adc2fcdba59b9ff07acb955b4dbb610d3d93f7c68182107c1d25fac39c

USER root

RUN yum install -y rpm-build rpm-sign python3-devel systemd-rpm-macros && \
    yum clean all
