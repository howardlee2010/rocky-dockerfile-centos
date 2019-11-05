FROM localhost:4000/kolla/centos-source-ovsdpdk:7.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovsdpdk-vswitchd" build-date="20191030"



COPY extend_start.sh /usr/local/bin/kolla_ovsdpdk_extend_start
RUN chmod 755 /usr/local/bin/kolla_ovsdpdk_extend_start


