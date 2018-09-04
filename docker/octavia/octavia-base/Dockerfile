FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="octavia-base" build-date="20180904"








RUN usermod --append --home /var/lib/octavia --groups kolla octavia \
    && mkdir -p /var/lib/octavia \
    && chown -R 42437:42437 /var/lib/octavia



ADD octavia-base-archive /octavia-base-source



RUN ln -s /octavia-base-source/* octavia \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /octavia \
    && mkdir -p /etc/octavia \
    && cp -r /octavia/etc/* /etc/octavia/ \
    && chown -R octavia: /etc/octavia


COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_octavia_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_octavia_extend_start

