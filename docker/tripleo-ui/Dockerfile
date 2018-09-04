FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="tripleo-ui" build-date="20180904"






    
        

        RUN yum -y install httpd mod_ssl bzip2 nodejs && yum clean all && rm -rf /var/cache/yum

RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

ADD tripleo-ui-archive /tripleo-ui-source
RUN cd tripleo-ui-source/package \
    && npm install \
    && npm run build \
    && mkdir -p /var/www/openstack-tripleo-ui \
    && cp -rf dist /var/www/openstack-tripleo-ui/



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start


