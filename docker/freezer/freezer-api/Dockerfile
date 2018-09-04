FROM kolla/centos-source-freezer-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="freezer-api" build-date="20180904"







    
        

RUN yum -y install httpd mod_ssl mod_wsgi && yum clean all && rm -rf /var/cache/yum

RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf
    

ADD freezer-api-archive /freezer-api-source



RUN ln -s freezer-api-source/* freezer-api \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /freezer-api \
    && cp -r /freezer-api/etc/freezer/* /etc/freezer/



COPY extend_start.sh /usr/local/bin/kolla_freezer_extend_start
RUN chmod 755 /usr/local/bin/kolla_freezer_extend_start


