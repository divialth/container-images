FROM rockylinux:8@sha256:9794037624aaa6212aeada1d28861ef5e0a935adaf93e4ef79837119f2a2d04c

# hadolint ignore=DL3002
USER root

RUN yum install -y rpm-build rpm-sign python3-devel && \
    yum clean all
