FROM centos:7@sha256:be65f488b7764ad3638f236b7b515b3678369a5124c47b8d32916d6487418ea4

USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
