# Command and output for hdfs dfs -ls /user

```
[root@ip-172-31-22-209 ~]# sudo -u hdfs hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - fullerton fullerton          0 2018-10-19 08:29 /user/fullerton
drwxrwxrwx   - mapred    hadoop             0 2018-10-19 08:23 /user/history
drwxrwxr-t   - hive      hive               0 2018-10-19 08:24 /user/hive
drwxrwxr-x   - hue       hue                0 2018-10-19 08:25 /user/hue
drwxrwxr-x   - oozie     oozie              0 2018-10-19 08:25 /user/oozie
drwxr-xr-x   - raffles   raffles            0 2018-10-19 08:28 /user/raffles
```

# The output from the CM API call ../api/v14/hosts

```
curl -u admin:admin 'http://ec2-35-176-168-249.eu-west-2.compute.amazonaws.com:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "56e11d66-2792-46aa-8c68-fb9c1c7186e6",
    "ipAddress" : "172.31.19.169",
    "hostname" : "ip-172-31-19-169.eu-west-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-28-212.eu-west-2.compute.internal:7180/cmf/hostRedirect/56e11d66-2792-46aa-8c68-fb9c1c7186e6",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722391040
  }, {
    "hostId" : "ca4a06fa-e417-405c-adca-d1a5b2cf35e8",
    "ipAddress" : "172.31.21.204",
    "hostname" : "ip-172-31-21-204.eu-west-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-28-212.eu-west-2.compute.internal:7180/cmf/hostRedirect/ca4a06fa-e417-405c-adca-d1a5b2cf35e8",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722391040
  }, {
    "hostId" : "afba030b-b4c7-454f-95ec-37460b18a4aa",
    "ipAddress" : "172.31.22.209",
    "hostname" : "ip-172-31-22-209.eu-west-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-28-212.eu-west-2.compute.internal:7180/cmf/hostRedirect/afba030b-b4c7-454f-95ec-37460b18a4aa",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722391040
  }, {
    "hostId" : "2b1c680d-4713-4821-9737-0a54e48d9683",
    "ipAddress" : "172.31.28.212",
    "hostname" : "ip-172-31-28-212.eu-west-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-28-212.eu-west-2.compute.internal:7180/cmf/hostRedirect/2b1c680d-4713-4821-9737-0a54e48d9683",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722391040
  }, {
    "hostId" : "17fa0fd0-1c08-4c42-b5d6-0cddc6e33935",
    "ipAddress" : "172.31.31.164",
    "hostname" : "ip-172-31-31-164.eu-west-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-28-212.eu-west-2.compute.internal:7180/cmf/hostRedirect/17fa0fd0-1c08-4c42-b5d6-0cddc6e33935",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722391040
  } ]
}%
```
