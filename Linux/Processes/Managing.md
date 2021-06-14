---
title: Managing Processes
parent: Processes
grand_parent: Linux
---
# Managing Processes

## Jobs
- Groups of processes, created from a command (from user f.ex)
- Can be run in:
  - Foreground: run directly from the shell, and when one job is running, other jobs need to wait for shell access
  - Background: Attaching a `&`. Gets a lower priority, releases the shell to other uses.
  - By default, jobs run in foreground. `bg` and `fg` can be used to run jobs after suspending them (`Ctrl` + `z`).
  - Background jobs can be shown with `jobs`

## Monitoring

To list and monitor processes, two main tools are used.

### `ps`
- Provides information about processes
- Has several options to control its output. For example
    ```sh
    ps #Shows processes in current shell
    ps -ef #Shows all processes in the system with full format
    ps -eLf #Same as above + threads and thread info
    ps aux #BSD Argument style, shows all processes of all users
    ps aox pid,ppcpu #BSD Argument style, shows only PID and %CPU
    ```
- A variant is `pstree` which shows all the processes in the system, and the threads and their relation (parent-child) in tree form.


### `top`

- **Interactive** tool to monitor and control processes
  
- Has "summary" lines at the beginning, showing:
  - Uptime and Load Average
  - Process count and their state
  - %CPU for user processes (`us`), for system processes (`si`).
  - The percentage of user jobs running at a lower priority (`ni`), Idle mode (`id`), the percentage of jobs waiting (`wa`) for I/O is listed, the percentage of hardware (`hi`) vs. software interrupts (`si`) and steal time (`st`) (generally used with virtual machines)
  - Memory information (RAM and Swap, which is used when RAM is full)
  
- Shows processes with the following categories as default:
  - `PID`, `USER`, Priority (`PR`), Niceness (`N`), Virtual (`VIRT`), physical (`RES`), and shared memory (`SHR`), Status (`S`), `%CPU`, `%MEM`, Execution time (`TIME+`) and `COMMAND`.

- Using interactive commands, more information can be obtained, processes can be sorted, prioritized or killed:
  - `f`: Change what is displayed and the sort parameter
  - `r`: Renice a process
  - `k`: Kill a process
  - `1`: Show all CPUs in summary
  - Many others



### Load Average

- Is the average system load on a PC for a defined period of time
- Takes into consideration process `RUNNING`, in run queue, or in `SLEEP` state
- Can be read in the output from `w`, `uptime` and `top`
- Interpreted like (`load average: 0,20, 0,58, 0,67`, for a 1 CPU PC):
  - For the last minute, 20% of the CPU has been utilized in avg.
  - For the last 5 minutes, 58% of the CPU has been utilized in avg.
  - For the last 15 minutes, 67% of the CPU has been utilized in avg.
- For more CPU all numbers are divided by the number of CPUs
    

## Kill

To kill processes (only the ones from the current user, otherwise admin acesss is needed):
```sh
kill -SIGKILL <PID>
kill -9 <PID>
```
## Scheduling processes to execute

### `at`
- Can be used to schedule when in the future a job should run
- For example:

```sh
at now + 2 days # Time to execute
at> cat file1.txt # Tasks to perform
at> <EOT> #Press Ctrl+D to submit
```
### `cron`
- Tool for scheduling background jobs (at specific times or periodic)
- Driven by a configuration file at `/etc/crontab` (cron table)
- There are both system-wide crontab files and individual user-based ones
- Can be edited with `crontab -e`
  - Each line has 6 parameters: `<MIN> <HOUR> <DOM> <MON> <DOW> <CMD>`
  - For example `* * * * * /usr/local/bin/execute/this/script.sh` will schedule a job to execute script.sh every minute of every hour of every day of the month, and every month and every day in the week.
  - `30 08 10 06 * /home/sysadmin/full-backup` will schedule a full-backup at 8.30 a.m., 10-June, irrespective of the day of the week.

### `sleep`
- Used to delay a command (make it wait before finish)
- By default accepts seconds but with suffixes can accept anything:

```bash
sleep 2 # 2 seconds
sleep 2s # 2 seconds
sleep 2m # 2 minutes
sleep 2h # 2 hours
sleep 2d # 2 days
```