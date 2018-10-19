# Command
```
[root@ip-172-31-22-209 krb5kdc]# su - raffles
[raffles@ip-172-31-22-209 ~]$ kinit
Password for raffles@NAWOJKA.SG:
[raffles@ip-172-31-22-209 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/raffles/tgen512 /user/raffles/tsort512
```
```
18/10/19 09:16:06 INFO terasort.TeraSort: starting
18/10/19 09:16:07 INFO hdfs.DFSClient: Created token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539940567960, maxDate=1540545367960, sequenceNumber=1, masterKeyId=2 on 172.31.19.169:8020
18/10/19 09:16:08 INFO security.TokenCache: Got dt for hdfs://ip-172-31-19-169.eu-west-2.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.19.169:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539940567960, maxDate=1540545367960, sequenceNumber=1, masterKeyId=2)
18/10/19 09:16:08 INFO input.FileInputFormat: Total input paths to process : 6
Spent 361ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 366ms
Sampling 10 splits of 156
Making 8 from 100000 sampled records
Computing parititions took 677ms
Spent 1044ms computing partitions.
18/10/19 09:16:08 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-19-169.eu-west-2.compute.internal/172.31.19.169:8032
18/10/19 09:16:09 INFO mapreduce.JobSubmitter: number of splits:156
18/10/19 09:16:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539940258703_0001
18/10/19 09:16:09 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.19.169:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@NAWOJKA.SG, renewer=yarn, realUser=, issueDate=1539940567960, maxDate=1540545367960, sequenceNumber=1, masterKeyId=2)
18/10/19 09:16:10 INFO impl.YarnClientImpl: Submitted application application_1539940258703_0001
18/10/19 09:16:10 INFO mapreduce.Job: The url to track the job: http://ip-172-31-19-169.eu-west-2.compute.internal:8088/proxy/application_1539940258703_0001/
18/10/19 09:16:10 INFO mapreduce.Job: Running job: job_1539940258703_0001
18/10/19 09:16:20 INFO mapreduce.Job: Job job_1539940258703_0001 running in uber mode : false
18/10/19 09:16:20 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 09:16:32 INFO mapreduce.Job:  map 1% reduce 0%
18/10/19 09:16:35 INFO mapreduce.Job:  map 5% reduce 0%
18/10/19 09:16:38 INFO mapreduce.Job:  map 6% reduce 0%
18/10/19 09:16:43 INFO mapreduce.Job:  map 7% reduce 0%
18/10/19 09:16:44 INFO mapreduce.Job:  map 10% reduce 0%
18/10/19 09:16:45 INFO mapreduce.Job:  map 11% reduce 0%
18/10/19 09:16:46 INFO mapreduce.Job:  map 12% reduce 0%
18/10/19 09:16:52 INFO mapreduce.Job:  map 13% reduce 0%
18/10/19 09:16:53 INFO mapreduce.Job:  map 17% reduce 0%
18/10/19 09:16:58 INFO mapreduce.Job:  map 18% reduce 0%
18/10/19 09:17:01 INFO mapreduce.Job:  map 19% reduce 0%
18/10/19 09:17:02 INFO mapreduce.Job:  map 22% reduce 0%
18/10/19 09:17:05 INFO mapreduce.Job:  map 23% reduce 0%
18/10/19 09:17:10 INFO mapreduce.Job:  map 26% reduce 0%
18/10/19 09:17:11 INFO mapreduce.Job:  map 28% reduce 0%
18/10/19 09:17:16 INFO mapreduce.Job:  map 29% reduce 0%
18/10/19 09:17:18 INFO mapreduce.Job:  map 31% reduce 0%
18/10/19 09:17:20 INFO mapreduce.Job:  map 33% reduce 0%
18/10/19 09:17:22 INFO mapreduce.Job:  map 34% reduce 0%


18/10/19 09:17:23 INFO mapreduce.Job:  map 35% reduce 0%
18/10/19 09:17:27 INFO mapreduce.Job:  map 37% reduce 0%
18/10/19 09:17:28 INFO mapreduce.Job:  map 38% reduce 0%
18/10/19 09:17:29 INFO mapreduce.Job:  map 40% reduce 0%
18/10/19 09:17:35 INFO mapreduce.Job:  map 41% reduce 0%
18/10/19 09:17:36 INFO mapreduce.Job:  map 42% reduce 0%
18/10/19 09:17:37 INFO mapreduce.Job:  map 44% reduce 0%
18/10/19 09:17:38 INFO mapreduce.Job:  map 45% reduce 0%
18/10/19 09:17:40 INFO mapreduce.Job:  map 46% reduce 0%
18/10/19 09:17:44 INFO mapreduce.Job:  map 47% reduce 0%
18/10/19 09:17:45 INFO mapreduce.Job:  map 49% reduce 0%
18/10/19 09:17:46 INFO mapreduce.Job:  map 50% reduce 0%
18/10/19 09:17:47 INFO mapreduce.Job:  map 51% reduce 0%
18/10/19 09:17:52 INFO mapreduce.Job:  map 53% reduce 0%
18/10/19 09:17:53 INFO mapreduce.Job:  map 54% reduce 0%
18/10/19 09:17:54 INFO mapreduce.Job:  map 56% reduce 0%
18/10/19 09:17:58 INFO mapreduce.Job:  map 57% reduce 0%
18/10/19 09:18:00 INFO mapreduce.Job:  map 58% reduce 0%
18/10/19 09:18:01 INFO mapreduce.Job:  map 60% reduce 0%
18/10/19 09:18:03 INFO mapreduce.Job:  map 61% reduce 0%
18/10/19 09:18:04 INFO mapreduce.Job:  map 62% reduce 0%
18/10/19 09:18:06 INFO mapreduce.Job:  map 63% reduce 0%
18/10/19 09:18:09 INFO mapreduce.Job:  map 64% reduce 0%
18/10/19 09:18:11 INFO mapreduce.Job:  map 67% reduce 0%
18/10/19 09:18:13 INFO mapreduce.Job:  map 68% reduce 0%
18/10/19 09:18:17 INFO mapreduce.Job:  map 69% reduce 0%
18/10/19 09:18:18 INFO mapreduce.Job:  map 71% reduce 0%
18/10/19 09:18:19 INFO mapreduce.Job:  map 72% reduce 0%
18/10/19 09:18:21 INFO mapreduce.Job:  map 73% reduce 0%
18/10/19 09:18:23 INFO mapreduce.Job:  map 74% reduce 0%
18/10/19 09:18:27 INFO mapreduce.Job:  map 75% reduce 0%
18/10/19 09:18:28 INFO mapreduce.Job:  map 77% reduce 0%
18/10/19 09:18:29 INFO mapreduce.Job:  map 78% reduce 0%
18/10/19 09:18:30 INFO mapreduce.Job:  map 79% reduce 0%
18/10/19 09:18:35 INFO mapreduce.Job:  map 80% reduce 0%
18/10/19 09:18:36 INFO mapreduce.Job:  map 82% reduce 0%
18/10/19 09:18:37 INFO mapreduce.Job:  map 84% reduce 0%
18/10/19 09:18:38 INFO mapreduce.Job:  map 85% reduce 0%
18/10/19 09:18:43 INFO mapreduce.Job:  map 86% reduce 0%
18/10/19 09:18:45 INFO mapreduce.Job:  map 87% reduce 0%
18/10/19 09:18:49 INFO mapreduce.Job:  map 88% reduce 0%
18/10/19 09:18:52 INFO mapreduce.Job:  map 89% reduce 0%
18/10/19 09:18:53 INFO mapreduce.Job:  map 90% reduce 4%
18/10/19 09:18:55 INFO mapreduce.Job:  map 90% reduce 11%
18/10/19 09:18:58 INFO mapreduce.Job:  map 92% reduce 15%
18/10/19 09:18:59 INFO mapreduce.Job:  map 93% reduce 15%
18/10/19 09:19:03 INFO mapreduce.Job:  map 94% reduce 15%
18/10/19 09:19:04 INFO mapreduce.Job:  map 95% reduce 15%
18/10/19 09:19:05 INFO mapreduce.Job:  map 95% reduce 16%
18/10/19 09:19:06 INFO mapreduce.Job:  map 96% reduce 16%
18/10/19 09:19:08 INFO mapreduce.Job:  map 97% reduce 16%
18/10/19 09:19:11 INFO mapreduce.Job:  map 98% reduce 16%
18/10/19 09:19:12 INFO mapreduce.Job:  map 99% reduce 16%
18/10/19 09:19:16 INFO mapreduce.Job:  map 100% reduce 16%
18/10/19 09:19:17 INFO mapreduce.Job:  map 100% reduce 17%
18/10/19 09:19:19 INFO mapreduce.Job:  map 100% reduce 24%
18/10/19 09:19:22 INFO mapreduce.Job:  map 100% reduce 28%
18/10/19 09:19:23 INFO mapreduce.Job:  map 100% reduce 33%
18/10/19 09:19:25 INFO mapreduce.Job:  map 100% reduce 38%
18/10/19 09:19:27 INFO mapreduce.Job:  map 100% reduce 46%
18/10/19 09:19:28 INFO mapreduce.Job:  map 100% reduce 69%
18/10/19 09:19:31 INFO mapreduce.Job:  map 100% reduce 73%
18/10/19 09:19:32 INFO mapreduce.Job:  map 100% reduce 75%
18/10/19 09:19:33 INFO mapreduce.Job:  map 100% reduce 79%
18/10/19 09:19:34 INFO mapreduce.Job:  map 100% reduce 91%
18/10/19 09:19:36 INFO mapreduce.Job:  map 100% reduce 92%
18/10/19 09:19:39 INFO mapreduce.Job:  map 100% reduce 96%
18/10/19 09:19:40 INFO mapreduce.Job:  map 100% reduce 99%
18/10/19 09:19:42 INFO mapreduce.Job:  map 100% reduce 100%
18/10/19 09:19:45 INFO mapreduce.Job: Job job_1539940258703_0001 completed successfully
18/10/19 09:19:45 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=2285583257
		FILE: Number of bytes written=4550619013
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=5120024180
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=492
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters
		Launched map tasks=156
		Launched reduce tasks=8
		Data-local map tasks=154
		Rack-local map tasks=2
		Total time spent by all maps in occupied slots (ms)=1063717
		Total time spent by all reduces in occupied slots (ms)=313623
		Total time spent by all map tasks (ms)=1063717
		Total time spent by all reduce tasks (ms)=313623
		Total vcore-milliseconds taken by all map tasks=1063717
		Total vcore-milliseconds taken by all reduce tasks=313623
		Total megabyte-milliseconds taken by all map tasks=1089246208
		Total megabyte-milliseconds taken by all reduce tasks=321149952
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Map output bytes=5222400000
		Map output materialized bytes=2240103638
		Input split bytes=24180
		Combine input records=0
		Combine output records=0
		Reduce input groups=51200000
		Reduce shuffle bytes=2240103638
		Reduce input records=51200000
		Reduce output records=51200000
		Spilled Records=102400000
		Shuffled Maps =1248
		Failed Shuffles=0
		Merged Map outputs=1248
		GC time elapsed (ms)=24153
		CPU time spent (ms)=756830
		Physical memory (bytes) snapshot=82847576064
		Virtual memory (bytes) snapshot=455598981120
		Total committed heap usage (bytes)=85058912256
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=5120000000
	File Output Format Counters
		Bytes Written=5120000000
18/10/19 09:19:45 INFO terasort.TeraSort: done

real	3m39.935s
user	0m9.977s
sys	0m0.632s
```
