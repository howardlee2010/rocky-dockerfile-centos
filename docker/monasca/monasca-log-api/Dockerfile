FROM kolla/centos-source-monasca-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-log-api" build-date="20180904"







ADD monasca-log-api-archive /monasca-log-api-source
RUN ln -s monasca-log-api-source/* monasca-log \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /monasca-log



COPY extend_start.sh /usr/local/bin/kolla_monasca_extend_start
RUN chmod 755 /usr/local/bin/kolla_monasca_extend_start





