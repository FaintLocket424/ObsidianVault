---
tags:
  - incomplete
---
![[Operating Systems MOC 🌍]]
### Why do we need an OS?
##### Case 1: The Abstract Machine 
- Extend basic hardware 
- Provide high level abstractions 
- Hides details of hardware, making code more portable.
##### Case 2: The Resource Manager 
- Responsible for allocating resources to users and processes.
- Allocation is done according to some policy like first-come, first served.
### What is an OS?
A program that acts as an intermediary between a user and the hardware.

There are a number of goals for the OS:
- Execute user programs 
- Make solving user problems easier 
- Make the computer convenient to use 
- Use the resources of the system fairly and efficiently with scheduling 

An OS is a:
- Resource allocator, responsible for resource management.
- Control program, controls execution of other programs 
- Kernel, the one program that is always running.
### Kernel Mode 
Dual-mode operation allows the OS to protect itself and other components with a user mode and a kernel mode.

Some instructions are privileged and require kernel mode to execute.
- Managing interrupts 
- Performing IO 
- Halting a process 

Transitions to Kernel Mode can occur when 
- A user process calls the OS to execute a function requiring a privileged instruction 
- An interrupts occurs 
- An error condition occurs in a user process 
- An attempt is made to execute a privileged instruction while in user mode.
### Operating System Types 
- Multi-user allows two or more users to run programs simultaneously.
- Multi-programming supports running a program on more than one CPU.
- Multi-tasking allows more than one program to run concurrently.
- Multi-threading allows different parts of a single program to run concurrently
- Real Time responds to input instantly.
- etc.
#### Multi-programming 
Multiprogramming is needed for efficiency.
A single user cannot keep the CPU and IO devices busy at all times.
Multiprogramming organises jobs so CPU always has something to execute.
A job is selected to run based on scheduling.
If a job has to wait, the OS switches to a different job.
#### Multi-tasking 
Timesharing (multitasking) is where the CPU switches jobs frequently so it can interact with each job frequently, creating interactive computing.
No jobs are left behind.
### OS Services 
One set of OS services provides functions that are helpful to the user
- User interface 
- Program execution 
- IO operations 
- File system manipulation 
- Communications 
- Error detection 

Another set of OS functions exist to ensure the efficient operation of the system via resource sharing 
- Resource allocation 
- Accounting 
- Protection and security 
### Interfaces - CLI and GUI 
#### CLI 
Allows for direct command entry.
Many multiple flavours implemented - shells.
#### GUI 
- User-friendly graphical interface.
- Uses mice and keyboard.
- Uses icons to represent programs and files.
### OS Structure 
A general purpose OS is a very large program.
There are many ways to structure one.
#### Simple Structure - MS-DOS 
MS-DOS was written to provide the most functionality in the least space.
It is not divided into modules.
It's interfaces and functionality are not well separated.
#### Non Simple Structure - UNIX 
A monolithic strategy with single file, single address space.

The UNIX OS consists of two separable parts 
- System programs 
- The kernel 














---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
