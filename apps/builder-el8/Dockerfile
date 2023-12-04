FROM rockylinux:8@sha256:c464612ef7e3d54d658c3eaa4778b5cdc990ec7a4d9ab63b0f00c9994c6ce980

USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
