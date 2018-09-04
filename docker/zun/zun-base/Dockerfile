FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zun-base" build-date="20180904"








RUN usermod --append --home /var/lib/zun --groups kolla zun \
    && mkdir -p /var/lib/zun \
    && chown -R 42463:42463 /var/lib/zun




    

        

RUN yum -y install httpd mod_wsgi mod_ssl python2-ldappool && yum clean all && rm -rf /var/cache/yum
RUN mkdir -p /var/www/cgi-bin/zun \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

ADD zun-base-archive /zun-base-source



RUN ln -s zun-base-source/* zun \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /zun \
    && mkdir -p /etc/zun /var/www/cgi-bin/zun \
    && cp -r /zun/etc/zun/* /etc/zun/ \
    && cp /zun/zun/api/app.wsgi /var/www/cgi-bin/zun \
    && chown -R zun: /etc/zun /var/www/cgi-bin/zun



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_zun_extend_start \
    && chmod 755 /var/www/cgi-bin/zun \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_zun_extend_start

