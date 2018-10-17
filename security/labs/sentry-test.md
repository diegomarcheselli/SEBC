# Verify user privileges
```
[nawojka@ip-172-31-44-213 ~]$ kinit
Password for nawojka@BOOTCAMP:
[nawojka@ip-172-31-44-213 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
scan complete in 3ms
Connecting to jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017142323_9fa94666-6c87-4b4b-95e7-d9ba68f1e9cc): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142323_9fa94666-6c87-4b4b-95e7-d9ba68f1e9cc); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20181017142323_9fa94666-6c87-4b4b-95e7-d9ba68f1e9cc): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142323_9fa94666-6c87-4b4b-95e7-d9ba68f1e9cc); Time taken: 0.12 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.294 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> SHOW DATABASES;
INFO  : Compiling command(queryId=hive_20181017142525_4bd782fd-b1f0-42ff-93a9-8586b8358e9b): SHOW DATABASES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142525_4bd782fd-b1f0-42ff-93a9-8586b8358e9b); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20181017142525_4bd782fd-b1f0-42ff-93a9-8586b8358e9b): SHOW DATABASES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142525_4bd782fd-b1f0-42ff-93a9-8586b8358e9b); Time taken: 0.116 seconds
INFO  : OK
+----------------+--+
| database_name  |
+----------------+--+
| default        |
+----------------+--+
1 row selected (0.219 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> use default;
Error: Error while compiling statement: FAILED: SemanticException No valid privileges
 User nawojka does not have privileges for SWITCHDATABASE
 The required privileges: Server=server1->Db=*->Table=+->Column=*->action=select;Server=server1->Db=*->Table=+->Column=*->action=insert; (state=42000,code=40000)
```
# Create a Sentry role with full authorization
```
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017142727_2f639ecd-cbaf-4eab-bfa8-1631810c12a0): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142727_2f639ecd-cbaf-4eab-bfa8-1631810c12a0); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20181017142727_2f639ecd-cbaf-4eab-bfa8-1631810c12a0): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142727_2f639ecd-cbaf-4eab-bfa8-1631810c12a0); Time taken: 0.409 seconds
INFO  : OK
No rows affected (0.475 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017142727_14731c5b-bf67-4727-8ac9-5f52d0f7941c): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142727_14731c5b-bf67-4727-8ac9-5f52d0f7941c); Time taken: 0.092 seconds
INFO  : Executing command(queryId=hive_20181017142727_14731c5b-bf67-4727-8ac9-5f52d0f7941c): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142727_14731c5b-bf67-4727-8ac9-5f52d0f7941c); Time taken: 0.083 seconds
INFO  : OK
No rows affected (0.191 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT ROLE sentry_admin TO GROUP nawojka;
INFO  : Compiling command(queryId=hive_20181017142727_c5c59fee-1375-4826-ada7-10fadbdadbf0): GRANT ROLE sentry_admin TO GROUP nawojka
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142727_c5c59fee-1375-4826-ada7-10fadbdadbf0); Time taken: 0.073 seconds
INFO  : Executing command(queryId=hive_20181017142727_c5c59fee-1375-4826-ada7-10fadbdadbf0): GRANT ROLE sentry_admin TO GROUP nawojka
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142727_c5c59fee-1375-4826-ada7-10fadbdadbf0); Time taken: 0.071 seconds
INFO  : OK
No rows affected (0.157 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017142828_2037c629-4812-4610-bc39-a699b4353c50): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017142828_2037c629-4812-4610-bc39-a699b4353c50); Time taken: 0.072 seconds
INFO  : Executing command(queryId=hive_20181017142828_2037c629-4812-4610-bc39-a699b4353c50): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017142828_2037c629-4812-4610-bc39-a699b4353c50); Time taken: 0.121 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.21 seconds)
```
# Create additional test users
Ansible to create users:
```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'groupadd selector'
```
```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'groupadd inserters'
```
```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'useradd -u 1100 -g selector george'\n
```
```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'useradd -u 1200 -g inserters ferdinand'\n
```
kadmin.local:
```
[root@ip-172-31-44-213 ~]# kadmin.local
Authenticating as principal cloudera-scm/admin@BOOTCAMP with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@BOOTCAMP; defaulting to no policy
Enter password for principal "george@BOOTCAMP":
Re-enter password for principal "george@BOOTCAMP":
Principal "george@BOOTCAMP" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@BOOTCAMP; defaulting to no policy
Enter password for principal "ferdinand@BOOTCAMP":
Re-enter password for principal "ferdinand@BOOTCAMP":
Principal "ferdinand@BOOTCAMP" created.
kadmin.local:  exit
```
# Create test roles
```
[nawojka@ip-172-31-44-213 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20181017143232_1589be5e-d252-4b8b-8516-6c07f0ed5531): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143232_1589be5e-d252-4b8b-8516-6c07f0ed5531); Time taken: 0.069 seconds
INFO  : Executing command(queryId=hive_20181017143232_1589be5e-d252-4b8b-8516-6c07f0ed5531): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143232_1589be5e-d252-4b8b-8516-6c07f0ed5531); Time taken: 0.022 seconds
INFO  : OK
No rows affected (0.152 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20181017143232_ffc4113a-2a94-436b-a706-aef30c4112d2): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143232_ffc4113a-2a94-436b-a706-aef30c4112d2); Time taken: 0.05 seconds
INFO  : Executing command(queryId=hive_20181017143232_ffc4113a-2a94-436b-a706-aef30c4112d2): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143232_ffc4113a-2a94-436b-a706-aef30c4112d2); Time taken: 0.025 seconds
INFO  : OK
No rows affected (0.087 seconds)
```
# Grant read privilege for all tables to 'reads'
```
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20181017143232_7bd27e30-6e31-49d9-9a42-74063aa3b08e): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143232_7bd27e30-6e31-49d9-9a42-74063aa3b08e); Time taken: 0.045 seconds
INFO  : Executing command(queryId=hive_20181017143232_7bd27e30-6e31-49d9-9a42-74063aa3b08e): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143232_7bd27e30-6e31-49d9-9a42-74063aa3b08e); Time taken: 0.021 seconds
INFO  : OK
No rows affected (0.076 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20181017143232_2f9de8c8-b914-403c-b7b8-c6879993699c): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143232_2f9de8c8-b914-403c-b7b8-c6879993699c); Time taken: 0.044 seconds
INFO  : Executing command(queryId=hive_20181017143232_2f9de8c8-b914-403c-b7b8-c6879993699c): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143232_2f9de8c8-b914-403c-b7b8-c6879993699c); Time taken: 0.048 seconds
INFO  : OK
No rows affected (0.1 seconds)
```
# Grant read privilege for default.sample07 only to 'writes'
```
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20181017143333_1c1fbb31-3f52-45e3-8c3d-12bde9da567a): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143333_1c1fbb31-3f52-45e3-8c3d-12bde9da567a); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20181017143333_1c1fbb31-3f52-45e3-8c3d-12bde9da567a): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143333_1c1fbb31-3f52-45e3-8c3d-12bde9da567a); Time taken: 0.071 seconds
INFO  : OK
No rows affected (0.135 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20181017143333_25174ff3-0572-4b2f-ac91-60d9d3a943e3): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143333_25174ff3-0572-4b2f-ac91-60d9d3a943e3); Time taken: 0.045 seconds
INFO  : Executing command(queryId=hive_20181017143333_25174ff3-0572-4b2f-ac91-60d9d3a943e3): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143333_25174ff3-0572-4b2f-ac91-60d9d3a943e3); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0.085 seconds)
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20181017143333_19e795b7-6a96-49a6-a22e-84d7ed3cfdb4): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143333_19e795b7-6a96-49a6-a22e-84d7ed3cfdb4); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20181017143333_19e795b7-6a96-49a6-a22e-84d7ed3cfdb4): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143333_19e795b7-6a96-49a6-a22e-84d7ed3cfdb4); Time taken: 0.022 seconds
INFO  : OK
No rows affected (0.079 seconds)
```
# kinit as george, then login to beeline
George:
```
[root@ip-172-31-44-213 ~]# su - george
[george@ip-172-31-44-213 ~]$ kinit
Password for george@BOOTCAMP:
[george@ip-172-31-44-213 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017143838_0bb3ac68-dce8-4b45-b67f-77b05e3146f9): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017143838_0bb3ac68-dce8-4b45-b67f-77b05e3146f9); Time taken: 0.057 seconds
INFO  : Executing command(queryId=hive_20181017143838_0bb3ac68-dce8-4b45-b67f-77b05e3146f9): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017143838_0bb3ac68-dce8-4b45-b67f-77b05e3146f9); Time taken: 0.136 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.281 seconds)
```
Ferdinand:
```
[root@ip-172-31-44-213 ~]# su - ferdinand
[ferdinand@ip-172-31-44-213 ~]$ kinit
Password for ferdinand@BOOTCAMP:
[ferdinand@ip-172-31-44-213 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-39-67.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-39-67.eu-central-1.compute.internal@BOOTCAMP
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-39-67.eu-central-1.> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017144040_52889ed8-ad22-442d-9159-999080d9bc4e): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017144040_52889ed8-ad22-442d-9159-999080d9bc4e); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20181017144040_52889ed8-ad22-442d-9159-999080d9bc4e): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017144040_52889ed8-ad22-442d-9159-999080d9bc4e); Time taken: 0.105 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.247 seconds)
```
