FROM kolla/centos-source-base:7.0.5
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovsdpdk" build-date="20191030"






# install ovs from source


    



RUN yum -y install kernel-devel-$(uname -r) redhat-lsb-core pciutils autoconf libtool fuse-devel gcc make autoconf automake libpcap-devel python-devel python-six crudini && yum clean all && rm -rf /var/cache/yum


RUN mkdir -p /lib/modules/$(uname -r) \
    && ln -s /usr/src/kernels/$(uname -r) /lib/modules/$(uname -r)/build


ADD plugins-archive /
RUN ln -s /plugins/ovsdpdk-plugin-ovs-archive-*/ /ovs \
    && ln -s /plugins/ovsdpdk-plugin-dpdk-archive-*/ /dpdk
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


