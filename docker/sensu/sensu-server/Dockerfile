FROM kolla/centos-source-sensu-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="sensu-server" build-date="20180904"






    


RUN yum -y install cyrus-sasl-devel gcc-c++ make ruby-devel && yum clean all && rm -rf /var/cache/yum





RUN sensu-install --plugins mailer,slack





USER sensu