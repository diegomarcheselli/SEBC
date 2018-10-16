# Add user:
```
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'useradd nawojka'
ansible -i hosts all --user centos --private-key /Users/n.schmidt/.ssh/aws.pem -c paramiko --become -m shell -a 'echo "nawojka" | passwd --stdin nawojka'

ec2-52-59-231-3.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
ec2-18-185-97-117.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
ec2-35-158-75-43.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
ec2-18-194-208-128.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
ec2-18-196-113-149.eu-central-1.compute.amazonaws.com | SUCCESS | rc=0 >>
```

# Create HDFS home directory:
```
sudo -u hdfs hdfs dfs -mkdir /user/nawojka
```
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -chown nawojka:supergroup  /user/nawojka
```
```
[centos@ip-172-31-44-213 ~]$ sudo -u hdfs hdfs dfs -ls /user/
Found 6 items
drwx------   - hdfs    supergroup          0 2018-10-16 08:58 /user/hdfs
drwxrwxrwx   - mapred  hadoop              0 2018-10-15 19:01 /user/history
drwxrwxr-t   - hive    hive                0 2018-10-15 19:02 /user/hive
drwxrwxr-x   - hue     hue                 0 2018-10-15 19:02 /user/hue
drwxr-xr-x   - nawojka supergroup          0 2018-10-16 09:05 /user/nawojka
drwxrwxr-x   - oozie   oozie               0 2018-10-15 19:03 /user/oozie
```
# Run teragen
Command:
```
time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -Ddfs.block.size=33554432 100000000 /user/nawojka/teragen
```
Output:
```
[nawojka@ip-172-31-44-213 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -Ddfs.block.size=33554432 100000000 /user/nawojka/teragen
18/10/16 09:19:51 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-33-143.eu-central-1.compute.internal/172.31.33.143:8032
18/10/16 09:19:52 INFO terasort.TeraSort: Generating 100000000 using 4
18/10/16 09:19:52 INFO mapreduce.JobSubmitter: number of splits:4
18/10/16 09:19:52 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
18/10/16 09:19:52 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/10/16 09:19:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539630088750_0004
18/10/16 09:19:52 INFO impl.YarnClientImpl: Submitted application application_1539630088750_0004
18/10/16 09:19:52 INFO mapreduce.Job: The url to track the job: http://ip-172-31-33-143.eu-central-1.compute.internal:8088/proxy/application_1539630088750_0004/
18/10/16 09:19:52 INFO mapreduce.Job: Running job: job_1539630088750_0004
18/10/16 09:19:57 INFO mapreduce.Job: Job job_1539630088750_0004 running in uber mode : false
18/10/16 09:19:57 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 09:20:08 INFO mapreduce.Job:  map 8% reduce 0%
18/10/16 09:20:09 INFO mapreduce.Job:  map 16% reduce 0%
18/10/16 09:20:11 INFO mapreduce.Job:  map 19% reduce 0%
18/10/16 09:20:12 INFO mapreduce.Job:  map 22% reduce 0%
18/10/16 09:20:14 INFO mapreduce.Job:  map 24% reduce 0%
18/10/16 09:20:15 INFO mapreduce.Job:  map 27% reduce 0%
18/10/16 09:20:17 INFO mapreduce.Job:  map 30% reduce 0%
18/10/16 09:20:18 INFO mapreduce.Job:  map 32% reduce 0%
18/10/16 09:20:20 INFO mapreduce.Job:  map 35% reduce 0%
18/10/16 09:20:21 INFO mapreduce.Job:  map 38% reduce 0%
18/10/16 09:20:23 INFO mapreduce.Job:  map 40% reduce 0%
18/10/16 09:20:24 INFO mapreduce.Job:  map 43% reduce 0%
18/10/16 09:20:26 INFO mapreduce.Job:  map 45% reduce 0%
18/10/16 09:20:27 INFO mapreduce.Job:  map 48% reduce 0%
18/10/16 09:20:29 INFO mapreduce.Job:  map 50% reduce 0%
18/10/16 09:20:30 INFO mapreduce.Job:  map 54% reduce 0%
18/10/16 09:20:32 INFO mapreduce.Job:  map 57% reduce 0%
18/10/16 09:20:33 INFO mapreduce.Job:  map 59% reduce 0%
18/10/16 09:20:35 INFO mapreduce.Job:  map 61% reduce 0%
18/10/16 09:20:36 INFO mapreduce.Job:  map 63% reduce 0%
18/10/16 09:20:39 INFO mapreduce.Job:  map 67% reduce 0%
18/10/16 09:20:41 INFO mapreduce.Job:  map 68% reduce 0%
18/10/16 09:20:42 INFO mapreduce.Job:  map 70% reduce 0%
18/10/16 09:20:45 INFO mapreduce.Job:  map 73% reduce 0%
18/10/16 09:20:48 INFO mapreduce.Job:  map 77% reduce 0%
18/10/16 09:20:51 INFO mapreduce.Job:  map 81% reduce 0%
18/10/16 09:20:54 INFO mapreduce.Job:  map 85% reduce 0%
18/10/16 09:20:57 INFO mapreduce.Job:  map 88% reduce 0%
18/10/16 09:21:00 INFO mapreduce.Job:  map 91% reduce 0%
18/10/16 09:21:03 INFO mapreduce.Job:  map 94% reduce 0%
18/10/16 09:21:06 INFO mapreduce.Job:  map 97% reduce 0%
18/10/16 09:21:07 INFO mapreduce.Job:  map 98% reduce 0%
18/10/16 09:21:08 INFO mapreduce.Job:  map 99% reduce 0%
18/10/16 09:21:09 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 09:21:11 INFO mapreduce.Job: Job job_1539630088750_0004 completed successfully
18/10/16 09:21:11 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=492300
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=266646
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=266646
		Total vcore-seconds taken by all map tasks=266646
		Total megabyte-seconds taken by all map tasks=273045504
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=585
		CPU time spent (ms)=142410
		Physical memory (bytes) snapshot=1385897984
		Virtual memory (bytes) snapshot=11114291200
		Total committed heap usage (bytes)=1112014848
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=10000000000

real	1m21.796s
user	0m6.219s
sys	0m0.439s
```

# Run TeraSort
Command:
```
time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/nawojka/teragen /user/nawojka/terasort
```
Output:
```
[nawojka@ip-172-31-44-213 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/nawojka/teragen /user/nawojka/terasort
18/10/16 09:22:55 INFO terasort.TeraSort: starting
18/10/16 09:22:56 INFO input.FileInputFormat: Total input paths to process : 4
Spent 166ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 172ms
Sampling 10 splits of 300
Making 8 from 100000 sampled records
Computing parititions took 672ms
Spent 846ms computing partitions.
18/10/16 09:22:57 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-33-143.eu-central-1.compute.internal/172.31.33.143:8032
18/10/16 09:22:57 INFO mapreduce.JobSubmitter: number of splits:300
18/10/16 09:22:57 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539630088750_0005
18/10/16 09:22:57 INFO impl.YarnClientImpl: Submitted application application_1539630088750_0005
18/10/16 09:22:57 INFO mapreduce.Job: The url to track the job: http://ip-172-31-33-143.eu-central-1.compute.internal:8088/proxy/application_1539630088750_0005/
18/10/16 09:22:57 INFO mapreduce.Job: Running job: job_1539630088750_0005
18/10/16 09:23:03 INFO mapreduce.Job: Job job_1539630088750_0005 running in uber mode : false
18/10/16 09:23:03 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 09:23:11 INFO mapreduce.Job:  map 3% reduce 0%
18/10/16 09:23:17 INFO mapreduce.Job:  map 5% reduce 0%
18/10/16 09:23:23 INFO mapreduce.Job:  map 6% reduce 0%
18/10/16 09:23:24 INFO mapreduce.Job:  map 8% reduce 0%
18/10/16 09:23:29 INFO mapreduce.Job:  map 9% reduce 0%
18/10/16 09:23:30 INFO mapreduce.Job:  map 10% reduce 0%
18/10/16 09:23:31 INFO mapreduce.Job:  map 11% reduce 0%
18/10/16 09:23:36 INFO mapreduce.Job:  map 13% reduce 0%
18/10/16 09:23:41 INFO mapreduce.Job:  map 15% reduce 0%
18/10/16 09:23:44 INFO mapreduce.Job:  map 16% reduce 0%
18/10/16 09:23:47 INFO mapreduce.Job:  map 17% reduce 0%
18/10/16 09:23:48 INFO mapreduce.Job:  map 18% reduce 0%
18/10/16 09:23:50 INFO mapreduce.Job:  map 19% reduce 0%
18/10/16 09:23:53 INFO mapreduce.Job:  map 20% reduce 0%
18/10/16 09:23:54 INFO mapreduce.Job:  map 21% reduce 0%
18/10/16 09:23:59 INFO mapreduce.Job:  map 23% reduce 0%
18/10/16 09:24:02 INFO mapreduce.Job:  map 24% reduce 0%
18/10/16 09:24:05 INFO mapreduce.Job:  map 25% reduce 0%
18/10/16 09:24:06 INFO mapreduce.Job:  map 26% reduce 0%
18/10/16 09:24:08 INFO mapreduce.Job:  map 27% reduce 0%
18/10/16 09:24:11 INFO mapreduce.Job:  map 28% reduce 0%
18/10/16 09:24:12 INFO mapreduce.Job:  map 29% reduce 0%
18/10/16 09:24:17 INFO mapreduce.Job:  map 31% reduce 0%
18/10/16 09:24:19 INFO mapreduce.Job:  map 32% reduce 0%
18/10/16 09:24:23 INFO mapreduce.Job:  map 33% reduce 0%
18/10/16 09:24:24 INFO mapreduce.Job:  map 34% reduce 0%
18/10/16 09:24:26 INFO mapreduce.Job:  map 35% reduce 0%
18/10/16 09:24:29 INFO mapreduce.Job:  map 36% reduce 0%
18/10/16 09:24:30 INFO mapreduce.Job:  map 37% reduce 0%
18/10/16 09:24:34 INFO mapreduce.Job:  map 38% reduce 0%
18/10/16 09:24:35 INFO mapreduce.Job:  map 39% reduce 0%
18/10/16 09:24:38 INFO mapreduce.Job:  map 40% reduce 0%
18/10/16 09:24:41 INFO mapreduce.Job:  map 41% reduce 0%
18/10/16 09:24:42 INFO mapreduce.Job:  map 42% reduce 0%
18/10/16 09:24:44 INFO mapreduce.Job:  map 43% reduce 0%
18/10/16 09:24:47 INFO mapreduce.Job:  map 44% reduce 0%
18/10/16 09:24:49 INFO mapreduce.Job:  map 45% reduce 0%
18/10/16 09:24:52 INFO mapreduce.Job:  map 46% reduce 0%
18/10/16 09:24:53 INFO mapreduce.Job:  map 47% reduce 0%
18/10/16 09:24:55 INFO mapreduce.Job:  map 48% reduce 0%
18/10/16 09:24:58 INFO mapreduce.Job:  map 49% reduce 0%
18/10/16 09:25:01 INFO mapreduce.Job:  map 50% reduce 0%
18/10/16 09:25:03 INFO mapreduce.Job:  map 51% reduce 0%
18/10/16 09:25:06 INFO mapreduce.Job:  map 52% reduce 0%
18/10/16 09:25:08 INFO mapreduce.Job:  map 53% reduce 0%
18/10/16 09:25:11 INFO mapreduce.Job:  map 54% reduce 0%
18/10/16 09:25:12 INFO mapreduce.Job:  map 55% reduce 0%
18/10/16 09:25:14 INFO mapreduce.Job:  map 56% reduce 0%
18/10/16 09:25:18 INFO mapreduce.Job:  map 57% reduce 0%
18/10/16 09:25:19 INFO mapreduce.Job:  map 58% reduce 0%
18/10/16 09:25:22 INFO mapreduce.Job:  map 59% reduce 0%
18/10/16 09:25:24 INFO mapreduce.Job:  map 60% reduce 0%
18/10/16 09:25:25 INFO mapreduce.Job:  map 61% reduce 0%
18/10/16 09:25:29 INFO mapreduce.Job:  map 62% reduce 0%
18/10/16 09:25:30 INFO mapreduce.Job:  map 63% reduce 0%
18/10/16 09:25:32 INFO mapreduce.Job:  map 64% reduce 0%
18/10/16 09:25:35 INFO mapreduce.Job:  map 65% reduce 0%
18/10/16 09:25:37 INFO mapreduce.Job:  map 66% reduce 0%
18/10/16 09:25:39 INFO mapreduce.Job:  map 67% reduce 0%
18/10/16 09:25:41 INFO mapreduce.Job:  map 68% reduce 0%
18/10/16 09:25:43 INFO mapreduce.Job:  map 69% reduce 0%
18/10/16 09:25:46 INFO mapreduce.Job:  map 70% reduce 0%
18/10/16 09:25:48 INFO mapreduce.Job:  map 71% reduce 0%
18/10/16 09:25:50 INFO mapreduce.Job:  map 72% reduce 0%
18/10/16 09:25:53 INFO mapreduce.Job:  map 73% reduce 0%
18/10/16 09:25:55 INFO mapreduce.Job:  map 74% reduce 0%
18/10/16 09:25:57 INFO mapreduce.Job:  map 75% reduce 0%
18/10/16 09:25:59 INFO mapreduce.Job:  map 76% reduce 0%
18/10/16 09:26:02 INFO mapreduce.Job:  map 77% reduce 0%
18/10/16 09:26:04 INFO mapreduce.Job:  map 78% reduce 0%
18/10/16 09:26:06 INFO mapreduce.Job:  map 79% reduce 0%
18/10/16 09:26:08 INFO mapreduce.Job:  map 80% reduce 0%
18/10/16 09:26:11 INFO mapreduce.Job:  map 81% reduce 0%
18/10/16 09:26:12 INFO mapreduce.Job:  map 82% reduce 0%
18/10/16 09:26:15 INFO mapreduce.Job:  map 83% reduce 0%
18/10/16 09:26:20 INFO mapreduce.Job:  map 83% reduce 6%
18/10/16 09:26:21 INFO mapreduce.Job:  map 84% reduce 9%
18/10/16 09:26:22 INFO mapreduce.Job:  map 84% reduce 11%
18/10/16 09:26:23 INFO mapreduce.Job:  map 84% reduce 13%
18/10/16 09:26:25 INFO mapreduce.Job:  map 84% reduce 14%
18/10/16 09:26:26 INFO mapreduce.Job:  map 85% reduce 14%
18/10/16 09:26:31 INFO mapreduce.Job:  map 86% reduce 14%
18/10/16 09:26:33 INFO mapreduce.Job:  map 87% reduce 14%
18/10/16 09:26:36 INFO mapreduce.Job:  map 88% reduce 14%
18/10/16 09:26:38 INFO mapreduce.Job:  map 88% reduce 15%
18/10/16 09:26:41 INFO mapreduce.Job:  map 89% reduce 15%
18/10/16 09:26:46 INFO mapreduce.Job:  map 90% reduce 15%
18/10/16 09:26:49 INFO mapreduce.Job:  map 91% reduce 15%
18/10/16 09:26:51 INFO mapreduce.Job:  map 92% reduce 15%
18/10/16 09:26:56 INFO mapreduce.Job:  map 93% reduce 15%
18/10/16 09:27:00 INFO mapreduce.Job:  map 93% reduce 16%
18/10/16 09:27:01 INFO mapreduce.Job:  map 94% reduce 16%
18/10/16 09:27:04 INFO mapreduce.Job:  map 95% reduce 16%
18/10/16 09:27:07 INFO mapreduce.Job:  map 96% reduce 16%
18/10/16 09:27:11 INFO mapreduce.Job:  map 97% reduce 16%
18/10/16 09:27:15 INFO mapreduce.Job:  map 98% reduce 16%
18/10/16 09:27:19 INFO mapreduce.Job:  map 99% reduce 16%
18/10/16 09:27:21 INFO mapreduce.Job:  map 100% reduce 17%
18/10/16 09:27:25 INFO mapreduce.Job:  map 100% reduce 22%
18/10/16 09:27:26 INFO mapreduce.Job:  map 100% reduce 26%
18/10/16 09:27:27 INFO mapreduce.Job:  map 100% reduce 31%
18/10/16 09:27:28 INFO mapreduce.Job:  map 100% reduce 34%
18/10/16 09:27:29 INFO mapreduce.Job:  map 100% reduce 35%
18/10/16 09:27:30 INFO mapreduce.Job:  map 100% reduce 44%
18/10/16 09:27:31 INFO mapreduce.Job:  map 100% reduce 46%
18/10/16 09:27:32 INFO mapreduce.Job:  map 100% reduce 47%
18/10/16 09:27:33 INFO mapreduce.Job:  map 100% reduce 53%
18/10/16 09:27:34 INFO mapreduce.Job:  map 100% reduce 55%
18/10/16 09:27:35 INFO mapreduce.Job:  map 100% reduce 56%
18/10/16 09:27:36 INFO mapreduce.Job:  map 100% reduce 58%
18/10/16 09:27:37 INFO mapreduce.Job:  map 100% reduce 60%
18/10/16 09:27:38 INFO mapreduce.Job:  map 100% reduce 61%
18/10/16 09:27:39 INFO mapreduce.Job:  map 100% reduce 71%
18/10/16 09:27:40 INFO mapreduce.Job:  map 100% reduce 77%
18/10/16 09:27:42 INFO mapreduce.Job:  map 100% reduce 78%
18/10/16 09:27:43 INFO mapreduce.Job:  map 100% reduce 85%
18/10/16 09:27:46 INFO mapreduce.Job:  map 100% reduce 90%
18/10/16 09:27:49 INFO mapreduce.Job:  map 100% reduce 94%
18/10/16 09:27:52 INFO mapreduce.Job:  map 100% reduce 99%
18/10/16 09:27:55 INFO mapreduce.Job:  map 100% reduce 100%
18/10/16 09:27:55 INFO mapreduce.Job: Job job_1539630088750_0005 completed successfully
18/10/16 09:27:55 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4475137001
		FILE: Number of bytes written=8888734512
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000047100
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=924
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters
		Launched map tasks=300
		Launched reduce tasks=8
		Data-local map tasks=300
		Total time spent by all maps in occupied slots (ms)=1449043
		Total time spent by all reduces in occupied slots (ms)=493385
		Total time spent by all map tasks (ms)=1449043
		Total time spent by all reduce tasks (ms)=493385
		Total vcore-seconds taken by all map tasks=1449043
		Total vcore-seconds taken by all reduce tasks=493385
		Total megabyte-seconds taken by all map tasks=1483820032
		Total megabyte-seconds taken by all reduce tasks=505226240
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4375223545
		Input split bytes=47100
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4375223545
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =2400
		Failed Shuffles=0
		Merged Map outputs=2400
		GC time elapsed (ms)=32106
		CPU time spent (ms)=1314690
		Physical memory (bytes) snapshot=146812903424
		Virtual memory (bytes) snapshot=853663793152
		Total committed heap usage (bytes)=153269829632
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=10000000000
	File Output Format Counters
		Bytes Written=10000000000
18/10/16 09:27:55 INFO terasort.TeraSort: done

real	5m1.489s
user	0m8.766s
sys	0m0.709s
```
