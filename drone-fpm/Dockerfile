ARG UBI_BASE_IMAGE=ubi8/ruby-27

FROM registry.access.redhat.com/${UBI_BASE_IMAGE}

USER root

RUN yum install -y --disableplugin=subscription-manager rpm-build rpm-sign && \
    yum clean all --disableplugin=subscription-manager

RUN gem install fpm

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
