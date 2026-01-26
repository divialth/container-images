FROM rockylinux/rockylinux:10@sha256:f4da504c18e7aced902f4f728cde787cd9d9b817bc639fe171026d18364dca6c

# hadolint ignore=DL3002
USER root

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
