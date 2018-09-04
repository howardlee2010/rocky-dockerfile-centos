FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="magnum-base" build-date="20180904"








RUN usermod --append --home /var/lib/magnum --groups kolla magnum \
    && mkdir -p /var/lib/magnum \
    && chown -R 42428:42428 /var/lib/magnum




ADD magnum-base-archive /magnum-base-source



RUN ln -s magnum-base-source/* magnum \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /magnum[osprofiler] \
    && mkdir -p /etc/magnum \
    && cp -r /magnum/etc/magnum/* /etc/magnum \
    && chown -R magnum: /etc/magnum



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_magnum_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_magnum_extend_start

