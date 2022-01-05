ARG UBI_BASE_IMAGE=ubi8/ruby-27

FROM registry.access.redhat.com/${UBI_BASE_IMAGE}

USER root

RUN yum install -y --disableplugin=subscription-manager http://mirror.centos.org/centos/8/BaseOS/x86_64/os/Packages/rpm-sign-4.14.3-19.el8.x86_64.rpm && \
    yum clean all --disableplugin=subscription-manager

RUN gem install fpm

COPY entrypoint.sh /bin/entrypoint.sh

RUN chmod 755 /bin/entrypoint.sh

ENTRYPOINT ["/bin/entrypoint.sh"]
