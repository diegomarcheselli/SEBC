# Cloud provider

AWS

Hosts:
```
ec2-52-56-245-5.eu-west-2.compute.amazonaws.com
ec2-35-176-168-249.eu-west-2.compute.amazonaws.com
ec2-35-176-114-62.eu-west-2.compute.amazonaws.com
ec2-3-8-29-171.eu-west-2.compute.amazonaws.com
ec2-18-130-208-208.eu-west-2.compute.amazonaws.com
```

# Linux release

CentOS 6.9

```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'cat /etc/redhat-release'
```
```
ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS release 6.9 (Final)

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS release 6.9 (Final)

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS release 6.9 (Final)

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS release 6.9 (Final)

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS release 6.9 (Final)
```

# Disk space

ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'df -h'
ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G 1012M   27G   4% /
tmpfs           7.8G     0  7.8G   0% /dev/shm

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G 1012M   27G   4% /
tmpfs           7.8G     0  7.8G   0% /dev/shm

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G 1012M   27G   4% /
tmpfs           7.8G     0  7.8G   0% /dev/shm

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G 1012M   27G   4% /
tmpfs           7.8G     0  7.8G   0% /dev/shm

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G 1012M   27G   4% /
tmpfs           7.8G     0  7.8G   0% /dev/shm


ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'lsblk'
ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  30G  0 part /

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  30G  0 part /

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  30G  0 part /

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  30G  0 part /

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  30G  0 part /



# yum repolist enabled

ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'yum repolist enabled'
 [WARNING]: Consider using yum module rather than running yum

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: centos.serverspace.co.uk
 * epel: mirrors.coreix.net
 * extras: centos.serverspace.co.uk
 * updates: centos.serverspace.co.uk
repo id          repo name                                               status
base             CentOS-6 - Base                                         6,712+1
epel             Extra Packages for Enterprise Linux 6 - x86_64           12,515
extras           CentOS-6 - Extras                                         21+12
updates          CentOS-6 - Updates                                          205
repolist: 19,453

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: centos.serverspace.co.uk
 * epel: d2lzkl7pfhq30w.cloudfront.net
 * extras: centos.serverspace.co.uk
 * updates: centos.serverspace.co.uk
repo id          repo name                                               status
base             CentOS-6 - Base                                         6,712+1
epel             Extra Packages for Enterprise Linux 6 - x86_64           12,515
extras           CentOS-6 - Extras                                         21+12
updates          CentOS-6 - Updates                                          205
repolist: 19,453

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.vorboss.net
 * epel: d2lzkl7pfhq30w.cloudfront.net
 * extras: mirror.vorboss.net
 * updates: centos.serverspace.co.uk
repo id          repo name                                               status
base             CentOS-6 - Base                                         6,712+1
epel             Extra Packages for Enterprise Linux 6 - x86_64           12,515
extras           CentOS-6 - Extras                                         21+12
updates          CentOS-6 - Updates                                          205
repolist: 19,453

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.vorboss.net
 * epel: mirror.vorboss.net
 * extras: mirror.vorboss.net
 * updates: mirrors.clouvider.net
repo id          repo name                                               status
base             CentOS-6 - Base                                         6,712+1
epel             Extra Packages for Enterprise Linux 6 - x86_64           12,515
extras           CentOS-6 - Extras                                         21+12
updates          CentOS-6 - Updates                                          205
repolist: 19,453

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: centos.serverspace.co.uk
 * epel: mirrors.coreix.net
 * extras: centos.serverspace.co.uk
 * updates: mirrors.clouvider.net
repo id          repo name                                               status
base             CentOS-6 - Base                                         6,712+1
epel             Extra Packages for Enterprise Linux 6 - x86_64           12,515
extras           CentOS-6 - Extras                                         21+12
updates          CentOS-6 - Updates                                          205
repolist: 19,453

# List /etc/passwd

ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'cat /etc/passwd | grep raffles'
ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash




ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'cat /etc/passwd | grep fullerton'
ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash



# List /etc/group

ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'cat /etc/group | grep hotels'
ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
hotels:x:3001:fullerton

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
hotels:x:3001:fullerton

ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
hotels:x:3001:fullerton

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
hotels:x:3001:fullerton

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
hotels:x:3001:fullerton



ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'cat /etc/group | grep shops'
ec2-3-8-29-171.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
shops:x:3002:raffles

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
shops:x:3002:raffles

ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
shops:x:3002:raffles

ec2-18-130-208-208.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
shops:x:3002:raffles

ec2-35-176-114-62.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
shops:x:3002:raffles
