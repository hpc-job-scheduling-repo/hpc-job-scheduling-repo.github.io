---
layout: default
title: Workloads
description: Job Workloads
---

To simulate various aspects of HPC Scheduling a recorded log of a historic workload is needed.
This page points to detailed workload logs collected from large scale parallel systems in production use in various places around the world.

##### Parallel Workloads Archive [www.cs.huji.ac.il/labs/parallel/workload/](https://www.cs.huji.ac.il/labs/parallel/workload/)
The Parallel Workloads Archive (PWA) is a well established HPC workload trace repository. It contains detailed workload logs collected from large scale parallel systems. Each archived workload log is formatted in a uniform format, so-called SWF.
Each data set is represented by a sequence of lines (jobs) containing 18 columns (job metadata) per line.

*  Job Number -- Unique job identifier, also called JobID.
*  Submit Time -- seconds starting from workload log time.
*  Wait Time -- difference between Submit Time and Start Time in seconds.
*  Run Time -- the actual time in seconds the job was running
*  Number of Allocated Processors -- integer value of allocated cores or CPU, depends on configuration
*  Average CPU Time Used -- both user and system, in seconds. 
*  Used Memory -- average used memory per core in kilobytes. 
*  Requested Number of Processors
*  Requested Time -- Wall time requested for job
*  Requested Memory -- requested memory per processor in kilobytes
*  Status -- a number indicating the reason why job has finished. 1 = job was completed normal, 0  = failed, and 5 = canceled. If this field can not be provided it is -1.
*  User ID -- a number identifying a user. 
*  Group ID -- a number identifying a group.
*  Executable (Application) Number -- a number to identify the application. If not available then -1.
*  Queue Number -- a number identifying configured queues. It is suggested to use 0 for interactive jobs.
*  Partition Number -- a number identifying configured partitions.
*  Preceding Job Number -- a previous Job Number (JobID) which is the job is waiting to finish. With this a dependency between jobs can be established.
*  Think Time from Preceding Job -- a value indicating how long a job has to wait after a preceding job has finished before the job is started.

##### JSSPP Workloads Archive [@JSSPP](https://jsspp.org/workload/)
The website of JSSPP also contains a few workloads. Mainly these workloads where used in publications at the workshop.

##### More comming soon

abc fkjsnlkfhjs
abc sdfsdf
abc fsadsdf
