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

```
root@mail:~# sysbench --test=cpu --cpu-max-prime=20000 --num-threads=16 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 16

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          10.6297s
    total number of events:              10000
    total time taken by event execution: 169.6363
    per-request statistics:
         min:                                  4.03ms
         avg:                                 16.96ms
         max:                                 52.40ms
         approx.  95 percentile:              29.20ms

Threads fairness:
    events (avg/stddev):           625.0000/5.96
    execution time (avg/stddev):   10.6023/0.02

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

```
root@mail:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.1.11
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 4096MB)
Jobs: 1 (f=1): [m(1)] [100.0% done] [35880KB/11716KB/0KB /s] [8970/2929/0 iops] [eta 00m:00s] 
test: (groupid=0, jobs=1): err= 0: pid=18895: Sat Jul 16 14:20:49 2016
  read : io=3071.7MB, bw=74475KB/s, iops=18618, runt= 42234msec
  write: io=1024.4MB, bw=24836KB/s, iops=6208, runt= 42234msec
  cpu          : usr=11.65%, sys=51.43%, ctx=73278, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=74475KB/s, minb=74475KB/s, maxb=74475KB/s, mint=42234msec, maxt=42234msec
  WRITE: io=1024.4MB, aggrb=24835KB/s, minb=24835KB/s, maxb=24835KB/s, mint=42234msec, maxt=42234msec

Disk stats (read/write):
  vda: ios=785705/262053, merge=0/19, ticks=1877252/297236, in_queue=2174800, util=99.80%
```
