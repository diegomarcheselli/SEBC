# The hostname of your DB node

ec2-52-56-245-5.eu-west-2.compute.amazonaws.com
ip-172-31-22-209.eu-west-2.compute.internal


# The command screenshot to display the DB version

ansible -i hosts db --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'mysql --version'
ec2-52-56-245-5.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.61, for Linux (x86_64) using readline 5.1

<img src="mysql.png">

# The command and output for listing databases

REMARK: I added also DB for Activity Monitor

Command:
```
[centos@ip-172-31-22-209 ~]$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 5
Server version: 5.5.61-log MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
```

Output:
```

+--------------------+
| Database           |
+--------------------+
| information_schema |
| amon               |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
10 rows in set (0.00 sec)

mysql>
```
