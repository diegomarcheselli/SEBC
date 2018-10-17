For testing I have change Container Memory for NodeManagers to 2GB. After this change YARN can use 7.3GB of memory and 13 vcores. The minimum container memory for my cluster is 1024MB, so it is not possible to run run with 512MB predefined in the script. I will run tests with 2 memory settings: 1024MB and 2048MB.

The results were usually worse with 2048 (because the number of containers was limited by memory setting - it was not possible to run containers that use more memory than maximal - 7.3GB)

Teragen does not use reducers, only mappers, the results for more mappers seem to be better (best for 4 mappers and 1 reducer) - 0m45.609s
Terasort performed best with 8 mappers and 1 reducers - 1m55.544s

Overall (teragen + terasort) performed best with 1024MB and 8 mappers and 2 reducers (0m53.797s + 1m58.430s) and then 1024 MB and 8 mappers and 1 reducer (0m59.387s + 1m55.544s).

# Resuls from the scripts
Test for 1 mapper and 1 reducer:
```
Testing loop started on Tue Oct 16 14:13:12 UTC 2018

MAP_MB = 819
RED_MB = 819
mappers = 1
reducers = 1
container memory = 1024

Starting teragen
real	1m14.943s
user	0m6.412s
sys	0m0.445s

Starting terasort
real	2m5.346s
user	0m8.199s
sys	0m0.554s

MAP_MB = 1638
RED_MB = 1638
mappers = 1
reducers = 1
container memory = 2048

Starting teragen
real	1m13.770s
user	0m6.523s
sys	0m0.448s

Starting terasort
real	4m27.883s
user	0m8.671s
sys	0m0.563s

Testing loop ended on Tue Oct 16 14:22:03 UTC 2018
```
Test for 2 mappers and 1 reducer:
```
Testing loop started on Tue Oct 16 14:25:23 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 2
reducers = 1
container memory = 1024

Starting teragen
real	0m56.608s
user	0m6.402s
sys	0m0.447s

Starting terasort
real	2m33.639s
user	0m8.407s
sys	0m0.540s

MAP_MB = 1638
RED_MB = 1638
mappers = 2
reducers = 1
container memory = 2048

Starting teragen
real	0m57.839s
user	0m6.336s
sys	0m0.487s

Starting terasort
real	4m45.691s
user	0m8.880s
sys	0m0.623s
Testing loop ended on Tue Oct 16 14:34:45 UTC 2018
```
Test for 1 mapper and 2 reducers:
```
Testing loop started on Tue Oct 16 14:36:29 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 1
reducers = 2
container memory = 1024

Starting teragen
real	1m18.600s
user	0m6.314s
sys	0m0.456s

Starting terasort
real	2m22.897s
user	0m8.643s
sys	0m0.549s

MAP_MB = 1638
RED_MB = 1638
mappers = 1
reducers = 2
container memory = 2048

Starting teragen
real	1m13.825s
user	0m6.493s
sys	0m0.455s

Starting terasort
real	4m27.126s
user	0m9.075s
sys	0m0.628s

Testing loop ended on Tue Oct 16 14:46:00 UTC 2018
```
Test for 2 mappers and 2 reducers:
```
Testing loop started on Tue Oct 16 18:06:43 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 2
reducers = 2
container memory = 1024

Starting teragen
real	1m5.272s
user	0m3.283
sys	0m0.464s

Starting terasort
real	2m24.466s
user	0m8.331s
sys	0m0.506s

MAP_MB = 1638
RED_MB = 1638
mappers = 2
reducers = 2
container memory = 2048

Starting teragen
real	1m3.762s
user	0m6.249s
sys	0m0.462s

Starting terasort
real	6m8.274s
user	0m8.815s
sys	0m0.655s
```
Test for 1 mapper and 4 reducers:
```
Testing loop started on Tue Oct 16 18:33:35 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 1
reducers = 4
container memory = 1024

Starting teragen
real	1m15.582s
user	0m6.440s
sys	0m0.462s

Starting terasort
real	2m54.550s
user	0m8.651s
sys	0m0.581s

MAP_MB = 1638
RED_MB = 1638
mappers = 1
reducers = 4
container memory = 2048

Starting teragen
real	1m11.874s
user	0m6.497s
sys	0m0.453s

Starting terasort
real	6m20.172s
user	0m9.000s
sys	0m0.614s
Testing loop ended on Tue Oct 16 18:45:26 UTC 2018
```
Test for 4 mappers and 1 reducer:
```
Testing loop started on Tue Oct 16 18:46:54 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 4
reducers = 1
container memory = 1024

Starting teragen
real	0m45.609s
user	0m6.085s
sys	0m0.459s

Starting terasort
real	2m34.918s
user	0m8.375s
sys	0m0.527s

MAP_MB = 1638
RED_MB = 1638
mappers = 4
reducers = 1
container memory = 2048

Starting teragen
real	0m58.067s
user	0m6.443s
sys	0m0.503s

Starting terasort
real	5m49.374s
user	0m9.228s
sys	0m0.626s

Testing loop ended on Tue Oct 16 18:57:10 UTC 2018
```
Test for 4 mappers and 2 reducers:
```
Testing loop started on Tue Oct 16 19:09:50 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 4
reducers = 2
container memory = 1024

Starting teragen
real	0m52.918s
user	0m6.220s
sys	0m0.473s

Starting terasort
real	2m55.597s
user	0m8.291s
sys	0m0.564s

MAP_MB = 1638
RED_MB = 1638
mappers = 4
reducers = 2
container memory = 2048

Starting teragen
real	1m2.963s
user	0m6.592s
sys	0m0.453s

Starting terasort
real	4m35.065s
user	0m8.745s
sys	0m0.625s

Deleted /results/tg-10GB-4-2-2048
Deleted /results/ts-10GB-4-2-2048
Testing loop ended on Tue Oct 16 19:19:25 UTC 2018
```
Test for 2 mappers and 4 reducers:
```
Testing loop started on Tue Oct 16 19:24:43 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 2
reducers = 4
container memory = 1024

Starting teragen
real	0m56.232s
user	0m6.325s
sys	0m0.409s

Starting terasort
real	3m17.855s
user	0m8.320s
sys	0m0.568s

MAP_MB = 1638
RED_MB = 1638
mappers = 2
reducers = 4
container memory = 2048

Starting teragen
real	0m58.153s
user	0m6.404s
sys	0m0.492s

Starting terasort
real	9m39.826s
user	0m9.826s
sys	0m0.701s

Testing loop ended on Tue Oct 16 19:39:43 UTC 2018
```
Test 1 mapper and 8 reducers:
```
Testing loop started on Tue Oct 16 20:30:28 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 1
reducers = 8
container memory = 1024

Starting teragen
real	1m13.709s
user	0m6.270s
sys	0m0.502s

Starting terasort
real	3m30.957s
user	0m8.529s
sys	0m0.552s

MAP_MB = 1638
RED_MB = 1638
mappers = 1
reducers = 8
container memory = 2048

Starting teragen
real	1m13.633s
user	0m6.442s
sys	0m0.473s

Starting terasort
real	4m57.716s
user	0m8.660s
sys	0m0.602s

Testing loop ended on Tue Oct 16 20:41:32 UTC 2018
```
Test 8 mappers and 1 reducer:
```
Testing loop started on Tue Oct 16 20:43:12 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 8
reducers = 1
container memory = 1024

Starting teragen
real	0m59.387s
user	0m6.376s
sys	0m0.445s

Starting terasort
real	1m55.544s
user	0m8.267s
sys	0m0.564s

MAP_MB = 1638
RED_MB = 1638
mappers = 8
reducers = 1
container memory = 2048

Starting teragen
real	1m8.984s
user	0m6.671s
sys	0m0.505s

Starting terasort
real	4m41.945s
user	0m8.705s
sys	0m0.618s
Testing loop ended on Tue Oct 16 20:52:06 UTC 2018
```


Test 8 mappers and 2 reducers:
```
Testing loop started on Tue Oct 16 21:25:32 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 8
reducers = 2
container memory = 1024

Starting teragen
real	0m53.797s
user	0m6.225s
sys	0m0.426s

Starting terasort
real	1m58.430s
user	0m8.189s
sys	0m0.566s

MAP_MB = 1638
RED_MB = 1638
mappers = 8
reducers = 2
container memory = 2048

Starting teragen
real	1m8.578s
user	0m6.337s
sys	0m0.464s

Starting terasort
real	4m19.965s
user	0m8.898s
sys	0m0.607s

Testing loop ended on Tue Oct 16 21:34:01 UTC 2018
```
Test 2 mappers and 8 reducers:
```
Testing loop started on Tue Oct 16 21:12:29 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 2
reducers = 8
container memory = 1024

Starting teragen
real	0m57.233s
user	0m6.299s
sys	0m0.500s

Starting terasort
real	2m25.632s
user	0m8.371s
sys	0m0.590s

MAP_MB = 1638
RED_MB = 1638
mappers = 2
reducers = 8
container memory = 2048

Starting teragen
real	0m55.945s
user	0m6.429s
sys	0m0.468s

Starting terasort
real	6m1.294s
user	0m9.004s
sys	0m0.628s

Testing loop ended on Tue Oct 16 21:22:57 UTC 2018
```
Test 8 mappers and 4 reducers:
```
Testing loop started on Tue Oct 16 21:37:14 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 8
reducers = 4
container memory = 1024

Starting teragen
real	0m52.208s
user	0m6.336s
sys	0m0.440s

Starting terasort
real	2m36.200s
user	0m8.364s
sys	0m0.546s

MAP_MB = 1638
RED_MB = 1638
mappers = 8
reducers = 4
container memory = 2048

Starting teragen
real	1m10.976s
user	0m6.391s
sys	0m0.454s

Starting terasort
real	6m0.214s
user	0m8.877s
sys	0m0.662s

Testing loop ended on Tue Oct 16 21:48:02 UTC 2018
```
Test 4 mappers and 8 reducers:
```
Testing loop started on Tue Oct 16 21:55:04 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 4
reducers = 8
container memory = 1024

Starting teragen
real	0m48.300s
user	0m6.247s
sys	0m0.503s

Starting terasort
real	3m4.271s
user	0m8.484s
sys	0m0.601s

MAP_MB = 1638
RED_MB = 1638
mappers = 4
reducers = 8
container memory = 2048

Starting teragen
real	0m55.818s
user	0m6.371s
sys	0m0.507s

Starting terasort
real	3m55.733s
user	0m8.848s
sys	0m0.625s

Testing loop ended on Tue Oct 16 22:03:56 UTC 2018
```

Test 4 mappers and 4 reducers:
```
Testing loop started on Tue Oct 16 20:57:51 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 4
reducers = 4
container memory = 1024

Starting teragen
real	0m51.586s
user	0m6.078s
sys	0m0.481s

Starting terasort
real	2m51.824s
user	0m8.490s
sys	0m0.552s

MAP_MB = 1638
RED_MB = 1638
mappers = 4
reducers = 4
container memory = 2048

Starting teragen
real	1m1.101s
user	0m6.273s
sys	0m0.469s

Starting terasort
real	6m24.930s
user	0m8.799s
sys	0m0.626s

Testing loop ended on Tue Oct 16 21:09:09 UTC 2018
```
Test 8 mappers and 8 reducers:
```
Testing loop started on Tue Oct 16 22:04:57 UTC 2018
MAP_MB = 819
RED_MB = 819
mappers = 8
reducers = 8
container memory = 1024

Starting teragen
real	0m50.614s
user	0m6.127s
sys	0m0.458s

Starting terasort
real	3m37.448s
user	0m8.593s
sys	0m0.619s

MAP_MB = 1638
RED_MB = 1638
mappers = 8
reducers = 8
container memory = 2048

Starting teragen
real	1m11.700s
user	0m6.543s
sys	0m0.458s

Starting terasort
real	6m30.421s
user	0m8.835s
sys	0m0.621s

Testing loop ended on Tue Oct 16 22:17:15 UTC 2018
```
