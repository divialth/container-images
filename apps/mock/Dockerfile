FROM rockylinux:9@sha256:b07e21a7bbcecbae55b9153317d333d4d50808bf5dc0859db0180b6fbd7afb3d

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
