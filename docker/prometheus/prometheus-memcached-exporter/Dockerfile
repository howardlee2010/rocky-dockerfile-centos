FROM kolla/centos-source-prometheus-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-memcached-exporter" build-date="20180904"




ENV memcached_exporter_version=0.4.1



RUN curl -sSL -o /tmp/memcached_exporter.tar.gz https://github.com/prometheus/memcached_exporter/releases/download/v${memcached_exporter_version}/memcached_exporter-${memcached_exporter_version}.linux-${prometheus_arch}.tar.gz \
    && tar xvf /tmp/memcached_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/memcached_exporter.tar.gz \
    && ln -s /opt/memcached_exporter* /opt/memcached_exporter





USER prometheus