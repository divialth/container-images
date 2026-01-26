FROM docker.io/centos:centos7@sha256:be65f488b7764ad3638f236b7b515b3678369a5124c47b8d32916d6487418ea4

USER root

RUN sed -i -e 's|^mirrorlist=|#mirrorlist=|g' \
        -e 's|^#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' \
        /etc/yum.repos.d/CentOS-Base.repo

RUN INSTALL_PKGS=" \
    python3-devel \
    rpm-build \
    rpm-sign \
    " && \
    yum install -y --setopt=tsflags=nodocs ${INSTALL_PKGS} && \
    yum reinstall -y --setopt=tsflags=nodocs tzdata && \
    yum -y clean all --enablerepo='*' && \
    rpm -V ${INSTALL_PKGS}
