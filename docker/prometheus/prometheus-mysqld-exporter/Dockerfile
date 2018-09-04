FROM kolla/centos-source-prometheus-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-mysqld-exporter" build-date="20180904"




ENV mysqld_exporter_version=0.10.0



RUN curl -ssL -o /tmp/mysqld_exporter.tar.gz https://github.com/prometheus/mysqld_exporter/releases/download/v${mysqld_exporter_version}/mysqld_exporter-${mysqld_exporter_version}.linux-${prometheus_arch}.tar.gz \
    && tar xvf /tmp/mysqld_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/mysqld_exporter.tar.gz \
    && ln -s /opt/mysqld_exporter* /opt/mysqld_exporter





USER prometheus