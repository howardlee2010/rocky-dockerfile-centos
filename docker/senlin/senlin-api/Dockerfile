FROM kolla/centos-source-senlin-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="senlin-api" build-date="20180904"







COPY extend_start.sh /usr/local/bin/kolla_senlin_extend_start
RUN chmod 755 /usr/local/bin/kolla_senlin_extend_start




USER senlin