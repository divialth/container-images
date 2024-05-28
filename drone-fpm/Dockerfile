FROM registry.access.redhat.com/ubi8/ruby-30@sha256:0202ee867419466e1808729b520f1c5f29fa75e0c2edf6eb4e3f1224ff4b4bca

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1
RUN gem install --no-document fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
