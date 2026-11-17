FROM rockylinux/rockylinux:10@sha256:d24beedc58f79b9e0e9289fedaa4fcbcbe692b1438883a86f177fd7c51053ca8

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
