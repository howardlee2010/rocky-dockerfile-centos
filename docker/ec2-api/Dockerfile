FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ec2-api" build-date="20180904"








RUN usermod --append --home /var/lib/ec2api --groups kolla ec2api \
    && mkdir -p /var/lib/ec2api \
    && chown -R 42466:42466 /var/lib/ec2api




ADD ec2-api-archive /ec2-api-source



RUN ln -s ec2-api-source/* ec2-api \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /ec2-api \
    && mkdir -p /etc/ec2api \
    && cp -r /ec2-api/etc/ec2api/* /etc/ec2api \
    && chown -R ec2api: /etc/ec2api



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 755 /usr/local/bin/kolla_extend_start




USER ec2api