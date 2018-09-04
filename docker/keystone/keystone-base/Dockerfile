FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="keystone-base" build-date="20180904"








RUN usermod --append --home /var/lib/keystone --groups kolla keystone \
    && mkdir -p /var/lib/keystone \
    && chown -R 42425:42425 /var/lib/keystone



    
        
RUN yum -y install httpd mod_auth_mellon mod_auth_openidc mod_ssl mod_wsgi python2-ldappool && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    


ADD keystone-base-archive /keystone-base-source



RUN ln -s keystone-base-source/* keystone \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /keystone \
    && mkdir -p /etc/keystone /var/www/cgi-bin/keystone \
    && cp -r /keystone/etc/* /etc/keystone/ \
    && cp /var/lib/kolla/venv/bin/keystone-wsgi-admin /var/www/cgi-bin/keystone/admin \
    && cp /var/lib/kolla/venv/bin/keystone-wsgi-public /var/www/cgi-bin/keystone/main \
    && chown -R keystone: /etc/keystone /var/www/cgi-bin/keystone




RUN chown -R keystone: /var/www/cgi-bin/keystone \
    && chmod 755 /var/www/cgi-bin/keystone/*

