FROM rockylinux/rockylinux:9

USER root

RUN dnf install -y epel-release && \
    crb enable
RUN dnf install -y mock && \
    yum clean all

RUN useradd mockbuilder
RUN usermod -a -G mock mockbuilder

USER mockbuilder
