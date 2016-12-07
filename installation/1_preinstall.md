//////Check vm.swappiness
[root@instance-1 mans_fighter45]# cat /proc/sys/vm/swappiness
10

/////Show the mount attributes of all volumes
[root@instance-1 mans_fighter45]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        10G  1.4G  8.7G  14% /
devtmpfs        6.4G     0  6.4G   0% /dev
tmpfs           6.4G     0  6.4G   0% /dev/shm
tmpfs           6.4G  8.3M  6.4G   1% /run
tmpfs           6.4G     0  6.4G   0% /sys/fs/cgroup
tmpfs           1.3G     0  1.3G   0% /run/user/1000
tmpfs           1.3G     0  1.3G   0% /run/user/0

/////Show the reserve space of any non-root, ext-based volumes
[root@instance-1 mans_fighter45]# cat /etc/fstab 
#
# /etc/fstab
# Created by anaconda on Tue Nov 29 20:27:03 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b59d6b3e-3799-4b0d-bc38-af6bc5a64151 /                       xfs     defaults,barrier=1 1 1


//////Show that transparent hugepages is disabled
[root@instance-1 mans_fighter45]# cat /sys/kernel/mm/transparent_hugepage/enabled 
[always] madvise never
[root@instance-1 mans_fighter45]# cat /sys/kernel/mm/transparent_hugepage/defrag 
[always] madvise never

///////Report the network interface attributes
[root@instance-1 mans_fighter45]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1460 qdisc mq state UP qlen 1000
    link/ether 42:01:0a:80:00:02 brd ff:ff:ff:ff:ff:ff
    inet 10.128.0.2/32 brd 10.128.0.2 scope global dynamic eth0
       valid_lft 83745sec preferred_lft 83745sec

///////Show forward and reverse host lookups using getent and nslookup
[root@instance-1 mans_fighter45]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
10.128.0.2      instance-1.c.articulate-case-151610.internal instance-1
169.254.169.254 metadata.google.internal
[root@instance-1 mans_fighter45]# nslookup hosts
Server:         169.254.169.254
Address:        169.254.169.254#53

/////Verify the nscd service is running
[root@instance-1 mans_fighter45]# sudo service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Wed 2016-12-07 04:18:59 UTC; 6s ago
  Process: 1621 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 1622 (nscd)
   CGroup: /system.slice/nscd.service
           └─1622 /usr/sbin/nscd
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring file `/etc/hosts` (4)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring directory `/etc` (2)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring file `/etc/resolv.conf` (5)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring directory `/etc` (2)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring file `/etc/services` (6)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 monitoring directory `/etc` (2)
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Dec 07 04:18:59 instance-1 nscd[1622]: 1622 Access Vector Cache (AVC) started
Dec 07 04:18:59 instance-1 systemd[1]: Started Name Service Cache Daemon.


///////Verify the ntpd service is running
[root@instance-1 mans_fighter45]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Wed 2016-12-07 03:24:06 UTC; 1h 1min ago
 Main PID: 1141 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─1141 /usr/sbin/ntpd -u ntp:ntp -g
Dec 07 03:24:06 instance-1 ntpd[1141]: Listen and drop on 1 v6wildcard :: UDP 123
Dec 07 03:24:06 instance-1 ntpd[1141]: Listen normally on 2 lo 127.0.0.1 UDP 123
Dec 07 03:24:06 instance-1 ntpd[1141]: Listen normally on 3 eth0 10.128.0.2 UDP 123
Dec 07 03:24:06 instance-1 ntpd[1141]: Listening on routing socket on fd #20 for interface updates
Dec 07 03:24:06 instance-1 ntpd[1141]: 0.0.0.0 c016 06 restart
Dec 07 03:24:06 instance-1 ntpd[1141]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Dec 07 03:24:06 instance-1 ntpd[1141]: 0.0.0.0 c011 01 freq_not_set
Dec 07 03:24:07 instance-1 ntpd[1141]: 0.0.0.0 c614 04 freq_mode
Dec 07 03:41:04 instance-1 ntpd[1141]: 0.0.0.0 0612 02 freq_set kernel 0.240 PPM
Dec 07 03:41:04 instance-1 ntpd[1141]: 0.0.0.0 0615 05 clock_sync
[root@instance-1 mans_fighter45]# 
