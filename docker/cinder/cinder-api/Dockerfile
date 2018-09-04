FROM kolla/centos-source-cinder-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cinder-api" build-date="20180904"







    
        
RUN yum -y install httpd mod_ssl mod_wsgi && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

RUN mkdir -p /var/www/cgi-bin/cinder \
    && cp -a /var/lib/kolla/venv/bin/cinder-wsgi /var/www/cgi-bin/cinder/cinder-wsgi



COPY extend_start.sh /usr/local/bin/kolla_cinder_extend_start
RUN chmod 755 /usr/local/bin/kolla_cinder_extend_start \
    && chown -R cinder: /var/www/cgi-bin/cinder \
    && chmod 755 /var/www/cgi-bin/cinder/cinder-wsgi


