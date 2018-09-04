FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="watcher-base" build-date="20180904"








RUN usermod --append --home /var/lib/watcher --groups kolla watcher \
    && mkdir -p /var/lib/watcher \
    && chown -R 42451:42451 /var/lib/watcher




ADD watcher-base-archive /watcher-base-source



RUN ln -s watcher-base-source/* watcher \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /watcher \
    && mkdir -p /etc/watcher \
    && cp -r /watcher/etc/watcher/* /etc/watcher/ \
    && chown -R watcher: /etc/watcher



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_watcher_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_watcher_extend_start

