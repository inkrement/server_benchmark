# CPU

```
root@mail:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          42.9285s
    total number of events:              10000
    total time taken by event execution: 42.9199
    per-request statistics:
         min:                                  4.03ms
         avg:                                  4.29ms
         max:                                 15.26ms
         approx.  95 percentile:               4.81ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   42.9199/0.00
```

# Memory 

```
root@mail:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
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

Operations performed: 10240 ( 4216.35 ops/sec)

10240.00 MB transferred (4216.35 MB/sec)


Test execution summary:
    total time:                          2.4286s
    total number of events:              10240
    total time taken by event execution: 2.4239
    per-request statistics:
         min:                                  0.14ms
         avg:                                  0.24ms
         max:                                 14.43ms
         approx.  95 percentile:               0.28ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.4239/0.00
```

# File System

```
root@mail:~# sysbench --test=fileio --file-total-size=25G --file-test-mode=rndrw --init-rng=on --max-time=300 --max-requests=0 run
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

Operations performed:  329820 Read, 219880 Write, 703501 Other = 1253201 Total
Read 5.0327Gb  Written 3.3551Gb  Total transferred 8.3878Gb  (28.63Mb/sec)
 1832.33 Requests/sec executed

Test execution summary:
    total time:                          300.0005s
    total number of events:              549700
    total time taken by event execution: 145.8976
    per-request statistics:
         min:                                  0.00ms
         avg:                                  0.27ms
         max:                                 23.69ms
         approx.  95 percentile:               0.52ms

Threads fairness:
    events (avg/stddev):           549700.0000/0.00
    execution time (avg/stddev):   145.8976/0.00
```
