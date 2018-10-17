Command:
```
curl -u nawojka:password 'ec2-18-196-113-149.eu-central-1.compute.amazonaws.com:7180/api/v12/cm/deployment' 
```
Output:
```json
{
  "timestamp" : "2018-10-17T07:26:37.308Z",
  "clusters" : [ {
    "name" : "cluster",
    "displayName" : "nawojka",
    "version" : "CDH5",
    "fullVersion" : "5.8.5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "12uc4w66lur1yp0bjt83vp2z2"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bhlhq2dobv2r3qr5r0rayolqi"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-f01e4d4e63716ee01efbc2dd4bd0cda7",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-06be7daedd16a4a4e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2io4qae11q9jqota123h9qzhn"
          }, {
            "name" : "serverId",
            "value" : "4"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      } ],
      "displayName" : "ZooKeeper",
      "roleConfigGroups" : [ {
        "name" : "zookeeper-SERVER-BASE",
        "displayName" : "Server Default Group",
        "roleType" : "SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "zookeeper"
        },
        "config" : {
          "items" : [ ]
        }
      } ]
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "50ci7m5qfoqrwatcwzo5ugd11"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "oozie-OOZIE_SERVER-BASE"
        }
      } ],
      "displayName" : "Oozie",
      "roleConfigGroups" : [ {
        "name" : "oozie-OOZIE_SERVER-BASE",
        "displayName" : "Oozie Server Default Group",
        "roleType" : "OOZIE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "oozie"
        },
        "config" : {
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-44-213.eu-central-1.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie_password"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        }
      } ]
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-44-213.eu-central-1.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "hue_password"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-aa6a2bf54191b76667f2b30358bbba07"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-fc5bfa949e43698273f7319bb121d6d2",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-00ef27a3e32bc603a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3ttagnudpnx08qewjif40byyt"
          }, {
            "name" : "secret_key",
            "value" : "WhzlPMnTaCp58ugXhkvdGzP9PfF3DD"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hue-HUE_SERVER-BASE"
        }
      } ],
      "displayName" : "Hue",
      "roleConfigGroups" : [ {
        "name" : "hue-HUE_LOAD_BALANCER-BASE",
        "displayName" : "Load Balancer Default Group",
        "roleType" : "HUE_LOAD_BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-HUE_SERVER-BASE",
        "displayName" : "Hue Server Default Group",
        "roleType" : "HUE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-KT_RENEWER-BASE",
        "displayName" : "Kerberos Ticket Renewer Default Group",
        "roleType" : "KT_RENEWER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      } ]
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "knjBtmDm43MqSoObbCJHvXqDgoEDKx"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "UcILXOKMNMDSDJ00kVSuZqd2avebvt"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "Bv1H3X2O72rWVAqFWeLUFoxJUryOIe"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-fc5bfa949e43698273f7319bb121d6d2",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "i-00ef27a3e32bc603a"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-BALANCER-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "282rpdjqletkhmy39lbtpo1lc"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "31g2h7ei15ywqjpr4xnl2m2lf"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-2"
        }
      }, {
        "name" : "hdfs-DATANODE-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "98dae0n2w9x912r1w5nicf4tt"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-f01e4d4e63716ee01efbc2dd4bd0cda7",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-06be7daedd16a4a4e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cysxjn7xlfg416rh8qcsrg1xf"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3qb7rqwtu9w5kzrrinbofejjh"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5y1qlxohaq1gh7qudzl0j7op9"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-HTTPFS-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9leg4qx49wxl1dbldppzexsph"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-HTTPFS-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7e8dwc28b98nywhex5u2628q8"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5vsuqm2yef0j86cb4m7grkqpl"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-fc5bfa949e43698273f7319bb121d6d2",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-00ef27a3e32bc603a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6z2m2uk02jqhr1q1zvmm7n1fn"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "48"
          }, {
            "name" : "role_jceks_password",
            "value" : "c9pluodie4lgqhloftobzjcqg"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "63"
          }, {
            "name" : "role_jceks_password",
            "value" : "es9melpboro5shjwtvo95c860"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      } ],
      "displayName" : "HDFS",
      "roleConfigGroups" : [ {
        "name" : "hdfs-BALANCER-BASE",
        "displayName" : "Balancer Default Group",
        "roleType" : "BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-1",
        "displayName" : "DataNode Group 1",
        "roleType" : "DATANODE",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "3156951040"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-2",
        "displayName" : "DataNode Group 2",
        "roleType" : "DATANODE",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "3156951040"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-BASE",
        "displayName" : "DataNode Default Group",
        "roleType" : "DATANODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "3156951040"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-BASE",
        "displayName" : "Failover Controller Default Group",
        "roleType" : "FAILOVERCONTROLLER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-BASE",
        "displayName" : "HttpFS Default Group",
        "roleType" : "HTTPFS",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-BASE",
        "displayName" : "JournalNode Default Group",
        "roleType" : "JOURNALNODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-BASE",
        "displayName" : "NameNode Default Group",
        "roleType" : "NAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "1766850560"
          }, {
            "name" : "role_config_suppression_namenode_java_heapsize_minimum_validator",
            "value" : "true"
          } ]
        }
      }, {
        "name" : "hdfs-NFSGATEWAY-BASE",
        "displayName" : "NFS Gateway Default Group",
        "roleType" : "NFSGATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-BASE",
        "displayName" : "SecondaryNameNode Default Group",
        "roleType" : "SECONDARYNAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "1766850560"
          } ]
        }
      } ],
      "replicationSchedules" : [ {
        "id" : 3,
        "startTime" : "2018-10-16T08:58:17.001Z",
        "interval" : 0,
        "intervalUnit" : "MINUTE",
        "paused" : false,
        "nextRun" : null,
        "alertOnStart" : false,
        "alertOnSuccess" : false,
        "alertOnFail" : false,
        "alertOnAbort" : false,
        "hdfsArguments" : {
          "sourceService" : {
            "peerName" : "olgierdg",
            "clusterName" : "cluster",
            "serviceName" : "hdfs"
          },
          "sourcePath" : "/tmp/olgierdg",
          "destinationPath" : "/olgierd_bdr",
          "mapreduceServiceName" : "yarn",
          "dryRun" : false,
          "abortOnError" : false,
          "removeMissingFiles" : false,
          "preserveReplicationCount" : true,
          "preserveBlockSize" : true,
          "preservePermissions" : true,
          "skipChecksumChecks" : false,
          "skipTrash" : false,
          "replicationStrategy" : "DYNAMIC",
          "preserveXAttrs" : false,
          "exclusionFilters" : [ ]
        },
        "active" : false
      } ],
      "snapshotPolicies" : [ ]
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "true"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "true"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "QtS20rOPYC6RkBBdQJIFLGOa0Be4KW"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4jzl0pvo34adtts202ug2i4fx"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-JOBHISTORY-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eiy4g6k4f3kdc94raf9f4dscr"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ibycsdng0k36w00htb39h7ng"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-2"
        }
      }, {
        "name" : "yarn-NODEMANAGER-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "trlpi42iaz680fom7kqgmpz"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-f01e4d4e63716ee01efbc2dd4bd0cda7",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-06be7daedd16a4a4e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4ykkccavnxm0mnt7hf59va6cl"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "55"
          }, {
            "name" : "role_jceks_password",
            "value" : "84h3jjjtvuam422vw4q8ryhmy"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-RESOURCEMANAGER-BASE"
        }
      } ],
      "displayName" : "YARN (MR2 Included)",
      "roleConfigGroups" : [ {
        "name" : "yarn-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "yarn-JOBHISTORY-BASE",
        "displayName" : "JobHistory Server Default Group",
        "roleType" : "JOBHISTORY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1",
        "displayName" : "NodeManager Group 1",
        "roleType" : "NODEMANAGER",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "2415"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-2",
        "displayName" : "NodeManager Group 2",
        "roleType" : "NODEMANAGER",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "1340"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-BASE",
        "displayName" : "NodeManager Default Group",
        "roleType" : "NODEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "2048"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-BASE",
        "displayName" : "ResourceManager Default Group",
        "roleType" : "RESOURCEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "2415"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        }
      } ]
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-44-213.eu-central-1.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive_password"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-a5f92759ba5f75f1ca6c26fc5c1cb921",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-040e8e730263aea44"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-f01e4d4e63716ee01efbc2dd4bd0cda7",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-06be7daedd16a4a4e"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-fc5bfa949e43698273f7319bb121d6d2",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-00ef27a3e32bc603a"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-HIVEMETASTORE-83544d7a66ca4bf1ea6b639ef9170f38",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-018f266462a585e76"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6n88tsmjmdf3k8z4ds6qa3f9z"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVEMETASTORE-BASE"
        }
      }, {
        "name" : "hive-HIVESERVER2-aa6a2bf54191b76667f2b30358bbba07",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-01a47b593cce06ba1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "d36g4a31qkosleaajrspc9a1q"
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVESERVER2-BASE"
        }
      } ],
      "displayName" : "Hive",
      "roleConfigGroups" : [ {
        "name" : "hive-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-BASE",
        "displayName" : "Hive Metastore Server Default Group",
        "roleType" : "HIVEMETASTORE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "1766850560"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-BASE",
        "displayName" : "HiveServer2 Default Group",
        "roleType" : "HIVESERVER2",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "1766850560"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "1952815513"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "328"
          } ]
        }
      }, {
        "name" : "hive-WEBHCAT-BASE",
        "displayName" : "WebHCat Server Default Group",
        "roleType" : "WEBHCAT",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      } ],
      "replicationSchedules" : [ ]
    } ],
    "parcels" : [ {
      "product" : "CDH",
      "version" : "5.8.5-1.cdh5.8.5.p0.5",
      "stage" : "DISTRIBUTED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    }, {
      "product" : "CDH",
      "version" : "5.8.5-1.cdh5.8.5.p0.5",
      "stage" : "ACTIVATED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "i-06be7daedd16a4a4e",
    "ipAddress" : "172.31.32.239",
    "hostname" : "ip-172-31-32-239.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-040e8e730263aea44",
    "ipAddress" : "172.31.33.143",
    "hostname" : "ip-172-31-33-143.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-01a47b593cce06ba1",
    "ipAddress" : "172.31.39.67",
    "hostname" : "ip-172-31-39-67.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-018f266462a585e76",
    "ipAddress" : "172.31.42.139",
    "hostname" : "ip-172-31-42-139.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-00ef27a3e32bc603a",
    "ipAddress" : "172.31.44.213",
    "hostname" : "ip-172-31-44-213.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__2fddee72-479a-437e-8915-a5027ab74e36",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "3543efa03ff4f233aa1e12ed4ff8493792955442ee6ac25d714b3d67cdec1a1e",
    "pwSalt" : -2000061876254553643,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-f01e4d4e63716ee01efbc2dd4bd0cda7",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "631eec38b38d075fb332ff0c455597517cb1072c30bc0bddde3c04e3df1ce033",
    "pwSalt" : 5072782183151701817,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-fc5bfa949e43698273f7319bb121d6d2",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "46eb42ace646aeea9054197a90168300e24ff5bed2e85a4f4d205baec1295dfc",
    "pwSalt" : -3400884020829111347,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-f01e4d4e63716ee01efbc2dd4bd0cda7",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "fde71b5eec1634ed3fa7a1632c5da1cd69760eeec1eb699a0fa667e7ad542836",
    "pwSalt" : -6150639763569577496,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-fc5bfa949e43698273f7319bb121d6d2",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "a8a447035d882d38de5811c2f441dd40d399bc470449e24bd1cd76f4e708236e",
    "pwSalt" : -1773647930929806378,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-f01e4d4e63716ee01efbc2dd4bd0cda7",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "3e6782dcea0b1bca913669e3295c4cbda76da9a52cf857789ff771774d690f7a",
    "pwSalt" : -3036437491760991873,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-fc5bfa949e43698273f7319bb121d6d2",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "5525c29fec5192519d97b6a4daec1f266e8f95d2d892ecd03c2df4cbc10b862e",
    "pwSalt" : -3792853783537681530,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-f01e4d4e63716ee01efbc2dd4bd0cda7",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "bb48b431fba606f735ade20a7c1988e1208a5ac9d0edef642e7de155abfce2c8",
    "pwSalt" : -5139160010548805138,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-fc5bfa949e43698273f7319bb121d6d2",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "5f89bd6ad4dd34f062204e44b7689a81289adcb5cac6991bda814868147c4a1e",
    "pwSalt" : -6111952266267993395,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-f01e4d4e63716ee01efbc2dd4bd0cda7",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "f743247a79cf165917bc365fe3606439ea986492d9e0da61ddfcfc075f24476b",
    "pwSalt" : -831143705541851909,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-fc5bfa949e43698273f7319bb121d6d2",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "5ed99d26b23f41f56c435a271545554ed26d37827fc447ddd4620847e8d7c338",
    "pwSalt" : -1181756999627085320,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "7478d39175a789886294633d4f3997d71f7e5e2c557377fa2db21f34a8329c10",
    "pwSalt" : 2720525430746451818,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "dbcfa59be46b040f363dcacf437277111a5077089e9c4ab4ab6f90e350372597",
    "pwSalt" : 6391617272959493963,
    "pwLogin" : true
  }, {
    "name" : "nawojka",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "1284ad0e74803d8eb094c0d8eaf2aed93cc8996145aeeb0950713482c485b57f",
    "pwSalt" : -178174408511771751,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20161019-1014",
    "gitHash" : "518f0d6d44abc87bc392646e4369a20c8192b7cf",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2a1rikvzfccdiy33jfnpsc6ay"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-ACTIVITYMONITOR-BASE"
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "7pkr9tjarlk444bfhyhf2zlv6"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-ALERTPUBLISHER-BASE"
      }
    }, {
      "name" : "mgmt-EVENTSERVER-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "e1yd9vrth722651uy17oxhg1"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-EVENTSERVER-BASE"
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "5pmjolxkfkbjyhjo5u7rjidwb"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-HOSTMONITOR-BASE"
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "80k0p39ihpw85x20phml6m7ut"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-REPORTSMANAGER-BASE"
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-fc5bfa949e43698273f7319bb121d6d2",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-00ef27a3e32bc603a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "d6j8hj205ouwvva3nxnyc4wc0"
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-SERVICEMONITOR-BASE"
      }
    } ],
    "displayName" : "Cloudera Management Service",
    "roleConfigGroups" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-BASE",
      "displayName" : "Activity Monitor Default Group",
      "roleType" : "ACTIVITYMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "ip-172-31-44-213.eu-central-1.compute.internal"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "amon_password"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-BASE",
      "displayName" : "Alert Publisher Default Group",
      "roleType" : "ALERTPUBLISHER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-BASE",
      "displayName" : "Event Server Default Group",
      "roleType" : "EVENTSERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-BASE",
      "displayName" : "Host Monitor Default Group",
      "roleType" : "HOSTMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }
    }, {
      "name" : "mgmt-NAVIGATOR-BASE",
      "displayName" : "Navigator Audit Server Default Group",
      "roleType" : "NAVIGATOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-NAVIGATORMETASERVER-BASE",
      "displayName" : "Navigator Metadata Server Default Group",
      "roleType" : "NAVIGATORMETASERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-BASE",
      "displayName" : "Reports Manager Default Group",
      "roleType" : "REPORTSMANAGER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-44-213.eu-central-1.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman_password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-BASE",
      "displayName" : "Service Monitor Default Group",
      "roleType" : "SERVICEMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }
    } ]
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/26/2012 3:10"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/,http://localhost/cdh5.8.3/"
    } ]
  },
  "allHostsConfig" : {
    "items" : [ {
      "name" : "rm_enabled",
      "value" : "true"
    } ]
  },
  "peers" : [ {
    "name" : "olgierdg",
    "type" : "REPLICATION",
    "url" : "http://ec2-3-120-225-216.eu-central-1.compute.amazonaws.com:7180",
    "username" : "__cloudera_internal_user__0295bcbe-8f25-4d03-9c98-b41813eca418",
    "password" : "9115cf2b-d49e-4c7a-8009-96ee4e4c14cf3ed82e0f-f4da-4a7e-99b9-0d886646fa29",
    "clouderaManagerCreatedUser" : true
  } ],
  "hostTemplates" : {
    "items" : [ ]
  }
}
```
