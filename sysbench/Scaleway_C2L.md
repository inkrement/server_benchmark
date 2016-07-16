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

```
root@web4:~# sysbench --test=cpu --cpu-max-prime=20000 --num-threads=16 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 16

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          5.7398s
    total number of events:              10000
    total time taken by event execution: 91.5356
    per-request statistics:
         min:                                  4.59ms
         avg:                                  9.15ms
         max:                                 44.60ms
         approx.  95 percentile:              24.59ms

Threads fairness:
    events (avg/stddev):           625.0000/17.98
    execution time (avg/stddev):   5.7210/0.01

```

# Memory
```
root@web4:~# sysbench --test=memory --memory-block-size=1M --memory-total-size=10G run
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

Operations performed: 10240 ( 4005.30 ops/sec)

10240.00 MB transferred (4005.30 MB/sec)


Test execution summary:
    total time:                          2.5566s
    total number of events:              10240
    total time taken by event execution: 2.5520
    per-request statistics:
         min:                                  0.24ms
         avg:                                  0.25ms
         max:                                  0.30ms
         approx.  95 percentile:               0.25ms

Threads fairness:
    events (avg/stddev):           10240.0000/0.00
    execution time (avg/stddev):   2.5520/0.00

```


# File System
```
root@web4:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=/dev/sda --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75 
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.2.10
Starting 1 process
Jobs: 1 (f=1): [m(1)] [100.0% done] [147.7MB/50640KB/0KB /s] [37.8K/12.7K/0 iops] [eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=4901: Sat Jul 16 12:01:21 2016
  read : io=3071.7MB, bw=151025KB/s, iops=37756, runt= 20827msec
  write: io=1024.4MB, bw=50363KB/s, iops=12590, runt= 20827msec
  cpu          : usr=20.50%, sys=77.69%, ctx=13121, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0, drop=r=0/w=0/d=0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=151024KB/s, minb=151024KB/s, maxb=151024KB/s, mint=20827msec, maxt=20827msec
  WRITE: io=1024.4MB, aggrb=50363KB/s, minb=50363KB/s, maxb=50363KB/s, mint=20827msec, maxt=20827msec

Disk stats (read/write):
  sda: ios=778188/259896, merge=1763/230, ticks=931910/332020, in_queue=1264400, util=99.67%
```
