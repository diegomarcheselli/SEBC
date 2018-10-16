# Create a precious directory in HDFS; copy the ZIP course file into it.
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -mkdir /precious
```
Put file
```
sudo -u hdfs hdfs dfs -put /tmp/SEBC-master.zip /precious
```
# Enable snapshots for precious
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfsadmin -allowSnapshot /precious
Allowing snaphot on /precious succeeded
```

# Create a snapshot called sebc-hdfs-test
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -createSnapshot /precious sebc-hdfs-test
Created snapshot /precious/.snapshot/sebc-hdfs-test
```

# Delete the directory
Directory cannot be deleted, because it is snapshottable
```
sudo -u hdfs hdfs dfs -rm -r /precious
rm: Failed to move to trash: hdfs://ip-172-31-42-139.eu-central-1.compute.internal:8020/precious: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
```

# Delete the ZIP file
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -rm /precious/SEBC-master.zip
18/10/16 09:49:36 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-42-139.eu-central-1.compute.internal:8020/precious/SEBC-master.zip' to trash at: hdfs://ip-172-31-42-139.eu-central-1.compute.internal:8020/user/hdfs/.Trash/Current/precious/SEBC-master.zip
```
# Restore the deleted file
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -cp -ptopax /precious/.snapshot/sebc-hdfs-test/SEBC-master.zip /precious/SEBC-master.zip
```
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup    1720611 2018-10-16 09:41 /precious/SEBC-master.zip
```
