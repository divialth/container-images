FROM rockylinux/rockylinux:9@sha256:8101994123cf3d0a8fee517bee7f39e555c7d92bd2d9eb3303cc988a0eeed00f

USER root

RUN dnf install -y epel-release && \
    crb enable
RUN dnf install -y rpm-build rpm-sign rpmdevtools mock && \
    yum clean all

RUN useradd mockbuilder
RUN usermod -a -G mock mockbuilder

USER mockbuilder

RUN mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}

WORKDIR /build
