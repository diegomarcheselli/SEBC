# Status of Hive before lab
Command:
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/'
```
Output:
```json
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
}%
```
# Stop Hive
Command:
```
curl -XPOST -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/commands/stop'
```
```json
{
  "id" : 900,
  "name" : "Stop",
  "startTime" : "2018-10-17T07:39:50.845Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}%
```
Status after stopping:
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/'
```
```json
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STOPPED",
  "healthSummary" : "DISABLED",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "STOPPED"
}%
```
# Start Hive
Command:
```
curl -XPOST -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/commands/start'
```
```json
{
  "id" : 904,
  "name" : "Start",
  "startTime" : "2018-10-17T07:45:57.787Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}%
```
Status after starting:
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/clusters/nawojka/services/hive/'
```
```json
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-44-213.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
}%
```
