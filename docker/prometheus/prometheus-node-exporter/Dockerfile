FROM kolla/centos-source-prometheus-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-node-exporter" build-date="20180904"




ENV node_exporter_version=0.14.0



RUN curl -sSL -o /tmp/node_exporter.tar.gz https://github.com/prometheus/node_exporter/releases/download/v${node_exporter_version}/node_exporter-${node_exporter_version}.linux-${prometheus_arch}.tar.gz \
    && tar xvf /tmp/node_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/node_exporter.tar.gz \
    && ln -s /opt/node_exporter* /opt/node_exporter





USER prometheus