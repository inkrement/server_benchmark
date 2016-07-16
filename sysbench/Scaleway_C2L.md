# CPU

```
root@web4:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          45.8844s
    total number of events:              10000
    total time taken by event execution: 45.8825
    per-request statistics:
         min:                                  4.59ms
         avg:                                  4.59ms
         max:                                  7.53ms
         approx.  95 percentile:               4.59ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   45.8825/0.00

```
