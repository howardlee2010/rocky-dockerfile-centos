FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="rally" build-date="20180904"








RUN usermod --append --home /var/lib/rally --groups kolla rally \
    && mkdir -p /var/lib/rally \
    && chown -R 42440:42440 /var/lib/rally




ADD rally-archive /rally-source



RUN ln -s rally-source/* rally \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /rally os-testr \
    && mkdir -p /etc/rally \
    && chown -R rally: /etc/rally


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER rally