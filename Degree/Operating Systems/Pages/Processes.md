---
tags:
  - incomplete
  - degree/compsys/operatingsystems
---
![[Operating Systems MOC 🌍]]
### Processes 
A program in execution is called a process.

An operating system executed a variety of programs.

A process needs various resources 
- CPU time 
- Memory 
- Files 
- IO devices 

The OS is responsible for 
- Process creation and deletion 
- Process holding and resuming 
- Process Synchronisation 

Processes include:
- Code 
- Register contents 
- Stack 
- Global variables 
- Heap 
### Process Control Block 
A processes' information is stored in a PCB.

The PCBs form a process table.

Information about each process in the PCB includes 
- A process identifier (pid)
- A status 
- CPU registers 
- CPU scheduling information 
- Memory usage 
- Other information 
### Process State 
As a program executes, it changes state.
- New - Being created 
- Running - Instructions being executed 
- Waiting - Waiting for an event 
- Ready - Ready to be dispatched to CPU
- Terminated - Completed execution or has been terminated.

![[Pasted image 20240507101113.png]]

### Process Creation 
A parent process can create many child processes, which in turn can create child processes of their own. This forms a tree of processes.

Generally, processes are identified and managed via the process identifier (pid).

Child processes can share resources with their parent in 3 ways:
- They share all resources 
- The child has a subset of the parent's resources.
- They share no resources.

The execution of the child and parent can happen in 2 ways:
- Can execute concurrently
- Parent waits for children to terminate.
### Process Termination 
Once a process has executed its last statement it asked the operating system to delete it with the `exit()` (UNIX) system call.

It outputs the data from the child process to the parent.
The child resources are de-allocated by the OS.

The parent may terminate the child if:
- Child process has exceeded it's allocated resources 
- Task assigned is no longer required.
- The parent itself is terminating (cascade termination).

If no parent is waiting, the process is a zombie.
If parent is terminated, process is an orphan.
### Process Scheduling 
A process scheduler selects among available processes for the next execution on CPU.

Maintains scheduling queues for processes.
- Job queue - All processes in system
- Ready queue - Processes in main memory, ready to execute.
- Device queues - Processes waiting for I/O.
Processes migrate between queues.












---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
