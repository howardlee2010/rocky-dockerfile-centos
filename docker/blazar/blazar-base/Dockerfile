FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="blazar-base" build-date="20180904"








RUN usermod --append --home /var/lib/blazar --groups kolla blazar \
    && mkdir -p /var/lib/blazar \
    && chown -R 42471:42471 /var/lib/blazar




ADD blazar-base-archive /blazar-base-source



RUN ln -s blazar-base-source/* blazar \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /blazar \
    && mkdir -p /etc/blazar \
    && cp -r /blazar/etc/blazar/* /etc/blazar \
    && chown -R blazar: /etc/blazar



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_blazar_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_blazar_extend_start

