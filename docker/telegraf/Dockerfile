FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="telegraf" build-date="20180904"







RUN usermod --append --home /etc/telegraf --groups kolla telegraf \
    && mkdir -p /etc/telegraf \
    && chown -R 42448:42448 /etc/telegraf





    


RUN yum -y install chrony net-tools telegraf collectd python2-pip && yum clean all && rm -rf /var/cache/yum

COPY telegraf_sudoers /etc/sudoers.d/kolla_telegraf_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_telegraf_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start




USER telegraf