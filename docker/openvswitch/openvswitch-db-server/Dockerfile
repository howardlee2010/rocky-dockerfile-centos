FROM kolla/centos-source-openvswitch-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="openvswitch-db-server" build-date="20180904"



COPY ovs_ensure_configured.sh /usr/local/bin/kolla_ensure_openvswitch_configured
COPY extend_start.sh /usr/local/bin/kolla_openvswitch_extend_start
COPY start_ovsdb_server.sh /usr/local/bin/start-ovsdb-server
RUN chmod 755 /usr/local/bin/kolla_ensure_openvswitch_configured \
              /usr/local/bin/kolla_openvswitch_extend_start \
              /usr/local/bin/start-ovsdb-server


