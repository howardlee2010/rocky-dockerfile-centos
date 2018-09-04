FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="memcached" build-date="20180904"







RUN usermod --append --home /run/memcache --groups kolla memcached \
    && mkdir -p /run/memcache \
    && chown -R 42457:42457 /run/memcache



RUN yum -y install memcached && yum clean all && rm -rf /var/cache/yum




USER memcached