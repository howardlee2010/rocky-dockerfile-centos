FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="aodh-base" build-date="20180904"








RUN usermod --append --home /var/lib/aodh --groups kolla aodh \
    && mkdir -p /var/lib/aodh \
    && chown -R 42402:42402 /var/lib/aodh



    

       

RUN yum -y install httpd mod_wsgi mod_ssl python2-ldappool && yum clean all && rm -rf /var/cache/yum
RUN mkdir -p /var/www/cgi-bin/aodh \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf
    

ADD aodh-base-archive /aodh-base-source



RUN ln -s aodh-base-source/* aodh \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /aodh pymongo \
    && mkdir -p /etc/aodh /var/www/cgi-bin/aodh \
    && cp /aodh/aodh/api/app.wsgi /var/www/cgi-bin/aodh \
    && chown -R aodh: /etc/aodh /var/www/cgi-bin/aodh



COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY aodh_sudoers /etc/sudoers.d/kolla_aodh_sudoers

RUN chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_aodh_sudoers \
    && chmod 755 /var/www/cgi-bin/aodh \
    && touch /usr/local/bin/kolla_aodh_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_aodh_extend_start

