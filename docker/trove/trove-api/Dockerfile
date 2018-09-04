FROM kolla/centos-source-trove-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="trove-api" build-date="20180904"







COPY extend_start.sh /usr/local/bin/kolla_trove_extend_start
RUN chmod 755 /usr/local/bin/kolla_trove_extend_start




USER trove