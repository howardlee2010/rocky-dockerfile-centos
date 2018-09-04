FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="influxdb" build-date="20180904"








RUN usermod --append --home /var/lib/influxdb --groups kolla influxdb \
    && mkdir -p /var/lib/influxdb \
    && chown -R 42421:42421 /var/lib/influxdb



RUN yum -y install influxdb && yum clean all && rm -rf /var/cache/yum

COPY influxdb_sudoers /etc/sudoers.d/kolla_influxdb_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_influxdb_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start




USER influxdb