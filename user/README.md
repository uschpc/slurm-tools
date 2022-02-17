# User tools

A collection of various user-oriented Slurm tools.

## Installation

These tools are either Bash or Python scripts, so you can simply download and run them as executables. If needed, install Bash or Python and change the file permissions to allow execute permission (e.g., `chmod 755 jobinfo`). If desired, add the executable files to a directory on your `PATH`.

## Usage

### myqueue

Display job queue information for user.

```
$ myqueue
------------------------------------------------------------------------------
      Job ID     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ------------ ---------- -------- ----------- --------------------
487418            sim2.sl       main  PENDING        0:00         (Dependency)
486794             sim.sl       main  RUNNING  1-12:13:20               d05-06
```

### cqueue

Display job queue information.

```
$ cqueue -p largemem
-----------------------------------------------------------------------------------------
      Job ID       User     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ---------- ------------ ---------- -------- ----------- --------------------
7453378            jesp Run_do52bran   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7453379            jesp Run_do6b.job   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7473836         ttrojan sys/dashboar   largemem  RUNNING     2:42:28               a04-10
7449562            snet run_study_4x   largemem  RUNNING  2-23:17:10               a02-10
7453377            jesp Run_do51bran   largemem  RUNNING  2-17:02:07               a01-10
7470944          huy435    rfmixchr1   largemem  RUNNING    21:18:51        a02-10,a04-10
```

### jobhist

Display a compact history of user's jobs with basic job information.

```
$ jobhist
-----------------------------------------------------------------------------------------------
 Startdate        Job ID     Job Name  Partition      State     Elapsed Nodes CPUs  Memory GPUs
---------- ------------- ------------ ---------- ---------- ----------- ----- ---- ------- ----
2021-06-25        484933  debugsim.sl      debug     FAILED    00:00:05     1    4    30Gn 0
2021-06-25        484934  debugsim.sl      debug  COMPLETED    00:00:19     1    4    30Gn 0
2021-06-26        486288  interactive       main  COMPLETED    00:20:53     1   16     2Gc 0
2021-06-27        486290  interactive      debug    TIMEOUT    00:30:02     1   16     2Gc 0
2021-06-28        486624       sim.sl    oneweek  COMPLETED  3-00:30:22     1   16   120Gn 0
```

### jobinfo

Display detailed job information.

```
$ jobinfo 483699
Job ID               : 483699
Job name             : simdebug.sl
User                 : ttrojan
Account              : ttrojan_123
Working directory    : /project/ttrojan_123/sim
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
Reserved memory      : 61352M/node
Max memory used      : 64.74G (estimate)
Memory efficiency    : 54.03%
Max disk write       : 1.04M
Max disk read        : 14.42M
```


### nodeinfo

Display node information by partition, CPU/GPU models, and state.

```
$ nodeinfo
------------------------------------------------------------------------------------------------------------------------------
Partition    Timelimit   CPU model     CPUs/ NUMA   GPU model          Memory(MB)/ State  Nodes Nodelist
                                       node  D:C:T                     node
------------ ----------- ------------- ----- ------ ------------------ ----------- ------ ----- ------------------------------
debug        1:00:00     xeon-2650v2   16    2:8:1  (null)             63400       idle   4     e05-[42,76,78,80]
debug        1:00:00     xeon-2640v3   16    2:8:1  gpu:k40:2(S:0-1)   63400       idle   1     e09-18
debug        1:00:00     xeon-2640v4   20    2:10:1 gpu:p100:2(S:0-1)  128000      idle   1     e23-02
epyc-64      2-00:00:00  epyc-7513     64    8:8:1  (null)             256000      down*  2     a02-05,a03-04
epyc-64      2-00:00:00  epyc-7513     64    8:8:1  (null)             256000      mix    2     a01-05,a02-14
epyc-64      2-00:00:00  epyc-7542     64    2:32:1 (null)             256000      mix    3     b22-[05,09,22]
epyc-64      2-00:00:00  epyc-7513     64    8:8:1  (null)             256000      alloc  43    a01-[02-04,13-14,16-19],a02-[0
epyc-64      2-00:00:00  epyc-7542     64    2:32:1 (null)             256000      alloc  25    b22-[01,03,06-08,12-21,23-32]
epyc-64      2-00:00:00  epyc-7513     64    8:8:1  (null)             256000      idle   14    a01-[07-09,11-12],a02-13,a03-[
epyc-64      2-00:00:00  epyc-7542     64    2:32:1 (null)             256000      idle   4     b22-[02,04,10-11]
main*        2-00:00:00  xeon-2640v4   20    2:10:1 gpu:k40:2          63400       down*  1     e16-05
main*        2-00:00:00  xeon-4116     24    2:12:1 (null)             94000+      mix    65    d05-[06,10-15,26-40,42],d06-[1
main*        2-00:00:00  xeon-2640v4   20    2:10:1 (null)             64000       mix    75    d17-[03-40],d18-[01-22,24-38]
main*        2-00:00:00  xeon-2640v3   16    2:8:1  (null)             63400       mix    79    e06-[01-04,06-17,19-22],e11-[2
main*        2-00:00:00  xeon-2640v3   16    2:8:1  gpu:k40:2(S:0-1)   63400       mix    17    e07-[01-16,18]
main*        2-00:00:00  xeon-2640v4   20    2:10:1 gpu:k40:2(S:0-1)   63400       mix    39    e16-[01-04,06-24],e17-[01-02,0
main*        2-00:00:00  xeon-4116     24    2:12:1 (null)             94000+      alloc  15    d05-[07-09,41],d06-[16,27-28],
main*        2-00:00:00  xeon-2640v4   20    2:10:1 (null)             64000       alloc  1     d18-23
main*        2-00:00:00  xeon-2640v3   16    2:8:1  (null)             63400       alloc  2     e06-18,e15-12
main*        2-00:00:00  xeon-2640v4   20    2:10:1 gpu:k40:2(S:0-1)   63400       alloc  1     e17-03
gpu          2-00:00:00  xeon-6130     32    2:16:1 gpu:v100:2(S:0-1)  191000      drain  1     d11-04
gpu          2-00:00:00  epyc-7513     64    8:8:1  gpu:a100:2(S:0-7)  256000      mix    7     a01-[01,06,15,20],b01-[01,15,2
gpu          2-00:00:00  epyc-7282     32    2:16:1 gpu:a40:2(S:0-1)   256000      mix    4     a02-[01,06,15],a03-06
gpu          2-00:00:00  xeon-6130     32    2:16:1 gpu:v100:2(S:0-1)  191000      mix    21    d11-[02-03],d13-[02-11],d14-[0
gpu          2-00:00:00  xeon-2640v4   20    2:10:1 gpu:p100:2(S:0-1)  128000      mix    23    d23-[10,13-14],e21-[04-16],e22
gpu          2-00:00:00  epyc-7513     64    8:8:1  gpu:a100:2(S:0-7)  256000      alloc  2     b01-06,b02-01
gpu          2-00:00:00  epyc-7282     32    2:16:1 gpu:a40:2(S:0-1)   256000      idle   8     a02-20,a03-[01,15,20],a04-[01,
gpu          2-00:00:00  epyc-7513     64    8:8:1  gpu:a100:2(S:0-7)  256000      idle   3     b02-[06,15,20]
gpu          2-00:00:00  xeon-6130     32    2:16:1 gpu:v100:2(S:0-1)  191000      idle   7     d14-[12-18]
gpu          2-00:00:00  xeon-2640v4   20    2:10:1 gpu:p100:2(S:0-1)  128000      idle   15    d23-[15-16],e21-[01-03],e22-[0
oneweek      7-00:00:00  xeon-2650v2   16    2:8:1  (null)             128000+     mix    8     e01-46,e02-[41,56-57,60,73,76,
oneweek      7-00:00:00  xeon-2640v3   16    2:8:1  (null)             63400       mix    1     e06-24
oneweek      7-00:00:00  xeon-2650v2   16    2:8:1  (null)             128000+     alloc  21    e01-[52,60,62,64,76],e02-[40,4
oneweek      7-00:00:00  xeon-2650v2   16    2:8:1  (null)             128000+     idle   18    e01-48,e02-[42-46,58-59,61-69,
oneweek      7-00:00:00  xeon-2640v3   16    2:8:1  (null)             63400       idle   1     e10-12
largemem     7-00:00:00  epyc-7513     64    8:8:1  (null)             1024000     mix    3     a01-10,a02-10,a04-10
largemem     7-00:00:00  epyc-7513     64    8:8:1  (null)             1024000     idle   1     a03-10
```
