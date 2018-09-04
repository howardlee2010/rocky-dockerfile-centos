FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="panko-base" build-date="20180904"








RUN usermod --append --home /var/lib/panko --groups kolla panko \
    && mkdir -p /var/lib/panko \
    && chown -R 42438:42438 /var/lib/panko



    

       
RUN yum -y install httpd mod_ssl mod_wsgi python2-ldappool && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    
ADD panko-base-archive /panko-base-source



RUN ln -s panko-base-source/* panko \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /panko pymongo \
    && mkdir -p /etc/panko \
    && cp -r /panko/etc/panko/* /etc/panko/ \
    && chown -R panko: /etc/panko



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_panko_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_panko_extend_start

