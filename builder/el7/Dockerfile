FROM centos:7@sha256:dead07b4d8ed7e29e98de0f4504d87e8880d4347859d839686a31da35a3b532f

USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
