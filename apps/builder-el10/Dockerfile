FROM rockylinux/rockylinux:10@sha256:827d37bc128288ccf160ee318bb3cb92d591164cb217e92f8bc61e3982ae1834

# hadolint ignore=DL3002
USER root

# hadolint ignore=DL3041,SC2086
RUN INSTALL_PKGS=" \
    python3-devel \
    rpm-build \
    rpm-sign \
    systemd-rpm-macros \
    " && \
    dnf install -y --setopt=tsflags=nodocs ${INSTALL_PKGS} && \
    dnf reinstall -y --setopt=tsflags=nodocs tzdata && \
    dnf -y clean all --enablerepo='*' && \
    rpm -V ${INSTALL_PKGS}
