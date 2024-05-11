---
tags:
  - incomplete
---
![[Operating Systems MOC 🌍]]
### The Kernel 
The aim of the kernel is the provide an environment in which processes can exist.

Four essential components:
- Privileged instruction set 
- Interrupt mechanism 
- Memory protection 
- Real-time clock 

The kernel consists of the 
- First-level interrupt handler (FLIH) to manage interrupts 
- The dispatcher/scheduler to switch between processes.
- Intra operating system communications.
### First Level Interrupt Handler 
The function of the FLIH is to
- Determine the source of an interrupt.
- Initiate a servicing of the interrupt.
### The Dispatcher 
Assigns processing resource for processes.

It is later called upon when 
- A current process cannot continue 
- The CPU needs to switch processes.
### Threads 
A thread is a unit of execution.
It belongs to a process and executes within it.
There are user threads and kernel threads.

- Separate threads have their own registers and stacks.
- Global variables are shared between threads
##### Benefits 
- Timing - Less time to create or terminate a thread than a process.
- Responsiveness - Allows continued execution if part of process is blocked.
- Resource Sharing - Threads share resources for process, easier than shared memory.
- Economy - Cheaper than process creation.
- Scalability - Can take advantage of multiprocessor architectures.
### Concurrency vs Parallelism
Concurrency execution on a single core 
![[Pasted image 20240507111318.png]]

Parallelism on a multi-core system 
![[Pasted image 20240507111331.png]]
### Amdahl's Law 
Identifies performance gains from adding additional cores to an application with both serial and parallel components.

$$
\text{Speed Up} \le \frac{1}{S + \left(\frac{1-S}{N}\right)}
$$

$S$ is the serial portion and $N$ is the processing cores.

So, if an application is 75% parallel and 25% serial, moving from 1 to 2 cores results in a 1.6x speed up.

$$
\frac{1}{0.25 + \frac{0.75}{2}} = 1.6
$$

As $N$ approaches infinity, speedup approaches $\frac{1}{S}$.








---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
