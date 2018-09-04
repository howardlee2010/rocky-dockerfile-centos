FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="heat-base" build-date="20180904"








RUN usermod --append --home /var/lib/heat --groups kolla heat \
    && mkdir -p /var/lib/heat \
    && chown -R 42418:42418 /var/lib/heat






    
RUN yum -y install httpd mod_ssl mod_wsgi && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf



ADD heat-base-archive /heat-base-source



RUN ln -s heat-base-source/* heat \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /heat \
    && mkdir -p /etc/heat \
    && cp -r /heat/etc/heat/* /etc/heat/ \
    && chown -R heat: /etc/heat



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_heat_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_heat_extend_start

