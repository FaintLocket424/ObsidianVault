---
tags:
  - incomplete
---
![[Operating Systems MOC 🌍]]
### Schedulers 
An operating system operates 3 types of schedulers
- Long term - Selects which processes though be brought into the ready queue.
- Medium term - Part of swapping and in-charge of handling the swapped out 
- Short term - Selects which process to be executed next and allocated to the CPU.
### Scheduling Algorithms 
- First come first served 
- shortest job first 
- shortest remaining time first 
- Priority 
- Round robin 
- Multilevel feedback queue 
#### First Come, First Served (FCFS)
The first process to request the CPU is allocated to the CPU until it is completed.

If we get 3 processes in the order $P_{1}$, $P_{2}$, $P_{3}$ at the same time with burst times 24, 3 and 3 respectively then it will execute all of $P_{1}$, then all of $P_{2}$, then all of $P_{3}$.

The wait time for $P_{1}=0$, for $P_{2}=24$ and $P_{3}=27$, with the average waiting time being $17$.

Say we now get them in order $P_{2}$, $P_{3}$, $P_{1}$.
Now the wait for $P_{1}=6$, $P_{2}=0$, $P_{3}=3$ so the average wait time is $3$.
This is much better than before.

Properties:
- Average waiting time may or may not be lengthy.
- A simple algorithm to implement.
- May result in convoy effect when short processes are waiting for a long process to finish.
#### Shortest Job First 
We associate with each process, the length of its next CPU burst.
We then use these lengths to schedule the process with the shortest time.
The processes cannot be stopped. Once one has started its burst, it goes until completion.

If we get these processes:
![[Pasted image 20240507114457.png]]
Then the Gantt Chart looks like this 
![[Pasted image 20240507114512.png]]
With the average waiting time being 4 and the average turnaround time being 8.
#### Shortest Remaining Time First 
If a new process arrives in the ready queue with a CPU burst length less than the remaining time of the executing process, swap out the running process with the shorter one.

This is a pre-emptive version of [[#Shortest Job First]].

If we get processes in this order, just like in SJF
![[Pasted image 20240507114457.png]]

Now the Gantt Chart looks like this 
![[Pasted image 20240507114832.png]]
With an average waiting time of 3 and an average turnaround time of 7.
#### Round Robin (RR)
Each process gets a small unit of CPU time. A time slice $q$ usually 10 to 100 ms.

After this time has elapsed, the process is pre-empted and added to the end of the ready queue.

If there are $n$ processes in the ready queue then each process gets $\frac{1}{n}$ of the CPU time in chunks of $q$ units at most at once.

If we get these processes
![[Pasted image 20240507115608.png]]
with a time quantum of $q=4$, the Gantt Chart looks like this 
![[Pasted image 20240507115817.png]]
Average waiting time is 5.66 and average turnaround time is 15.66.

Performance of the RR algorithm depends heavily on the size of the time quantum.

If the time quantum is very large, RR acts like [[#First Come, First Served (FCFS)]].
If the time quantum is very small, this results in a large number of context switches.

The time quantum should be large compared to the context-switch time, but not too large.

A rule of thumb is 80% of the CPU bursts should be shorter than the time quantum.
#### Priority Scheduling 
Each process is assigned a priority number.

The CPU is allocated by the dispatcher to the process with the highest priority.

This can be pre-emptive or not.

##### Non-pre-emptive Priority Example 
Take these processes
![[Pasted image 20240507120230.png]]
The Gantt Chart looks like this 
![[Pasted image 20240507120240.png]]
With an average wait time of 8.2.

When it is finished with a process, it choses the highest priority job first.

This has the problem of starvation or indefinite blocking, where low priority jobs may never execute.
A solution to this is ageing where jobs gain priority over time.

You can also combine [[#Round Robin (RR)]] with priority, running high priority jobs first and running equal priority jobs with RR.








---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
