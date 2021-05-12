# ovs-docker-quagga-tutorial


## 环境要求

centos7 5.12.0-1.el7.elrepo.x86_64 docker openswitch

## openvswitch-2.15.0安装

```text

yum install wget openssl-devel  python-sphinx gcc make python-devel openssl-devel kernel-devel graphviz kernel-debug-devel autoconf automake rpm-build redhat-rpm-config libtool python-twisted-core python-zope-interface PyQt4 desktop-file-utils libcap-ng-devel groff checkpolicy selinux-policy-devel gcc-c++ python-six unbound unbound-devel  python3-sphinx libunwind-devel -y

curl -OL https://www.openvswitch.org/releases/openvswitch-2.15.0.tar.gz

mkdir -p ~/rpmbuild/SOURCES

mv openvswitch-2.15.0.tar.gz /root/rpmbuild/SOURCES/

cd /root/rpmbuild/SOURCES/

tar -xvzf openvswitch-2.15.0.tar.gz

rpmbuild -bb --nocheck openvswitch-2.15.0/rhel/openvswitch.spec

yum localinstall /root/rpmbuild/RPMS/x86_64/openvswitch-2.15.0-1.x86_64.rpm -y

systemctl start openvswitch.service


systemctl enable openvswitch.service

```

### 拉取必要的镜像

```text

docker pull centos:7

docker run -itd --privileged=true --name quagga centos:7 /bin/bash 

docker exec -it quagga yum update -y

docker exec -it quagga yum install quagga net-tools vim screen -y

docker commit quagga quagga

```

### 增加网桥

```text



```
