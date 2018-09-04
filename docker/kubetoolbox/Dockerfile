FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kubetoolbox" build-date="20180904"







RUN yum -y install ceph-common ipmitool jq && yum clean all && rm -rf /var/cache/yum


    
    
        ENV KUBE_ARCH=amd64
    

    RUN curl -o /usr/bin/kubectl http://storage.googleapis.com/kubernetes-release/release/v1.5.4/bin/linux/${KUBE_ARCH}/kubectl \
        && chmod 755 /usr/bin/kubectl




