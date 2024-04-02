FROM registry.access.redhat.com/ubi8/ruby-30@sha256:c1a27d5c2ee66fb627a33c8b10a801b749fe526efe3f0934fcd3129c8bbdfbdd

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
