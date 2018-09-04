FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="vitrage-base" build-date="20180904"








RUN usermod --append --home /var/lib/vitrage --groups kolla vitrage \
    && mkdir -p /var/lib/vitrage \
    && chown -R 42459:42459 /var/lib/vitrage




    

        

RUN yum -y install httpd mod_wsgi mod_ssl python2-ldappool && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    



ADD vitrage-base-archive /vitrage-base-source
RUN ln -s vitrage-base-source/* vitrage \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /vitrage \
    && mkdir -p /etc/vitrage /var/www/cgi-bin/vitrage \
    && cp -r /vitrage/etc/vitrage/* /etc/vitrage/ \
    && cp /vitrage/vitrage/api/app.wsgi /var/www/cgi-bin/vitrage \
    && chown -R vitrage: /etc/vitrage /var/www/cgi-bin/vitrage



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN touch /usr/local/bin/kolla_vitrage_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_vitrage_extend_start

