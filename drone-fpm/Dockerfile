FROM registry.access.redhat.com/ubi8/ruby-30@sha256:57c188d84d434c827432a8f7ad3efe3a6973cbf7fa578326d1b7c2a018d40dc4

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
