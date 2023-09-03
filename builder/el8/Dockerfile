FROM rockylinux:8@sha256:85fa0b733cfbcc6e9770829b69ebcc58f51ff71fc9c0f4f5cdf40e3c7f58ccad

USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
