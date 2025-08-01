---
title: Useful Commands
created: 2024-07-07T00:00:00
modified: 2025-08-01T18:36:32
tags:
  - how-to
  - easy
  - sysadmin
---

# **HOW TO:** Use Some Useful Commands

This doc will go over certain useful commands you may use on the infrastructure.

# System Commands

## View System Stats

If you want to view CPU & RAM usage, active processes, and system uptime, run the following command:

```bash
top -i
# -i will hide any inactive processes.
```

It will look something like this:

```
top - 11:52:41 up 57 days,  3:13,  1 user,  load average: 0.24, 0.20, 0.13
Tasks: 194 total,   1 running, 193 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.5 us,  0.7 sy,  0.8 ni, 97.6 id,  0.0 wa,  0.0 hi,  0.1 si,  0.3 st
MiB Mem :  16002.8 total,  14226.2 free,    905.5 used,    871.0 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.  14757.2 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
███████ netdata   ██  ██  ██████ ██████  █████ █   3.3   1.2 290:45.66 netdata
```

| Item           | Meaning                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------- |
| **`up`**       | Show uptime in days                                                                            |
| **`Tasks`**    | Lists the total amount, running, sleeping, stopped and 'zombie' tasks                          |
| `%CPU(s)`      | CPU utilisations                                                                               |
| **`MiB Mem`**  | Shows the total, free, used, and cached memory in KibiBytes (MiB)                              |
| **`MiB Swap`** | Shows the total, free, use, and available [Swap](https://phoenixnap.com/kb/swap-space) memory. |

| Column    | Meaning                                                                                                            |
| --------- | ------------------------------------------------------------------------------------------------------------------ |
| `PID`     | Process ID                                                                                                         |
| `USER`    | User that started the process                                                                                      |
| `PR`      | Process Priority                                                                                                   |
| `NI`      | 'Nice' value, another priority value                                                                               |
| `VIRT`    | Virtual Memory Size in KibiBytes (KiB)                                                                             |
| `RES`     | Resident Memory Size in KibiBytes (KiB)                                                                            |
| `SHR`     | Shared Memory Size in KibiBytes (KiB)                                                                              |
| `S`       | Process Status. ('D' = Uninterruptable sleep, 'R' = Running, 'S' = Sleeping, 'T' = Traced / Stopped, 'Z' = Zombie) |
| `%CPU`    | CPU Utilisation in Percentage                                                                                      |
| `%MEM`    | Memory Utilisation in Percentage                                                                                   |
| `TIME+`   | Total CPU time used by the process, in hundredths of a second                                                      |
| `COMMAND` | The command used to start the process                                                                              |

## Restarting a Server

When you want to restart a server, run the following command:

```bash
sudo shutdown -r now
# -r tells it to restart
# now tells it to do it immediately
```

You will be instantly disconnected as the server shuts down and restarts.

A restart will take a few minutes, so be patient!

!!! note "After a restart, follow the [restart / unexpected shutdown checklist](./power-loss-checklist.md)!"
