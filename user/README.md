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
