I will use Ansible to execute commands on the remote VMs.

# 1. vm.swappiness
First the vm.swappiness is set to 60:
```
ansible -i hosts all -c paramiko -m shell -a 'cat /proc/sys/vm/swappiness'

ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
60
```
Run command to change (as root):
```
ansible -i hosts all --become -c paramiko -m shell -a 'sysctl -w vm.swappiness=1'

ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
vm.swappiness = 1
```

After the change:
```
ansible -i hosts all -c paramiko -m shell -a 'cat /proc/sys/vm/swappiness'

ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
1
```

# 2. Mount attributes
```
ansible -i hosts all --become -c paramiko -m shell -a 'mount -l'

ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'cat /etc/fstab'
ec2-18-194-208-128.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>

#
# /etc/fstab
# Created by anaconda on Tue Jun  5 13:56:10 2018
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=c64c61c1-9e9b-4f2e-912d-d81ce4c3b716 /                       ext4    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
```
# 3. Show the reserve space of any non-root, ext-based volumes
```
ansible -i hosts all  --become -c paramiko -m shell -a 'lsblk'
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  8G  0 part /
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'df -h'
ec2-35-158-75-43.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      7.8G  752M  6.7G  10% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
```
The AWS settings were supposed to add 30GB, but it is not configured on the partition.
The workaround for this problem is to install growpart utils and resize root partition:

```
ansible -i hosts all --become -c paramiko -m shell -a 'yum install -y epel-release'

ansible -i hosts all --become -c paramiko -m shell -a 'yum -y install cloud-utils-growpart'
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'growpart /dev/xvda 1'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
CHANGED: partition=1 start=2048 old: size=16775168 end=16777216 new: size=62908492,end=62910540
```
and reboot the VMs.
```
ansible -i hosts all  --become -c paramiko -m shell -a 'yum install -y epel-release'
```
Run df -h again:
```
ansible -i hosts all --become -c paramiko -m shell -a 'df -h'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G  819M   28G   3% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
```
```
ansible -i hosts all  --become -c paramiko -m shell -a 'lsblk'
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  30G  0 disk
└─xvda1 202:1    0  8G  0 part /
```

# 4. Disable transparent hugepage support
By default transparent hugepage support was enabled
```
ansible -i hosts all --become  -c paramiko -m shell -a 'cat /sys/kernel/mm/redhat_transparent_hugepage/defrag'
ec2-35-158-75-43.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
[always] madvise never
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'cat /sys/kernel/mm/redhat_transparent_hugepage/enabled'
ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
[always] madvise never
```
To diasble:
```
ansible -i hosts all  --become -c paramiko -m shell -a 'echo never > /sys/kernel/mm/redhat_transparent_hugepage/defrag'
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
```
```
ansible -i hosts all  --become -c paramiko -m shell -a 'echo never > /sys/kernel/mm/redhat_transparent_hugepage/enabled'
ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
```
Check:
```
ansible -i hosts all  --become -c paramiko -m shell -a 'cat /sys/kernel/mm/redhat_transparent_hugepage/defrag'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
always madvise [never]
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'cat /sys/kernel/mm/redhat_transparent_hugepage/enabled'
ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
always madvise [never]
```
# 5. List your network interface configuration
```
ansible -i hosts all --become -c paramiko -m shell -a 'ifconfig'
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
eth0      Link encap:Ethernet  HWaddr 06:AA:A3:3B:92:FE
          inet addr:172.31.44.213  Bcast:172.31.47.255  Mask:255.255.240.0
          inet6 addr: fe80::4aa:a3ff:fe3b:92fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:1220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:809520 (790.5 KiB)  TX bytes:122985 (120.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
# 6.
nslookup tool is not installed on CentOS server. To install:
```
ansible -i hosts all --become -c paramiko -m shell -a 'sudo yum install -y bind-utils'
```
Public DNS name of another AWS instance:
```
ansible -i hosts all --become -c paramiko -m shell -a 'nslookup ec2-18-194-208-128.eu-central-1.compute.amazonaws.com'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Server:		172.31.0.2
Address:	172.31.0.2#53
```
Public IP addess of another AWS instace:
```
ansible -i hosts all --become -c paramiko -m shell -a 'nslookup 18.194.208.128'
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
128.208.194.18.in-addr.arpa	name = ec2-18-194-208-128.eu-central-1.compute.amazonaws.com.
```

Google.com
```
ansible -i hosts all --become -c paramiko -m shell -a 'nslookup google.com'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.22.110
```

# 7. Show the nscd service is running
nscd is not installed by default on CentOS 6.
To install and configure:
```
ansible -i hosts all --become -c paramiko -m shell -a 'yum -y install nscd'
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'service nscd start'
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'chkconfig nscd on'
```
Check if running:
```
ansible -i hosts all --become -c paramiko -m shell -a 'service nscd status'

ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
nscd (pid 3646) is running...
```
To test:
```
ansible -i hosts all --become -c paramiko -m shell -a 'nscd -g'
ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
nscd configuration:

              0  server debug level
         1m 27s  server runtime
              5  current number of threads
             32  maximum number of threads
              0  number of times clients had to wait
             no  paranoia mode enabled
           3600  restart internal
              5  reload count

passwd cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
            544  used data pool size
            600  seconds time to live for positive entries
             20  seconds time to live for negative entries
             53  cache hits on positive entries
              0  cache hits on negative entries
              3  cache misses on positive entries
              0  cache misses on negative entries
             94% cache hit rate
              6  current number of cached values
              6  maximum number of cached values
              1  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/passwd for changes

group cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
            432  used data pool size
           3600  seconds time to live for positive entries
             60  seconds time to live for negative entries
             10  cache hits on positive entries
              0  cache hits on negative entries
              3  cache misses on positive entries
              1  cache misses on negative entries
             71% cache hit rate
              6  current number of cached values
              6  maximum number of cached values
              2  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/group for changes

hosts cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
           3600  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/hosts for changes

services cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/services for changes

netgroup cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/netgroup for changes

SELinux AVC Statistics:

            120  entry lookups
            101  entry hits
             19  entry misses
             18  entry discards
             19  CAV lookups
             15  CAV hits
             15  CAV probes
              4  CAV misses
```
```
ansible -i hosts all --become -c paramiko -m shell -a 'time nslookup www.google.com'
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	www.google.com
Address: 216.58.214.100
real	0m0.015s
user	0m0.002s
sys	0m0.013s
```

# 8. Show the ntpd service is running
For AWS Amazon Time Sync Service can be used (chronyd instead of ntpd). Steps are desribed here:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html
Chrony running:
```
ansible -i hosts all --become -c paramiko -m shell -a 'service chronyd status'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than running sudo

ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
chronyd (pid  3154) is running...
```
Chrony sources:
```
ansible -i hosts all --become -c paramiko -m shell -a 'chronyc sources -v'
ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
210 Number of sources = 1

  .-- Source mode  '^' = server, '=' = peer, '#' = local clock.
 / .- Source state '*' = current synced, '+' = combined , '-' = not combined,
| /   '?' = unreachable, 'x' = time may be in error, '~' = time too variable.
||                                                 .- xxxx [ yyyy ] +/- zzzz
||      Reachability register (octal) -.           |  xxxx = adjusted offset,
||      Log2(Polling interval) --.      |          |  yyyy = measured offset,
||                                \     |          |  zzzz = estimated error.
||                                 |    |           \
MS Name/IP address         Stratum Poll Reach LastRx Last sample
===============================================================================
^* 169.254.169.123               3   6    17    31     -0ns[  -72us] +/-   44ms
```
Chrony tracking:
```
ansible -i hosts all --become -c paramiko -m shell -a 'chronyc tracking'
ec2-35-158-75-43.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
Reference ID    : 169.254.169.123 (169.254.169.123)
Stratum         : 4
Ref time (UTC)  : Mon Oct 15 13:15:25 2018
System time     : 0.000000000 seconds fast of NTP time
Last offset     : +0.000061000 seconds
RMS offset      : 0.000061000 seconds
Frequency       : 5.098 ppm fast
Residual freq   : +0.000 ppm
Skew            : 1.000 ppm
Root delay      : 0.000536 seconds
Root dispersion : 0.000515 seconds
Update interval : 65.1 seconds
Leap status     : Normal
```
