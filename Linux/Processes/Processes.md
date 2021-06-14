---
title:  Processes
parent: Linux
nav_order: 7
has_children: true
---
# Processes in Linux

- A process (or task) is an instance of a running program/application in the machine.
- Can be composed of threads (lightweight)
- Is not a command or program. One of these, can trigger multiple processes
- Uses system resources (Memory, CPU, NW cards, Hard Drives, etc)
- The OS (The kernel, scheduler) orchestrates the processes so they get access to the resources

## Process Types

Process Type | Description | Example
--- | --- | ---
Interactive Processes | Need to be started by a user, either at a command line or through a graphical interface |bash, firefox, top
Batch Processes | Automatic processes which are scheduled from and then disconnected from the terminal (Run in background). These tasks are queued and work on a FIFO (First-In, First-Out) basis. | updatedb, ldconfig
Daemons	| Server processes that run continuously. Many are launched during system startup and then wait for a user or system request indicating that their service is required.	| httpd, sshd, libvirtd, docker
Threads	| Lightweight processes. These are tasks that run under the umbrella of a main process, sharing memory and other resources, but are scheduled and run by the system on an individual basis. An individual thread can end without terminating the whole process and a process can create new threads at any time. Many non-trivial programs are multi-threaded. | firefox, gnome-terminal-server
Kernel Threads | Kernel tasks that users neither start nor terminate and have little control over. These may perform actions like moving a thread from one CPU to another, or making sure input/output operations to disk are completed. | kthreadd, migration, ksoftirqd

## Scheduling

### States

A process can be in one of:
- **RUNNING**: Currently executing or waiting to be granted a share of time in the run queue (1 for each processor)
- **SLEEP**: Waiting for something (external) to happen.
- Others: F.Ex **ZOMBIE**, when a child process finished but parent has not checked yet, so it appears alive.

### Priorities
- To determine access to the resources, the OS prioritizes the processes
- In Linux, the **niceness** value is used. (Less nice, more priority)
- Goes from -20 (top priority) to 19
- Can be checked using `ps lf`
- Can be changed using `renice` (To give more, super user is required):
    ```sh
    renice +5 3077 #Lowers the priority (niceness = 5) of PID 3077
    sudo renice -5 3077 #Gives more priority(niceness = -5) for PID 3077
    ```


## Identification

### PID 
- Unique ID given by the OS to the process
- ALlows to track resource usage and to manage
- Starts with 1 (`init` process)
- A process can have:
  - PID
  - PPID (Parent process ID, the one who started it)
  - TID (Thread Unique ID if the process is a thread, inside a main process)

### User and Group ID

- Different users (parts from different groups) can start processes
- For users, the `RUID` (Real User Id) is used to signal who started, together with `EUID` to see who granted access. In practice, `UID` is shown.
- For groups, the logic is the same. In practice, is identified with `GID`


