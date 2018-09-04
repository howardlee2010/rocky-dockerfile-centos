FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="qdrouterd" build-date="20180904"








RUN usermod --append --home /var/lib/qdrouterd --groups kolla qdrouterd \
    && mkdir -p /var/lib/qdrouterd \
    && chown -R 42465:42465 /var/lib/qdrouterd




    

RUN yum -y install cyrus-sasl-lib cyrus-sasl-plain qpid-dispatch-router && yum clean all && rm -rf /var/cache/yum




COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY qdrouterd_sudoers /etc/sudoers.d/kolla_qdrouterd_sudoers
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_qdrouterd_sudoers




USER qdrouterd