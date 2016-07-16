# CPU

```
root@web2:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          46.1326s
    total number of events:              10000
    total time taken by event execution: 46.1283
    per-request statistics:
         min:                                  4.59ms
         avg:                                  4.61ms
         max:                                  6.18ms
         approx.  95 percentile:               4.65ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   46.1283/0.00
```

# Memory 

```
root@web2:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
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

Operations performed: 10240 ( 3581.45 ops/sec)

10240.00 MB transferred (3581.45 MB/sec)


Test execution summary:
    total time:                          2.8592s
    total number of events:              10240
    total time taken by event execution: 2.8538
    per-request statistics:
         min:                                  0.26ms
         avg:                                  0.28ms
         max:                                  1.46ms
         approx.  95 percentile:               0.30ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.8538/0.00
```


# File System

```
root@web2:~# sysbench --test=fileio --file-total-size=25G --file-test-mode=rndrw --init-rng=on --max-time=300 --max-requests=0 run
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

Operations performed:  15060 Read, 10040 Write, 32001 Other = 57101 Total
Read 235.31Mb  Written 156.88Mb  Total transferred 392.19Mb  (1.3072Mb/sec)
   83.66 Requests/sec executed

Test execution summary:
    total time:                          300.0104s
    total number of events:              25100
    total time taken by event execution: 6.1333
    per-request statistics:
         min:                                  0.01ms
         avg:                                  0.24ms
         max:                                 12.87ms
         approx.  95 percentile:               0.54ms

Threads fairness:
    events (avg/stddev):           25100.0000/0.00
    execution time (avg/stddev):   6.1333/0.00
```
