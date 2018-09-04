FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="karbor-base" build-date="20180904"








RUN usermod --append --home /var/lib/karbor --groups kolla karbor \
    && mkdir -p /var/lib/karbor \
    && chown -R 42458:42458 /var/lib/karbor




ADD karbor-base-archive /karbor-base-source



RUN ln -s karbor-base-source/* karbor \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /karbor \
    && mkdir -p /etc/karbor \
    && cp -r /karbor/etc/* /etc/karbor/ \
    && chown -R karbor: /etc/karbor



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_karbor_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_karbor_extend_start

