FROM rockylinux/rockylinux:10-ubi@sha256:0d59f109ca0b9e14c15ff5876e34a7e8026515a3aa65aa577b65129d94196471

USER root

RUN INSTALL_PKGS=" \
    libffi-devel \
    redhat-rpm-config \
    rpm-build \
    ruby \
    ruby-bundled-gems \
    ruby-devel \
    rubygem-bundler \
    rubygem-rake \
    " && \
    dnf install -y --setopt=tsflags=nodocs ${INSTALL_PKGS} && \
    dnf reinstall -y --setopt=tsflags=nodocs tzdata && \
    dnf -y clean all --enablerepo='*' && \
    rpm -V ${INSTALL_PKGS}

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.17.0
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
