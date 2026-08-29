
## Demo

[Project Demonstration Video](https://youtu.be/JnPp3LxYlz4)

# Adaptive Data-Driven CPU Scheduler for xv6-RISC-V

## Overview

An extension of **xv6-RISC-V** that implements an adaptive, data-driven CPU scheduler. Instead of treating every process equally, the scheduler collects **live process behavior from the kernel** and uses it to make scheduling decisions.

## Key Features

* **Adaptive CPU Scheduler** — makes scheduling decisions using process behavior and an adaptive score.
* **Process Accounting** — tracks:

  * CPU runtime (`rtime`)
  * Waiting time (`wtime`)
  * Sleeping time (`stime`)
  * Scheduling count (`sched_count`)
  * Sleep count (`sleep_count`)
  * Adaptive score (`adaptive_score`)
* **System Calls** — implemented `getpinfo()` to expose live kernel process statistics to user programs.
* **Threads** — supports thread creation, joining, and shared memory.
* **Mutex Synchronization** — prevents race conditions when multiple threads access shared resources.
* **Semaphores** — controls the number of threads allowed in a critical section.
* **Testing and Benchmarking** — includes `teststats`, `optbench`, `threadtest`, `mutextest`, `semtest`, `cpubench`, and `tickbench`.
* **Kernel-Level Implementation** — scheduler, process accounting, system calls, thread support, and synchronization mechanisms were integrated into xv6.

## Example Results

### CPU vs I/O Behavior

```text
CPU-Bound: rtime=50, stime=0
IO-Bound:  rtime=0,  stime=50
```

### Thread Synchronization

```text
Final counter: 400 (expected 400)
```

### Semaphore

```text
Max simultaneous threads: 2 (expected <= 2)
```

## Running the Project

Start xv6 with the adaptive scheduler:

```bash
make qemu SCHED=ADAPTIVE
```

Then run the tests from the xv6 shell:

```text
teststats
optbench
threadtest
mutextest
semtest
cpubench
tickbench
```

## Requirements Covered

* Threads
* Optimization using live system-generated data
* Synchronization
* Semaphores
* System calls
* Kernel-level work
* Real process data collection

## Environment

**xv6-RISC-V | Ubuntu/WSL | QEMU | RISC-V | Git**
