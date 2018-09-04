FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="collectd" build-date="20180904"








RUN usermod --append --home /var/lib/collectd --groups kolla collectd \
    && mkdir -p /var/lib/collectd \
    && chown -R 42409:42409 /var/lib/collectd





  

  
      

  
# make sure, collectd is pulled from centos-opstools
RUN yum-config-manager --disable epel


RUN yum -y install collectd collectd-amqp1 collectd-apache collectd-ceph collectd-connectivity collectd-disk collectd-ipmi collectd-mysql collectd-netlink collectd-ovs-events collectd-ovs-stats collectd-ping collectd-procevent collectd-python collectd-smart collectd-snmp-agent collectd-sysevent collectd-utils collectd-virt collectd-write_kafka collectd-write_prometheus python-collectd-gnocchi collectd-hugepages collectd-rdt collectd-turbostat && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chown -R collectd /var/lib/collectd \
    && chown -R collectd /etc/collectd* \
    && chown -R collectd /var/run/




USER collectd