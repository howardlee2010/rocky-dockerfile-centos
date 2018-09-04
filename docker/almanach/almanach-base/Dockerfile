FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="almanach-base" build-date="20180904"








RUN usermod --append --home /var/lib/almanach --groups kolla almanach \
    && mkdir -p /var/lib/almanach \
    && chown -R 42475:42475 /var/lib/almanach




ADD almanach-base-archive /almanach-base-source



RUN ln -s almanach-base-source/* almanach \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /almanach \
    && mkdir -p /etc/almanach \
    && chown -R almanach: /etc/almanach



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 755 /usr/local/bin/kolla_extend_start

