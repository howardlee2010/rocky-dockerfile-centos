FROM kolla/centos-source-ovsdpdk:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovsdpdk-db" build-date="20180904"



COPY extend_start.sh /usr/local/bin/kolla_ovsdpdk_extend_start
COPY start_ovsdb_server.sh /usr/local/bin/start-ovsdb-server
RUN chmod 755 /usr/local/bin/kolla_ovsdpdk_extend_start && \
    chmod 755 /usr/local/bin/start-ovsdb-server


