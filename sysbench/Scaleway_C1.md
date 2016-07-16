# CPU
```
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
```

```
root@stats:~# sysbench --test=cpu --cpu-max-prime=20000 --num-threads=16 run
sysbench 0.4.12:  multi-threaded system evaluation benchmark

Running the test with following options:
Number of threads: 16

Doing CPU performance benchmark

Threads started!
Done.

Maximum prime number checked in CPU test: 20000


Test execution summary:
    total time:                          23.1121s
    total number of events:              10000
    total time taken by event execution: 368.6029
    per-request statistics:
         min:                                  4.59ms
         avg:                                 36.86ms
         max:                                141.14ms
         approx.  95 percentile:              84.57ms

Threads fairness:
    events (avg/stddev):           625.0000/1.27
    execution time (avg/stddev):   23.0377/0.04


```
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


```
root@stats:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.1.3
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 4096MB)
Jobs: 1 (f=1): [m] [100.0% done] [117.2MB/40347KB/0KB /s] [29.1K/10.9K/0 iops] [eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=27742: Sat Jul 16 12:18:27 2016
  read : io=3071.7MB, bw=91944KB/s, iops=22985, runt= 34210msec
  write: io=1024.4MB, bw=30661KB/s, iops=7665, runt= 34210msec
  cpu          : usr=15.76%, sys=61.07%, ctx=5766, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=91943KB/s, minb=91943KB/s, maxb=91943KB/s, mint=34210msec, maxt=34210msec
  WRITE: io=1024.4MB, aggrb=30661KB/s, minb=30661KB/s, maxb=30661KB/s, mint=34210msec, maxt=34210msec

Disk stats (read/write):
  vda: ios=778343/259607, merge=0/16, ticks=768670/229640, in_queue=997910, util=98.90%
```

