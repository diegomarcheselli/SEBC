# Command
```
[fullerton@ip-172-31-22-209 ~]$ kinit
Password for fullerton@NAWOJKA.SG:
[fullerton@ip-172-31-22-209 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar pi 16 1000
```
# Output
```
Number of Maps  = 16
Samples per Map = 1000
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Wrote input for Map #10
Wrote input for Map #11
Wrote input for Map #12
Wrote input for Map #13
Wrote input for Map #14
Wrote input for Map #15
Starting Job
18/10/19 09:24:14 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-19-169.eu-west-2.compute.internal/172.31.19.169:8032
18/10/19 09:24:14 INFO hdfs.DFSClient: Created token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539941054408, maxDate=1540545854408, sequenceNumber=2, masterKeyId=2 on 172.31.19.169:8020
18/10/19 09:24:14 INFO security.TokenCache: Got dt for hdfs://ip-172-31-19-169.eu-west-2.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.19.169:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539941054408, maxDate=1540545854408, sequenceNumber=2, masterKeyId=2)
18/10/19 09:24:14 INFO input.FileInputFormat: Total input paths to process : 16
18/10/19 09:24:14 INFO mapreduce.JobSubmitter: number of splits:16
18/10/19 09:24:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539940258703_0002
18/10/19 09:24:14 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.19.169:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539941054408, maxDate=1540545854408, sequenceNumber=2, masterKeyId=2)
18/10/19 09:24:15 INFO impl.YarnClientImpl: Submitted application application_1539940258703_0002
18/10/19 09:24:15 INFO mapreduce.Job: The url to track the job: http://ip-172-31-19-169.eu-west-2.compute.internal:8088/proxy/application_1539940258703_0002/
18/10/19 09:24:15 INFO mapreduce.Job: Running job: job_1539940258703_0002
18/10/19 09:24:23 INFO mapreduce.Job: Job job_1539940258703_0002 running in uber mode : false
18/10/19 09:24:23 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 09:24:29 INFO mapreduce.Job:  map 6% reduce 0%
18/10/19 09:24:30 INFO mapreduce.Job:  map 19% reduce 0%
18/10/19 09:24:33 INFO mapreduce.Job:  map 31% reduce 0%
18/10/19 09:24:34 INFO mapreduce.Job:  map 50% reduce 0%
18/10/19 09:24:36 INFO mapreduce.Job:  map 69% reduce 0%
18/10/19 09:24:38 INFO mapreduce.Job:  map 88% reduce 0%
18/10/19 09:24:40 INFO mapreduce.Job:  map 100% reduce 0%
18/10/19 09:24:43 INFO mapreduce.Job:  map 100% reduce 100%
18/10/19 09:24:43 INFO mapreduce.Job: Job job_1539940258703_0002 completed successfully
18/10/19 09:24:43 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=130
		FILE: Number of bytes written=2569767
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=4854
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=67
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters
		Launched map tasks=16
		Launched reduce tasks=1
		Data-local map tasks=15
		Rack-local map tasks=1
		Total time spent by all maps in occupied slots (ms)=86698
		Total time spent by all reduces in occupied slots (ms)=2976
		Total time spent by all map tasks (ms)=86698
		Total time spent by all reduce tasks (ms)=2976
		Total vcore-milliseconds taken by all map tasks=86698
		Total vcore-milliseconds taken by all reduce tasks=2976
		Total megabyte-milliseconds taken by all map tasks=88778752
		Total megabyte-milliseconds taken by all reduce tasks=3047424
	Map-Reduce Framework
		Map input records=16
		Map output records=32
		Map output bytes=288
		Map output materialized bytes=544
		Input split bytes=2966
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=544
		Reduce input records=32
		Reduce output records=0
		Spilled Records=64
		Shuffled Maps =16
		Failed Shuffles=0
		Merged Map outputs=16
		GC time elapsed (ms)=1393
		CPU time spent (ms)=13490
		Physical memory (bytes) snapshot=7580028928
		Virtual memory (bytes) snapshot=47197450240
		Total committed heap usage (bytes)=8041529344
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=1888
	File Output Format Counters
		Bytes Written=97
Job Finished in 29.52 seconds
Estimated value of Pi is 3.14250000000000000000

real	0m32.661s
user	0m7.455s
sys	0m0.587s
```
