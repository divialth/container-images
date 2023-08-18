FROM registry.access.redhat.com/ubi8/ruby-30@sha256:3ea98761f3d620d2607dce2943c02faff6c55ade4d6ecc9ee2bf32f047b1dfc4

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build && \
    yum clean all --disableplugin=subscription-manager

# renovate: datasource=rubygems depName=fpm versioning=ruby
RUN gem install fpm -v 1.15.1

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
