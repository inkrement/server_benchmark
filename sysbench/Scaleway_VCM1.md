
# CPU
```
root@web3:~# sysbench --test=cpu --cpu-max-prime=20000 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 1

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          46.1131s
    total number of events:              10000
    total time taken by event execution: 46.1087
    per-request statistics:
         min:                                  4.59ms
         avg:                                  4.61ms
         max:                                  7.85ms
         approx.  95 percentile:               4.65ms

Threads fairness:
    events (avg/stddev):           10000.0000/0.00
    execution time (avg/stddev):   46.1087/0.00

```

# Memory

```
root@web3:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
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

Operations performed: 10240 ( 3855.80 ops/sec)

10240.00 MB transferred (3855.80 MB/sec)


Test execution summary:
    total time:                          2.6557s
    total number of events:              10240
    total time taken by event execution: 2.6509
    per-request statistics:
         min:                                  0.25ms
         avg:                                  0.26ms
         max:                                  0.46ms
         approx.  95 percentile:               0.28ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.6509/0.00

```

# Filesystem

```
root@web3:~# sysbench --test=fileio --file-total-size=25G prepare
sysbench 0.4.12:  multi-threaded system evaluation benchmark

128 files, 204800Kb each, 25600Mb total
Creating files for the test...
root@web3:~# sysbench --test=fileio --file-total-size=25G --file-test-mode=rndrw --init-rng=on --max-time=300 --max-requests=0 run
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

Operations performed:  11460 Read, 7640 Write, 24431 Other = 43531 Total
Read 179.06Mb  Written 119.38Mb  Total transferred 298.44Mb  (1018.6Kb/sec)
   63.66 Requests/sec executed

Test execution summary:
    total time:                          300.0095s
    total number of events:              19100
    total time taken by event execution: 7.3451
    per-request statistics:
         min:                                  0.01ms
         avg:                                  0.38ms
         max:                                 17.92ms
         approx.  95 percentile:               0.73ms

Threads fairness:
    events (avg/stddev):           19100.0000/0.00
    execution time (avg/stddev):   7.3451/0.00

```
