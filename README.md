# Slurm CLI tools

A collection of CLI tools used on CARC HPC clusters for various Slurm tasks and queries.

## Installation

The CLI tools are Python scripts that rely only on the Python standard library and use the argparse library. Some scripts may need to be modified to run on other HPC clusters, depending on the Python version available, Slurm configuration, etc. Check the notes in each script for more information.

To install, simply clone the repo:

```
git clone --depth 1 https://github.com/uschpc/slurm-tools.git
```

The scripts will be downloaded with execute permissions. If desired, move the scripts to another directory, such as a directory on `PATH`. If needed, install and/or load a compatible version of Python.

## Usage

Each script contains help and usage information that can be viewed with the `--help` flag (e.g., `jobinfo --help`).

The scripts are described and shown with example output below.

### myaccount

View account information for user.

```
$ myaccount
-----------------------------------------------------------------
Cluster accounts
-----------------------------------------------------------------
User       Account         Cluster    Default         QOS
---------- --------------- ---------- --------------- -----------
ttrojan    ttrojan_123     discovery  ttrojan_123     normal
ttrojan    ttrojan_125     discovery  ttrojan_123     normal

-----------------------------------------------------------------
Cluster account service units (SUs)
-----------------------------------------------------------------
Account           Limit           Usage           Remaining
----------------- --------------- --------------- ---------------
ttrojan_123       12000000        422699          11577301
ttrojan_125       n/a             839856          n/a

-----------------------------------------------------------------
Allowed cluster partitions
-----------------------------------------------------------------
Partition      Allowed accounts
-------------- --------------------------------------------------
trojan         ttrojan_125
shared         ALL
```

### noderes

View available resources on nodes.

```
$ noderes -p debug
-------------------------------------------------------------------
Node      Partition     State         CPU      GPU Free   Free Free
                                    Model    Model CPUs Memory GPUs
------ ------------ --------- ----------- -------- ---- ------ ----
b11-09        debug      idle   epyc-7313      a40   32   248G    2
d05-41        debug      idle   xeon-4116       --   24   185G   --
d05-42        debug      idle   xeon-4116       --   24   185G   --
e23-02        debug     mixed xeon-2640v4     p100    8    75G    2
```

### jobqueue

View job queue information.

```
$ jobqueue -p largemem
-----------------------------------------------------------------------------------------
Job ID             User     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ---------- ------------ ---------- -------- ----------- --------------------
7453378            jesp Run_do52bran   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7453379            jesp Run_do6b.job   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7473836         ttrojan sys/dashboar   largemem  RUNNING     2:42:28               a04-10
7449562            snet run_study_4x   largemem  RUNNING  2-23:17:10               a02-10
7453377            jesp Run_do51bran   largemem  RUNNING  2-17:02:07               a01-10
7470944          huy435    rfmixchr1   largemem  RUNNING    21:18:51        a02-10,a04-10
```

### jobhist

View compact history of jobs.

```
$ jobhist -p largemem
----------------------------------------------------------------------------------------------------
Job ID         Startdate       User     Job Name  Partition      State     Elapsed Nodes CPUs Memory
------------- ---------- ---------- ------------ ---------- ---------- ----------- ----- ---- ------
14690860      2024-07-29    ttrojan       sim.sl   largemem    RUNNING  3-08:19:19     1   32   128G 
14734145      2024-07-31       jesp         sfla   largemem    RUNNING  2-21:46:24     1   64   998G 
14738354      2024-07-31       snet  interactive   largemem  COMPLETED    06:56:19     1   16   400G 
14741823      2024-07-31     huy435   model_fit1   largemem  COMPLETED    07:04:19     1   64   248G 
14741846      2024-07-31     huy435   model_fit2   largemem  COMPLETED    08:10:59     1   64   248G 
14741918      2024-08-01       snet   feature.sl   largemem     FAILED    00:02:16     1    8   300G 
```

### jobinfo

View detailed job information.

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
Submit time          : 2024-01-26T14:56:23
Start time           : 2024-01-26T14:56:24
End time             : 2024-01-26T14:57:32
Wait time            : 00:00:01
Reserved walltime    : 00:10:00
Used walltime        : 00:01:08
Used CPU walltime    : 00:36:16
Used CPU time        : 00:35:18
CPU efficiency       : 97.37%
% User (computation) : 96.35%
% System (I/O)       :  3.65%
Reserved memory      : 120G
Max memory used      : 64.74G (estimate)
Memory efficiency    : 53.95%
Max disk write       : 1.04M
Max disk read        : 14.42M
```

## License

[0BSD](LICENSE)
