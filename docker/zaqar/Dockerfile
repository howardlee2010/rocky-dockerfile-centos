FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zaqar" build-date="20180904"








RUN usermod --append --home /var/lib/zaqar --groups kolla zaqar \
    && mkdir -p /var/lib/zaqar \
    && chown -R 42452:42452 /var/lib/zaqar





    
RUN yum -y install httpd mod_ssl mod_wsgi && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf



ADD zaqar-archive /zaqar-source



RUN ln -s zaqar-source/* zaqar \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt pymongo /zaqar \
    && mkdir -p /etc/zaqar \
    && cp -r /zaqar/etc/* /etc/zaqar/ \
    && chown -R zaqar: /etc/zaqar



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER zaqar