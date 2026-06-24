FROM rockylinux/rockylinux:9@sha256:8101994123cf3d0a8fee517bee7f39e555c7d92bd2d9eb3303cc988a0eeed00f

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
