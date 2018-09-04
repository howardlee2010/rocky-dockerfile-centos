FROM kolla/centos-source-prometheus-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-alertmanager" build-date="20180904"




ENV prometheus_alertmanager_version=0.14.0



RUN curl -sSL -o /tmp/prometheus_alertmanager.tar.gz https://github.com/prometheus/alertmanager/releases/download/v${prometheus_alertmanager_version}/alertmanager-${prometheus_alertmanager_version}.linux-${prometheus_arch}.tar.gz \
    && tar xvf /tmp/prometheus_alertmanager.tar.gz -C /opt/ \
    && rm -f /tmp/prometheus_alertmanager.tar.gz \
    && ln -s /opt/alertmanager* /opt/prometheus_alertmanager





USER prometheus