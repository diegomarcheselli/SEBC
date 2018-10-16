# Adjusted values:

According to the source: https://community.cloudera.com/t5/Cloudera-Manager-Installation/Memory/td-p/30571 (and calculation I did on the production cluster in the past) Cloudera Manager reserves 20% of RAM for the OS, so I adjusted value of formula in B7 to:
```
=PRODUCT(0,2;B3)
```

# Workload factor

Workload factor affects the number of map and reduce jobs that are run on the node.
Workload factor of 1 means that only one map and one reduce tasks is executed on the node (and we have 10 nodes so the value is set to 10)
Workload 2 means that two map and reduce tasks can be run on the node, but the value of vcores that can be assign to YARN on every node limits it to 15.
Setting Workload Factor to more than two won't change the values.
