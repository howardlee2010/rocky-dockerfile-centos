FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="openvswitch-base" build-date="20180904"








    


RUN yum -y install openvswitch && yum clean all && rm -rf /var/cache/yum



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_openvswitch_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_openvswitch_extend_start

