region = us-central1-c	
space = 2 vCPU, 13 GB

[mans_fighter45@instance-1 ~]$ yum repolist enabled
Loaded plugins: fastestmirror
base                                                                                     | 3.6 kB  00:00:00     
extras                                                                                   | 3.4 kB  00:00:00     
google-cloud-compute/signature                                                           |  454 B  00:00:00     
google-cloud-compute/signature                                                           | 1.4 kB  00:00:00 !!! 
google-cloud-sdk/signature                                                               |  454 B  00:00:00     
google-cloud-sdk/signature                                                               | 1.4 kB  00:00:00 !!! 
updates                                                                                  | 3.4 kB  00:00:00     
(1/6): extras/7/x86_64/primary_db                                                        | 166 kB  00:00:00     
(2/6): google-cloud-compute/primary                                                      | 1.9 kB  00:00:00     
(3/6): google-cloud-sdk/primary                                                          | 2.8 kB  00:00:00     
(4/6): base/7/x86_64/group_gz                                                            | 155 kB  00:00:00     
(5/6): updates/7/x86_64/primary_db                                                       | 9.1 MB  00:00:00     
(6/6): base/7/x86_64/primary_db                                                          | 5.3 MB  00:00:00     
Determining fastest mirrors
 * base: mirrors.gigenet.com
 * extras: mirrors.liquidweb.com
 * updates: mirror.eboundhost.com
google-cloud-compute                                                                                        4/4
google-cloud-sdk                                                                                            7/7
repo id                                              repo name                                            status
base/7/x86_64                                        CentOS-7 - Base                                      9,007
extras/7/x86_64                                      CentOS-7 - Extras                                      393
google-cloud-compute                                 Google Cloud Compute                                     4
google-cloud-sdk                                     Google Cloud SDK                                         7
updates/7/x86_64                                     CentOS-7 - Updates                                   2,560
repolist: 11,971

[root@instance-1 mans_fighter45]# cat /etc/passwd | grep raffles
raffles:x:2700:2700::/home/raffles:/bin/bash
[root@instance-1 mans_fighter45]# cat /etc/passwd | grep orchard
orchard:x:2800:2800::/home/orchard:/bin/bash
[root@instance-1 mans_fighter45]# cat /etc/group | grep shops
shops:x:2802:
[root@instance-1 mans_fighter45]# cat /etc/group | grep walks
walks:x:2801:
