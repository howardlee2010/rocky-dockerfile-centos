FROM kolla/centos-source-ovn-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovn-sb-db-server" build-date="20180904"






    


RUN yum -y install openvswitch-ovn-central && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_ovn_extend_start
COPY start_sb_db_server.sh /usr/local/bin/start-sb-db-server
RUN chmod 755 /usr/local/bin/kolla_ovn_extend_start \
              /usr/local/bin/start-sb-db-server


