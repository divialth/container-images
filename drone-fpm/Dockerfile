FROM rockylinux/rockylinux:10-ubi@sha256:b316080c3c3cc005af04d71e66bc7a4a3efd50dba43dee641efffdddc79c9441

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
