FROM rockylinux/rockylinux:9@sha256:bb5755f96bec05ff26165e779ec843d7167544be9e50770508f307019a6d05c4

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
