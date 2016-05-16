# CPU

```
root@justrocketscience:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          54.5396s
    total number of events:              10000
    total time taken by event execution: 54.5287
    per-request statistics:
         min:                                  3.81ms
         avg:                                  5.45ms
         max:                                 26.54ms
         approx.  95 percentile:               7.67ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   54.5287/0.00

```

# Memory

```
root@justrocketscience:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
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

Operations performed: 10240 ( 4285.66 ops/sec)

10240.00 MB transferred (4285.66 MB/sec)


Test execution summary:
    total time:                          2.3894s
    total number of events:              10240
    total time taken by event execution: 2.3833
    per-request statistics:
         min:                                  0.15ms
         avg:                                  0.23ms
         max:                                  6.59ms
         approx.  95 percentile:               0.44ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.3833/0.00
```

# File System

```
root@justrocketscience:~# sysbench --test=fileio --file-total-size=20G --file-test-mode=rndrw --init-rng=on --max-time=300 --max-requests=0 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1
Initializing random number generator from timer.


Extra file open flags: 0
128 files, 160Mb each
20Gb total file size
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

Operations performed:  421740 Read, 281160 Write, 899653 Other = 1602553 Total
Read 6.4352Gb  Written 4.2902Gb  Total transferred 10.725Gb  (36.609Mb/sec)
 2342.97 Requests/sec executed

Test execution summary:
    total time:                          300.0035s
    total number of events:              702900
    total time taken by event execution: 165.9392
    per-request statistics:
         min:                                  0.01ms
         avg:                                  0.24ms
         max:                                 25.72ms
         approx.  95 percentile:               0.73ms

Threads fairness:
    events (avg/stddev):           702900.0000/0.00
    execution time (avg/stddev):   165.9392/0.00

``
