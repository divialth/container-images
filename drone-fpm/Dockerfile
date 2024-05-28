FROM registry.access.redhat.com/ubi8/ruby-30@sha256:8586c7eef1d0bcc0575bafd0e77f626c6aad850d2bf80e810013fae4d5d801f3

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
