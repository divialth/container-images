FROM registry.access.redhat.com/ubi8/ruby-30@sha256:dc05ced6f0eb1f43f2e78bd6329767a86b205d6e7b2590d62b41b937869ed3d5

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
