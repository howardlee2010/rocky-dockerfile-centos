FROM kolla/centos-source-prometheus-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-server" build-date="20180904"




ENV prometheus_version=1.7.1



RUN curl -sSL -o /tmp/prometheus.tar.gz https://github.com/prometheus/prometheus/releases/download/v${prometheus_version}/prometheus-${prometheus_version}.linux-${prometheus_arch}.tar.gz \
    && tar xvf /tmp/prometheus.tar.gz -C /opt/ \
    && rm -f /tmp/prometheus.tar.gz \
    && ln -s /opt/prometheus* /opt/prometheus \
    && mkdir -p /etc/prometheus /data





USER prometheus