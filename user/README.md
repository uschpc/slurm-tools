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

Print detailed information for a pending, running, or completed job.

```
$ jobinfo 483699
Job ID               : 483699
Job name             : sim.sl
User                 : ttrojan
Account              : ttrojan_123
Cluster              : discovery
Partition            : oneweek
Nodes                : 1
Nodelist             : e01-76
CPUs                 : 16
GPUs                 : 0
State                : FAILED
Exit code            : 1:0
Submit time          : 2021-06-22T12:38:06
Start time           : 2021-06-22T12:38:15
End time             : 2021-06-25T12:40:53
Wait time            :   00:00:09
Reserved walltime    : 3-07:00:00
Used walltime        : 3-00:02:38
Used CPU time        : 3-14:00:01
% User (computation) : 93.82%
% System (I/O)       :  6.18%
Memory reserved      : 248G/node
Max memory used      : 218.60G (e01-76)
Max disk write       : 143.41G (e01-76)
Max disk read        : 352.60G (e01-76)
```
