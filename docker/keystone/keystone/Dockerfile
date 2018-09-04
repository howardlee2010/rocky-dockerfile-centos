FROM kolla/centos-source-keystone-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="keystone" build-date="20180904"





COPY keystone_bootstrap.sh /usr/local/bin/kolla_keystone_bootstrap
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_keystone_bootstrap


    
        
    
RUN yum -y install mod_auth_gssapi && yum clean all && rm -rf /var/cache/yum
ADD plugins-archive /



RUN if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/* requests-kerberos; \
    fi




