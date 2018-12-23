<!--
Copyright (c) 2010 Yahoo! Inc., 2012 - 2016 YCSB contributors.
All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you
may not use this file except in compliance with the License. You
may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied. See the License for the specific language governing
permissions and limitations under the License. See accompanying
LICENSE file.
-->

# Yahoo! Cloud System Benchmark (YCSB)

[![Build Status](https://travis-ci.org/brianfrankcooper/YCSB.png?branch=master)](https://travis-ci.org/brianfrankcooper/YCSB)

# YCSB Cassandra with Latency Delaying Simulation

For research purpose only

Summaries for 1000 request

```
1. 20ms 80% delay    ->    800 * 20 ms =~ 16000 ms
First trial
[OVERALL], RunTime(ms), 13295
[OVERALL], Throughput(ops/sec), 75.21624670928921
[READ], Operations, 1000
[READ], AverageLatency(us), 9733.728
[READ], MinLatency(us), 518
[READ], MaxLatency(us), 50431
[READ], 95thPercentileLatency(us), 20719
[READ], 99thPercentileLatency(us), 24735
[READ], Return=OK, 1000

Second trial
[OVERALL], RunTime(ms), 13435
[OVERALL], Throughput(ops/sec), 74.4324525493115
[READ], Operations, 1000
[READ], AverageLatency(us), 9930.8
[READ], MinLatency(us), 631
[READ], MaxLatency(us), 59103
[READ], 95thPercentileLatency(us), 20639
[READ], 99thPercentileLatency(us), 22607
[READ], Return=OK, 1000

2. 40ms 30% delay    ->    300 * 40 ms =~ 12000 ms
First trial
[OVERALL], RunTime(ms), 14691
[OVERALL], Throughput(ops/sec), 68.06888571234089
[READ], Operations, 1000
[READ], AverageLatency(us), 7970.082
[READ], MinLatency(us), 729
[READ], MaxLatency(us), 70911
[READ], 95thPercentileLatency(us), 35455
[READ], 99thPercentileLatency(us), 41855
[READ], Return=OK, 1000

Second trial
[OVERALL], RunTime(ms), 14585
[OVERALL], Throughput(ops/sec), 68.56359273225917
[READ], Operations, 1000
[READ], AverageLatency(us), 8027.749
[READ], MinLatency(us), 720
[READ], MaxLatency(us), 65183
[READ], 95thPercentileLatency(us), 36095
[READ], 99thPercentileLatency(us), 41631
[READ], Return=OK, 1000

3. 20ms 30% delay    ->    300 * 20 ms =~  6000 ms
First trial
[OVERALL], RunTime(ms), 8564
[OVERALL], Throughput(ops/sec), 116.76786548341896
[READ], Operations, 1000
[READ], AverageLatency(us), 5043.276
[READ], MinLatency(us), 782
[READ], MaxLatency(us), 65919
[READ], 95thPercentileLatency(us), 19375
[READ], 99thPercentileLatency(us), 22255
[READ], Return=OK, 1000

Second trial
[OVERALL], RunTime(ms), 8494
[OVERALL], Throughput(ops/sec), 117.73016246762421
[READ], Operations, 1000
[READ], AverageLatency(us), 4994.549
[READ], MinLatency(us), 677
[READ], MaxLatency(us), 56287
[READ], 95thPercentileLatency(us), 19279
[READ], 99thPercentileLatency(us), 22607
[READ], Return=OK, 1000

4. 0ms  0%  delay    ->    0   * 20 ms =~     0 ms
First trial
[OVERALL], RunTime(ms), 6757
[OVERALL], Throughput(ops/sec), 147.9946721918011
[READ], Operations, 1000
[READ], AverageLatency(us), 3209.498
[READ], MinLatency(us), 590
[READ], MaxLatency(us), 50079
[READ], 95thPercentileLatency(us), 8095
[READ], 99thPercentileLatency(us), 13231
[READ], Return=OK, 1000

Second trial
[OVERALL], RunTime(ms), 6431
[OVERALL], Throughput(ops/sec), 155.49681231534754
[READ], Operations, 1000
[READ], AverageLatency(us), 2907.358
[READ], MinLatency(us), 938
[READ], MaxLatency(us), 42943
[READ], 95thPercentileLatency(us), 5459
[READ], 99thPercentileLatency(us), 9319
[READ], Return=OK, 1000
```

## Links

http://wiki.github.com/brianfrankcooper/YCSB/
https://labs.yahoo.com/news/yahoo-cloud-serving-benchmark/
ycsb-users@yahoogroups.com

## Getting Started

1. Download the [latest release of YCSB](https://github.com/brianfrankcooper/YCSB/releases/latest):

   ```sh
   curl -O --location https://github.com/brianfrankcooper/YCSB/releases/download/0.15.0/ycsb-0.15.0.tar.gz
   tar xfvz ycsb-0.15.0.tar.gz
   cd ycsb-0.15.0
   ```

2. Set up a database to benchmark. There is a README file under each binding
   directory.

3. Run YCSB command.

   On Linux:

   ```sh
   bin/ycsb.sh load basic -P workloads/workloada
   bin/ycsb.sh run basic -P workloads/workloada
   ```

   On Windows:

   ```bat
   bin/ycsb.bat load basic -P workloads\workloada
   bin/ycsb.bat run basic -P workloads\workloada
   ```

Running the `ycsb` command without any argument will print the usage.

See https://github.com/brianfrankcooper/YCSB/wiki/Running-a-Workload
for a detailed documentation on how to run a workload.

See https://github.com/brianfrankcooper/YCSB/wiki/Core-Properties for
the list of available workload properties.

## Building from source

YCSB requires the use of Maven 3; if you use Maven 2, you may see [errors
such as these](https://github.com/brianfrankcooper/YCSB/issues/406).

To build the full distribution, with all database bindings:

    mvn clean package

To build a single database binding:

    mvn -pl com.yahoo.ycsb:mongodb-binding -am clean package
