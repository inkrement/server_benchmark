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

```

```
root@justrocketscience:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.1.3
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 4096MB)
Jobs: 1 (f=1): [m] [100.0% done] [109.7MB/37884KB/0KB /s] [28.7K/9471/0 iops] [eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=3734: Sat Jul 16 08:13:26 2016
  read : io=3071.7MB, bw=97414KB/s, iops=24353, runt= 32289msec
  write: io=1024.4MB, bw=32485KB/s, iops=8121, runt= 32289msec
  cpu          : usr=11.37%, sys=36.99%, ctx=36294, majf=0, minf=22
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=786347/w=262229/d=0, short=r=0/w=0/d=0

Run status group 0 (all jobs):
   READ: io=3071.7MB, aggrb=97413KB/s, minb=97413KB/s, maxb=97413KB/s, mint=32289msec, maxt=32289msec
  WRITE: io=1024.4MB, aggrb=32485KB/s, minb=32485KB/s, maxb=32485KB/s, mint=32289msec, maxt=32289msec

Disk stats (read/write):
  vda: ios=786955/262066, merge=0/50, ticks=664836/935700, in_queue=1600264, util=98.91%
```
