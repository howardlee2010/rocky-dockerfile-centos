FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="designate-base" build-date="20180904"








RUN usermod --append --home /var/lib/designate --groups kolla designate \
    && mkdir -p /var/lib/designate \
    && chown -R 42411:42411 /var/lib/designate






ADD designate-base-archive /designate-base-source
RUN ln -s designate-base-source/* designate \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /designate \
    && mkdir -p /etc/designate \
    && cp -r /designate/etc/designate/* /etc/designate/ \
    && mv /etc/designate/rootwrap.conf.sample /etc/designate/rootwrap.conf \
    && chown -R designate: /etc/designate \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/designate/rootwrap.conf


COPY designate_sudoers /etc/sudoers.d/kolla_designate_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_designate_sudoers \
    && touch /usr/local/bin/kolla_designate_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_designate_extend_start

