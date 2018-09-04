FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="congress-base" build-date="20180904"








RUN usermod --append --home /var/lib/congress --groups kolla congress \
    && mkdir -p /var/lib/congress \
    && chown -R 42410:42410 /var/lib/congress






ADD congress-base-archive /congress-base-source
RUN ln -s congress-base-source/* congress \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /congress \
    && mkdir -p /etc/congress \
    && cp -r /congress/etc/* /etc/congress/ \
    && chown -R congress: /etc/congress



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_congress_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_congress_extend_start

