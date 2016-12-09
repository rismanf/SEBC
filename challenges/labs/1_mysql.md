mysql> select @@hostname;
+------------+
| @@hostname |
+------------+
| instance-1 |
+------------+
1 row in set (0.00 sec)

[root@instance-1 mans_fighter45]# mysql --version
mysql  Ver 14.14 Distrib 5.5.53, for Linux (x86_64) using readline 5.1

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
