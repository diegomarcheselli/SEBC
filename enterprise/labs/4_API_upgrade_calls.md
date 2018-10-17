# Report the latest available version of the API
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/version'
```
```json
v14%
```
# Report the CM version
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v14/cm/version'
```
```json
{
  "version" : "5.9.3",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170627-1506",
  "gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
  "snapshot" : false
}%
```

# List all CM users
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v14/users'
```
```json
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "nawojka",
    "roles" : [ "ROLE_ADMIN" ]
  } ]
}%
```

# Report the database server in use by CM
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v14/cm/deployment' | grep -A 2 database_host
```
```
"name" : "database_host",
"value" : "ip-172-31-44-213.eu-central-1.compute.internal",
```
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v14/cm/scmDbInfo'
```
```json
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}%
```
