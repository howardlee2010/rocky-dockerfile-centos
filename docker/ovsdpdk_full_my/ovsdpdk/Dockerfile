FROM kolla/centos-source-base:7.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovsdpdk" build-date="20191030"

RUN rm -rf /etc/yum.repos.d/opendaylight.repo \
  && yum clean all \
  && yum makecache

COPY rpms /tmp/rpms

RUN yum localinstall /tmp/rpms/kernel-devel-3.10.0-862.el7.x86_64.rpm -y \
  && yum localinstall /tmp/rpms/kernel-headers-3.10.0-862.el7.x86_64.rpm -y \
  && rm -rf /tmp/rpms

RUN yum -y install redhat-lsb-core pciutils autoconf libtool fuse-devel gcc make autoconf automake libpcap-devel python-devel python-six crudini numactl-devel && yum clean all && rm -rf /var/cache/yum

RUN mkdir -p /lib/modules/$(uname -r) \
  && ln -s /usr/src/kernels/$(uname -r) /lib/modules/$(uname -r)/build

COPY plugins /plugins

RUN ln -s /plugins/openvswitch-2.10.0/ /ovs \
  && ln -s /plugins/dpdk-17.11/ /dpdk

WORKDIR /dpdk

RUN make config T="x86_64-native-linuxapp-gcc"

WORKDIR "/dpdk/build"

RUN  sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_BUILD_COMBINE_LIBS=n/CONFIG_RTE_BUILD_COMBINE_LIBS=y/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_MAX_MEMSEG=.*$/CONFIG_RTE_MAX_MEMSEG=1024/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_LIBRTE_VHOST=.*$/CONFIG_RTE_LIBRTE_VHOST=y/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_LIBRTE_KNI=.*$/CONFIG_RTE_LIBRTE_KNI=n/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_KNI_KMOD=.*$/CONFIG_RTE_KNI_KMOD=n/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_EAL_IGB_UIO=.*$/CONFIG_RTE_EAL_IGB_UIO=y/"  &&   sed -i "/dpdk/build/.config" -e "s/CONFIG_RTE_BUILD_SHARED_LIB=.*$/CONFIG_RTE_BUILD_SHARED_LIB=n/"  

RUN make -j $(nproc) EXTRA_CFLAGS='-O2 -fPIC' \
  && make install

WORKDIR /ovs

RUN ./boot.sh \
  && ./configure --with-dpdk="/dpdk/build" --prefix=/usr --with-dbdir=/etc/openvswitch --with-rundir=/run/openvswitch \
  && make -j $(nproc) CFLAGS='-O2 -fPIC' \
  && make install

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

