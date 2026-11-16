FROM rockylinux/rockylinux:9@sha256:bb5755f96bec05ff26165e779ec843d7167544be9e50770508f307019a6d05c4

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
