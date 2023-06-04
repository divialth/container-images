FROM rockylinux/rockylinux:8@sha256:20cfffabbe5fe1ff6643741bde0afdea23a2e525639b2fbf97c5820ecad11871

USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
