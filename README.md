# lenovo_issue
Issue with lenovo SR250


# Conclusions

Seems to work if installed from usb stick as "develoment machine", realtime-config, etherlab, e3..

Note: Do not have usb mouse connected in text mode since it generates latencits when it is discovered (approx each 60s)




Install new kernel:

1. remove kernel filter in /etc/yum.conf (kernel updates blocked by infra)
2. add cern rt repo

Centos 7 Install Realtime kernel using yum
Wanted to try out an rt kernel for my asterisk box. One option is to build a patched kernel.. The other option I am trying out now is to install using the Cern repo. I am using a plain Centos 7 installation and not the Cern version. At the time of writing this I had to install an older version of tuned in order to successfully finish the process: 
yum install http://ftp.ntua.gr/mirror/centos/7.2.1511/updates/x86_64/Packages/tuned-2.5.1-4.el7_2.6.noarch.rpm
Install the repo in /etc/yum.repos.d/Centos-RT.repo: 
[rt]
name=CentOS-$releasever - RealTime
baseurl=http://linuxsoft.cern.ch/cern/centos/$releasever/rt/$basearch/
gpgcheck=1
enabled=1
protect=1
priority=10
gpgkey=http://linuxsoft.cern.ch/cern/centos/7/os/x86_64/RPM-GPG-KEY-cern
Finally yum groupinstall RT should install the rt kernel. Reboot to use. I am currently trying it on a VM and so far no issues.


4. sudo yum search kernel-rt
5. sudo yum install kernel-rt...
6.  




