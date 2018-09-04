FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="etcd" build-date="20180904"








RUN usermod --append --home /var/lib/etcd --groups kolla etcd \
    && mkdir -p /var/lib/etcd \
    && chown -R 42413:42413 /var/lib/etcd



    

RUN yum -y install etcd && yum clean all && rm -rf /var/cache/yum

COPY etcd_sudoers /etc/sudoers.d/kolla_etcd_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_etcd_sudoers




USER etcd