# renovate: datasource=rubygems depName=fpm versioning=ruby
ENV FPM_VERSION 1.15.1

FROM registry.access.redhat.com/ubi8/ruby-30@sha256:3ea98761f3d620d2607dce2943c02faff6c55ade4d6ecc9ee2bf32f047b1dfc4

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

RUN gem install --no-rdoc --no-ri  fpm -v ${FPM_VERSION}

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
