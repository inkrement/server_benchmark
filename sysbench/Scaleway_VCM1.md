
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

```
root@web3:~# sysbench --test=cpu --cpu-max-prime=20000 --num-threads=16 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 16

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          11.5526s
    total number of events:              10000
    total time taken by event execution: 184.4547
    per-request statistics:
         min:                                  4.59ms
         avg:                                 18.45ms
         max:                                 54.66ms
         approx.  95 percentile:              34.66ms

Threads fairness:
    events (avg/stddev):           625.0000/8.57
    execution time (avg/stddev):   11.5284/0.02

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

```
root@web3:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.2.10
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 4096MB)
Jobs: 1 (f=1): [m(1)] [96.6% done] [133.6MB/45606KB/0KB /s] [34.2K/11.5K/0 iops] [eta 00m:01s]
test: (groupid=0, jobs=1): err= 0: pid=4986: Sat Jul 16 12:06:51 2016
  read : io=3071.7MB, bw=112770KB/s, iops=28192, runt= 27892msec
  write: io=1024.4MB, bw=37606KB/s, iops=9401, runt= 27892msec
  cpu          : usr=16.82%, sys=54.93%, ctx=7598, majf=0, minf=9
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0, drop=r=0/w=0/d=0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=112770KB/s, minb=112770KB/s, maxb=112770KB/s, mint=27892msec, maxt=27892msec
  WRITE: io=1024.4MB, aggrb=37606KB/s, minb=37606KB/s, maxb=37606KB/s, mint=27892msec, maxt=27892msec

Disk stats (read/write):
  vda: ios=782664/261038, merge=0/5, ticks=695730/263380, in_queue=958600, util=99.10%
```
