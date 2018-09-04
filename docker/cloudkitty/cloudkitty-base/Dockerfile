FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cloudkitty-base" build-date="20180904"








RUN usermod --append --home /var/lib/cloudkitty --groups kolla cloudkitty \
    && mkdir -p /var/lib/cloudkitty \
    && chown -R 42408:42408 /var/lib/cloudkitty






ADD cloudkitty-base-archive /cloudkitty-base-source
RUN ln -s cloudkitty-base-source/* cloudkitty \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /cloudkitty \
    && mkdir -p /etc/cloudkitty  \
    && cp -r /cloudkitty/etc/cloudkitty/* /etc/cloudkitty/ \
    && chown -R cloudkitty: /etc/cloudkitty



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_cloudkitty_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_cloudkitty_extend_start

