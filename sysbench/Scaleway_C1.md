# CPU

root@stats:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          46.2201s
    total number of events:              10000
    total time taken by event execution: 46.2152
    per-request statistics:
         min:                                  4.59ms
         avg:                                  4.62ms
         max:                                  5.75ms
         approx.  95 percentile:               4.68ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   46.2152/0.00


# Memory

```
root@stats:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing memory operations speed test
Memory block size: 1024K

Memory transfer size: 10240M

Memory operations type: write
Memory scope type: global
Threads started!
Done.

Operations performed: 10240 ( 3875.99 ops/sec)

10240.00 MB transferred (3875.99 MB/sec)


Test execution summary:
    total time:                          2.6419s
    total number of events:              10240
    total time taken by event execution: 2.6377
    per-request statistics:
         min:                                  0.24ms
         avg:                                  0.26ms
         max:                                  0.38ms
         approx.  95 percentile:               0.28ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.6377/0.00
```

# File System

```
root@stats:~# sysbench --test=fileio --file-total-size=25G --file-test-mode=rndrw --init-rng=on --max-time=300 --max-requests=0 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1
Initializing random number generator from timer.


Extra file open flags: 0
128 files, 200Mb each
25Gb total file size
Block size 16Kb
Number of random requests for random IO: 0
Read/Write ratio for combined random IO test: 1.50
Periodic FSYNC enabled, calling fsync() each 100 requests.
Calling fsync() at the end of test, Enabled.
Using synchronous I/O mode
Doing random r/w test
Threads started!
Time limit exceeded, exiting...
Done.

Operations performed:  40740 Read, 27160 Write, 86863 Other = 154763 Total
Read 636.56Mb  Written 424.38Mb  Total transferred 1.0361Gb  (3.5365Mb/sec)
  226.33 Requests/sec executed

Test execution summary:
    total time:                          300.0003s
    total number of events:              67900
    total time taken by event execution: 25.6971
    per-request statistics:
         min:                                  0.01ms
         avg:                                  0.38ms
         max:                                 21.42ms
         approx.  95 percentile:               0.71ms

Threads fairness:
    events (avg/stddev):           67900.0000/0.00
    execution time (avg/stddev):   25.6971/0.00

```
