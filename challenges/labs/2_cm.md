# List the command and output of ls /etc/yum.repos.d

```
ansible -i hosts cm --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'ls /etc/yum.repos.d'
ec2-35-176-168-249.eu-west-2.compute.amazonaws.com | SUCCESS | rc=0 >>
CentOS-Base.repo
CentOS-Debuginfo.repo
CentOS-fasttrack.repo
CentOS-Media.repo
CentOS-Vault.repo
cloudera-manager.repo
epel.repo
epel-testing.repo
mysql-community.repo
mysql-community-source.repo
```

# Use the scm_prepare_database.sh script to write your db.properties file

```
/usr/share/cmf/schema/scm_prepare_database.sh -h ip-172-31-22-209.eu-west-2.compute.internal mysql scm scm scm_password
JAVA_HOME=/usr/java/jdk1.8.0_131
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_131/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```
