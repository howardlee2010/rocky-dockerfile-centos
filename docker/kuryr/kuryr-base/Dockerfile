FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kuryr-base" build-date="20180904"








RUN usermod --append --home /var/lib/kuryr --groups kolla kuryr \
    && mkdir -p /var/lib/kuryr \
    && chown -R 42469:42469 /var/lib/kuryr




ADD kuryr-base-archive /kuryr-base-source



# NOTE(Jeffrey4l): remove kuryr-lib constraint in upper-constraints.txt file.
# Otherwise, it will be failed.
RUN ln -s kuryr-base-source/* kuryr-base \
    && sed -i 's|^kuryr-lib===.*$||g' requirements/upper-constraints.txt \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /kuryr-base \
    && mkdir -p /etc/kuryr \
    && chown -R kuryr: /etc/kuryr


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

