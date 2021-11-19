# User tools

A collection of various user-oriented Slurm tools.

## Installation

These tools are either Bash or Python scripts, so you can simply download and run them as executables. If needed, change the file permissions to allow execute permission. If desired, add the executable files to a directory on your `PATH`.

## Usage

### myqueue

Print job queue information for user.

```
$ myqueue
------------------------------------------------------------------------------
      Job ID     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ------------ ---------- -------- ----------- --------------------
487418            sim2.sl       main  PENDING        0:00         (Dependency)
486794             sim.sl       main  RUNNING  1-12:13:20               d05-06
```

### jobhist

Print a compact history of user's jobs with basic job information.

```
$ jobhist
-----------------------------------------------------------------------------------------
 Startdate        Job ID     Job Name  Partition      State    Elapsed Nodes CPUs  Memory
---------- ------------- ------------ ---------- ---------- ---------- ----- ---- -------
2021-06-25 484933         debugsim.sl      debug     FAILED   00:00:05     1    4    30Gn
2021-06-25 484934         debugsim.sl      debug  COMPLETED   00:00:19     1    4    30Gn
2021-06-26 486288         interactive       main  COMPLETED   00:20:53     1   16     2Gc
2021-06-27 486290         interactive      debug    TIMEOUT   00:30:02     1   16     2Gc
2021-06-28 486624              sim.sl    oneweek  COMPLETED 3-00:30:22     1   16   120Gn
```

### jobinfo

Print detailed information for a job.

```
$ jobinfo 483699
Job ID               : 483699
Job name             : simdebug.sl
User                 : ttrojan
Account              : ttrojan_123
Cluster              : discovery
Partition            : debug
Nodes                : 2
Nodelist             : e05-[42,76]
Tasks                : 32
CPUs                 : 32
GPUs                 : 0
State                : COMPLETED
Exit code            : 0:0
Submit time          : 2021-08-26T14:56:23
Start time           : 2021-08-26T14:56:24
End time             : 2021-08-26T14:57:32
Wait time            : 00:00:01
Reserved walltime    : 00:10:00
Used walltime        : 00:01:08
Used CPU walltime    : 00:36:16
Used CPU time        : 00:35:18
% User (computation) : 96.35%
% System (I/O)       :  3.65%
CPU efficiency       : 97.37%
Memory reserved      : 61352M/node
Max memory used      : 64.74G (estimate)
Memory efficiency    : 54.03%
Max disk write       : 1.04M
Max disk read        : 14.42M
```


### nodeinfo

Display node information by partition, CPU/GPU model, and state.

```
$ nodeinfo
---------------------------------------------------------------------------------------------------------------------
Partition    CPU model     GPU model          State  Nodes CPUs Memory(MB) Timelimit   Nodelist
------------ ------------- ------------------ ------ ----- ---- ---------- ----------- ------------------------------
debug        xeon-2640     gpu:k20:2(S:0-1)   idle   1     16   63000      1:00:00     a02-26
debug        xeon-2650v2   (null)             idle   4     16   63400      1:00:00     e05-[42,76,78,80]
debug        xeon-2640v3   gpu:k40:2(S:0-1)   idle   1     16   63400      1:00:00     e09-18
debug        xeon-2640v4   gpu:p100:2(S:0-1)  idle   1     20   128000     1:00:00     e23-02
epyc-64      epyc-7513     (null)             mix    4     64   256000     2-00:00:00  a01-09,a02-[07-09]
epyc-64      epyc-7542     (null)             mix    5     64   256000     2-00:00:00  b22-[28-32]
epyc-64      epyc-7513     (null)             alloc  21    64   256000     2-00:00:00  a01-[07-08,11-14,16-19],a02-[0
epyc-64      epyc-7542     (null)             alloc  27    64   256000     2-00:00:00  b22-[01-27]
epyc-64      epyc-7513     (null)             idle   36    64   256000     2-00:00:00  a01-[02-05],a02-[13-14,16-19],
main*        xeon-2640v3   (null)             drain  3     16   63400      2-00:00:00  e06-[05,24],e10-12
main*        xeon-4116     (null)             mix    70    24   94000+     2-00:00:00  d05-[06-15,26-42],d06-[15,17-2
main*        xeon-2640v4   (null)             mix    65    20   63400+     2-00:00:00  d17-[03-04,07,11-13,15-16,18-1
main*        xeon-2640v3   (null)             mix    52    16   63400      2-00:00:00  e06-[01-04,06-12,14-15,17-18,2
main*        xeon-2640v3   gpu:k40:2(S:0-1)   mix    13    16   63400      2-00:00:00  e07-[01-04,08,10-16,18]
main*        xeon-2640v4   gpu:k40:2(S:0-1)   mix    37    20   63400      2-00:00:00  e16-[02-05,07-20,22-24],e17-[0
main*        xeon-4116     (null)             alloc  10    24   94000+     2-00:00:00  d06-16,d11-[10-13,16,20,29,37,
main*        xeon-2640v4   (null)             alloc  13    20   64000      2-00:00:00  d17-[05-06,08-10,14,17,20,23],
main*        xeon-2640v3   (null)             alloc  9     16   63400      2-00:00:00  e06-19,e11-47,e13-[28-33],e14-
main*        xeon-2640v3   gpu:k40:2(S:0-1)   alloc  4     16   63400      2-00:00:00  e07-[05-07,09]
main*        xeon-2640v4   gpu:k40:2(S:0-1)   alloc  2     20   63400      2-00:00:00  e16-[01,06]
main*        xeon-2640v4   (null)             idle   2     20   64000      2-00:00:00  d17-[21-22]
main*        xeon-2640v3   (null)             idle   20    16   63400      2-00:00:00  e06-[13,16],e13-[37-38,41-42],
main*        xeon-2640v4   gpu:k40:2(S:0-1)   idle   2     20   63400      2-00:00:00  e16-21,e17-02
gpu          epyc-7282     gpu:a40:2(S:0-1)   mix    2     32   256000     2-00:00:00  a02-[01,15]
gpu          xeon-6130     gpu:v100:2(S:0-1)  mix    2     32   191000     2-00:00:00  d11-02,d13-03
gpu          xeon-2640v4   gpu:p100:2(S:0-1)  mix    11    20   128000     2-00:00:00  d23-[10,13-14],e21-[01-08]
gpu          epyc-7513     gpu:a100:2(S:0-7)  alloc  8     64   256000     2-00:00:00  a01-[01,15,20],b01-[01,06,20],
gpu          xeon-6130     gpu:v100:2(S:0-1)  alloc  16    32   191000     2-00:00:00  d11-[03-04],d14-[03-14,16-17]
gpu          xeon-2640v4   gpu:p100:2(S:0-1)  alloc  18    20   128000     2-00:00:00  e21-[09-16],e22-[01-10]
gpu          epyc-7513     gpu:a100:2(S:0-7)  idle   4     64   256000     2-00:00:00  a01-06,b01-15,b02-[15,20]
gpu          epyc-7282     gpu:a40:2(S:0-1)   idle   10    32   256000     2-00:00:00  a02-[06,20],a03-[01,06,15,20],
gpu          xeon-6130     gpu:v100:2(S:0-1)  idle   11    32   191000     2-00:00:00  d13-[02,04-11],d14-[15,18]
gpu          xeon-2640v4   gpu:p100:2(S:0-1)  idle   9     20   128000     2-00:00:00  d23-[15-16],e22-[11-16],e23-01
oneweek      xeon-2650v2   (null)             mix    27    16   128000+    7-00:00:00  e01-[52,64,76],e02-[40,42,46,4
oneweek      xeon-2650v2   (null)             alloc  16    16   128000     7-00:00:00  e01-[46,48,60,62],e02-[43,50-5
oneweek      xeon-2650v2   (null)             idle   4     16   128000     7-00:00:00  e02-[41,44-45,56]
largemem     xeon-4850     (null)             drain* 3     40   1031600    7-00:00:00  a16-[02-04]
largemem     epyc-7513     (null)             mix    2     64   1024000    7-00:00:00  a01-10,a02-10
largemem     epyc-7513     (null)             idle   2     64   1024000    7-00:00:00  a03-10,a04-10
```
