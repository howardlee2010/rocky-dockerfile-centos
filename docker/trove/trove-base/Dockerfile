FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="trove-base" build-date="20180904"








RUN usermod --append --home /var/lib/trove --groups kolla trove \
    && mkdir -p /var/lib/trove \
    && chown -R 42449:42449 /var/lib/trove




ADD trove-base-archive /trove-base-source



RUN ln -s trove-base-source/* trove \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /trove \
    && mkdir -p /etc/trove \
    && cp -r /trove/etc/trove/* /etc/trove/ \
    && chown -R trove: /etc/trove



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_trove_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_trove_extend_start

