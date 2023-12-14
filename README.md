# Realtek RTL8156 NIC driver for ESXi 8.0.2

This source code is based on realtek official source, VMware-ESXI-67U3-ODP and VMware-TOOLS-10.2.0-ODP.

Just do these steps:
- Prepare the building environment, I did it on CentOS 7
- Log in with root, make a folder name 'build' on /, make folder toolchain and vsphere in /build.
- Copy and extract gcc-4.8.0, binutils-2.22, glibc-2.3.4-2.41 to /build/toolchain/src 
- Compile the toolchain, dest path is /build/toolchain/lin64
- Extract and copy vmkdrivers-gpl from 67U3-ODP to /build/vsphere
- Copy build-r8125.sh to /build/vsphere/vmkdrivers-gpl/
- Copy r8125 folder to /build/vsphere/vmkdrivers-gpl/vmkdrivers/src_9/drivers/net
- Run build-r8125.sh

- Realtek USB FE / GBE / 2.5G / 5G Ethernet Family Controller Software
https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software

VMware vSphere Hypervisor (ESXi) 8.0 Open Source Information
https://customerconnect.vmware.com/downloads/get-download?downloadGroup=VS-MGMT-SDK80U2-OSS
Open Source Disclosure packages for VMWare vSphere Hypervisor (ESXi) 8.0u2
SHA1SUM: e6e0f6302bdd5b2c6c3e6cd1d17dfbd2e28e41a8

Open Source Disclosure Package for VMware vSphere Hypervisor (ESXi) 8.0u2 Toolchain
TOOLCHAIN packages, contains all the used toolchains during the build process, together with source, build instructions and build scripts.
https://github.com/vmware/open-vm-tools/archive/refs/tags/stable-12.3.5.tar.gz
- test
esxcli software vib remove -n net-r8125 esxcli software vib install -v /vmfs/volumes/datastore1/net-r8125-9.006.04-1.vib
