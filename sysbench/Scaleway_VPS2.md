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

```
root@web2:~# sysbench --test=cpu --cpu-max-prime=20000 --num-threads=16 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 16

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          13.8951s
    total number of events:              10000
    total time taken by event execution: 221.8708
    per-request statistics:
         min:                                  4.59ms
         avg:                                 22.19ms
         max:                                179.08ms
         approx.  95 percentile:              57.91ms

Threads fairness:
    events (avg/stddev):           625.0000/15.66
    execution time (avg/stddev):   13.8669/0.01

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

```
root@web2:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.2.10
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 4096MB)
Jobs: 1 (f=1): [m(1)] [100.0% done] [34493KB/11556KB/0KB /s] [8623/2889/0 iops] [eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=30364: Sat Jul 16 14:24:12 2016
  read : io=3071.7MB, bw=55552KB/s, iops=13887, runt= 56621msec
  write: io=1024.4MB, bw=18525KB/s, iops=4631, runt= 56621msec
  cpu          : usr=16.94%, sys=50.37%, ctx=12706, majf=0, minf=9
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0, drop=r=0/w=0/d=0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=55551KB/s, minb=55551KB/s, maxb=55551KB/s, mint=56621msec, maxt=56621msec
  WRITE: io=1024.4MB, aggrb=18525KB/s, minb=18525KB/s, maxb=18525KB/s, mint=56621msec, maxt=56621msec

Disk stats (read/write):
  vda: ios=782344/260933, merge=0/11, ticks=1530780/536270, in_queue=2066420, util=98.60%
```
