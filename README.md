rac_on_xx
====
Oracle RAC on Docker /systemd-nspawn /Azure /EC2 /GCE 

- [docker](https://github.com/s4ragent/rac_on_xx/tree/master/docker "RAC on Docker")  Oracle RAC on docker 
- [nspawn](https://github.com/s4ragent/rac_on_xx/tree/master/nspawn "RAC on Docker")  Oracle RAC on systemd-nspawn 
- [Microsoft Azure](https://github.com/s4ragent/rac_on_xx/tree/master/azure "RAC on Azure")  Oracle RAC on Azure
- [Amazon EC2](https://github.com/s4ragent/rac_on_xx/tree/master/ec2 "RAC on EC2")  Oracle RAC on EC2
- [Google Compute Cloud](https://github.com/s4ragent/rac_on_xx/tree/master/gce "RAC on GCE")  Oracle RAC on GCE


## Description
- basic infomation

|||
|-----|-----|
|OS|Oracle Linux 7.x|
|Storage|NFS4 with Flex ASM|
|L2 Network emulation|vxlan|
|DNS|dnsmasq on each instance|

- Network infomation (e.g. 3-nodes RAC)

|hostname/instance name/vip|eth0|vxlan0(public)|vxlan1(internal)|vxlan2(asm)|
|--------|--------|-------|-------|-------|
|storage|10.xx.xx.xx|-|-|-|
|node001|10.xx.xx.xx|192.168.0.51|192.168.100.51|192.168.200.51|
|node002|10.xx.xx.xx|192.168.0.52|192.168.100.52|192.168.200.52|
|node003|10.xx.xx.xx|192.168.0.53|192.168.100.53|192.168.200.53|
|node001.vip|-|192.168.0.151|-|-|
|node002.vip|-|192.168.0.152|-|-|
|node003.vip|-|192.168.0.152|-|-|
|scan1.vip|-|192.168.0.31|-|-|
|scan2.vip|-|192.168.0.32|-|-|
|scan3.vip|-|192.168.0.33|-|-|


- Storage infomation 

|Diskgroup name|use|asm device path|redundancy|size(GB)|size(GB)(e.g. 3-nodes RAC)|
|--------|--------|-------|-------|-------|-------|
|VOTE|ocr and voting disk|/u01/oradata/vote.img|external| 40960 + ( num_of_nodes * 2048 )|47104|
|DATA|Database files|/u01/oradata/data.img|external| 5120 + ( num_of_nodes * 1024 ) |8192|
|FRA|flash recovery area|/u01/oradata/fra.img|external|25600|25600|

## Demo (12-nodes RAC on ubuntu docker)
![crsctl](https://github.com/s4ragent/misc/blob/master/rac_on_xx/docker/docker01.png)
![crsctl](https://github.com/s4ragent/misc/blob/master/rac_on_xx/docker/docker02.png)
![crsctl](https://github.com/s4ragent/misc/blob/master/rac_on_xx/docker/docker03.png)
![crsctl](https://github.com/s4ragent/misc/blob/master/rac_on_xx/docker/docker04.png)


## Licence
MIT

## Author
@s4r_agent
