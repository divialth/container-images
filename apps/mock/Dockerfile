FROM rockylinux/rockylinux:9@sha256:91bbb8eb52ca462611c1f9ce5c4cede4172a31bfe64f336e82f29648694a3cfe

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
