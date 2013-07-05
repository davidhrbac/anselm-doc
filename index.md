---
layout: default
title: RepoForge FAQ
---

# PBS Batch Jobs 

## Altering the Job

### Remove the Job from the Queue

Job(s) can be stopped or removed from the queue with the command _qdel_ regardless its state.

To remove a job with PBS ID 111, use the following command:

    $ qdel 1111

### Hold Queued Job

Job(s) in the queue in a non-running state may be placed on hold using the qhold command. Jobs placed on hold will not be removed from the queue, but they will not be eligible for execution.

To move a currently queued job with a PBS ID 1111 to a hold state, use the following command:

    $ qhold 1111

###Release Held Job

The job on hold will not be eligible to run until it is released to return to a queued state. The qrls command can be used to remove a job from the held state.

For example, to release a job with PBS ID 111 from a held state, use the following command:

    $ qrls 1111

More details on the qrls utility can be found on the qrls man page.

###Modify Job Details

Non-running (or on hold) only jobs can be modified with the qalter PBS command.

####Modify the job´s name

    $ qalter -N <newname> <jobid>

####Modify the number of requested cores

    $ qalter -l size=<NumCores> <jobid>

####Modify the job´s wall time

    $ qalter -l walltime=<hh:mm:ss> <jobid>

####Set job´s dependencies

    $ qalter -W  depend=type:argument <jobid>

####Remove a job´s dependency (omit :argument)

    $ qalter -W  depend=type <jobid>

Notes:
 * Use qstat -f &lt;jobid&gt; to gather all the information about a job, including job dependencies.
 * Use qstat -a &lt;jobid&gt; to verify the changes afterward.
 * Users cannot specify a new walltime for their job that exceeds the maximum walltime of the queue where your job is.
 * If you need to modify a running job, please contact us. Certain alterations can only be performed by Anselm administrators.

