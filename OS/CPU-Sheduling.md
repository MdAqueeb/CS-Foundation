## What is CPU Scheduling?

* CPU Scheduling decides which process should use the CPU next.
* It selects a process from the Ready Queue and allocates the CPU to it.

## Why do we need CPU Scheduling?

* Without CPU Scheduling, the OS cannot efficiently manage multiple processes.
* It helps decide:

  * Which process gets the CPU.
  * Which process waits in the Ready Queue.
  * How CPU time is allocated.

## CPU Scheduler vs Dispatcher

### CPU Scheduler

* Selects a process from the Ready Queue.

### Dispatcher

* Gives CPU control to the selected process.
* Performs context switching when required.

## What is Ready Queue?

* The Ready Queue contains processes that are ready to execute and waiting for CPU service.

## Preemptive Scheduling

* The OS can interrupt a running process and allocate the CPU to another process.(Simple meaning concurrency(all in progress))
* Examples: Round Robin, SRTF.

## Non-Preemptive Scheduling

* Once a process gets the CPU, it continues until completion or enters the waiting state.
* Examples: FCFS, SJF.

## Important Formulas

### Turnaround Time (TAT)

* Total time spent in the system.
* TAT = Completion Time (CT) - Arrival Time (AT)

### Waiting Time (WT)

* Time spent waiting in the Ready Queue.
* WT = TAT - Burst Time (BT)

### Response Time (RT)

* Time taken to get CPU for the first time.
* RT = First Start Time - Arrival Time (AT)

### Completion Time (CT)

* How much time takes to complete
* CT = Start Time + Bust Time (BT)

## CPU Scheduling Algorithms

* FCFS (First Come First Serve)
* SJF (Shortest Job First)
* SRTF (Shortest Remaining Time First)
* Round Robin
* Priority Scheduling
* Multilevel Queue

## FCFS (First Come First Serve)

* FCFS is the simplest CPU Scheduling algorithm.
* Processes are executed in the order they arrive.
* The process that arrives first gets the CPU first.
* FCFS is a Non-Preemptive Scheduling algorithm.

### Advantages

* Easy to implement.
* Fair according to arrival order.

### Disadvantages

* Convoy Effect.
* Short processes may wait for a long process to finish.

## SJF (Shortest Job First)

- SJF is a CPU Scheduling algorithm.
- It selects the process with the shortest Burst Time first.
- It follows Non-Preemptive Scheduling.
- Non-Preemptive: Once a process gets CPU, it executes until completion.

### Advantages
- Reduces Average Waiting Time.
- Better than FCFS for short processes.

### Disadvantages
- Starvation may occur.
- Starvation: Long processes may wait for a very long time this is called Starvation.

### Example

P1 = 8
P2 = 4
P3 = 1
P4 = 3

Execution Order:

P3 → P4 → P2 → P1

## SRTF (Shortest Remaining Time First)

- SRTF is the preemptive version of SJF.
- It always selects the process with the shortest remaining time.
- If a new process arrives with a shorter remaining time, the current process is interrupted.
- It follows Preemptive Scheduling.

### Advantages
- Lower average waiting time than SJF.
- Better response for short processes.

### Disadvantages
- More context switching.
- Starvation can occur for long processes.

### Example

P1 = AT(0), BT(8)
P2 = AT(1), BT(4)

Execution:

P1 → P2 → P1

## Round Robin (RR)

### What is Round Robin?

* Round Robin is a Preemptive CPU Scheduling Algorithm.
* Each process gets a fixed amount of CPU time called Time Quantum (Time Slice).
* If the process is not completed within the Time Quantum, it is moved to the end of the Ready Queue.

### How Round Robin Works?

1. CPU Scheduler picks a process from the Ready Queue.
2. Dispatcher gives CPU control to that process.
3. Process executes for the Time Quantum.
4. If completed, it is terminated.
5. If not completed, it is moved to the end of the Ready Queue.
6. Next process gets CPU service.

### Example

Time Quantum = 2

P1 = 5
P2 = 4

Execution:

0 → 2 : P1
2 → 4 : P2
4 → 6 : P1
6 → 8 : P2
8 → 9 : P1

Gantt Chart:

0      2      4      6      8      9
| P1 | P2 | P1 | P2 | P1 |

### Advantages

* Fair scheduling because every process gets CPU time.
* Good response time.
* Suitable for Time Sharing Operating Systems.
* Prevents a process from holding the CPU for too long.

### Disadvantages

* More Context Switching.
* Performance depends on Time Quantum selection.

### Important Points

* If Time Quantum is too large, Round Robin behaves like FCFS.
* If Time Quantum is too small, Context Switching overhead increases.
* Round Robin follows Preemptive Scheduling.

## Priority Scheduling

### What is Priority Scheduling?

* Priority Scheduling is a CPU Scheduling Algorithm that selects the process based on priority.
* The process with the highest priority gets the CPU first.
* Usually, a smaller priority number means higher priority, but it depends on the system design.

### Why do we need Priority Scheduling?

* Some processes are more important than others.
* Important processes should get CPU service before less important processes.

### Types of Priority Scheduling

#### Non-Preemptive Priority Scheduling

* Once a process gets the CPU, it runs until completion.
* Even if a higher-priority process arrives, the current process is not interrupted.

Example:

P1 (Priority = 3) starts running.

P2 (Priority = 1) arrives.

P1 continues execution until completion, then P2 runs.

#### Preemptive Priority Scheduling

* If a higher-priority process arrives while another process is running, the current process is interrupted.
* The higher-priority process gets the CPU immediately.

Example:

P1 (Priority = 3) starts running.

P2 (Priority = 1) arrives.

P1 is stopped and P2 starts execution.

### Advantages

* Important processes get CPU service quickly.
* Useful for real-time and system-critical tasks.

### Disadvantages

* Low-priority processes may wait for a long time.
* Can lead to Starvation.

### Important Concepts

#### Starvation

* A low-priority process waits for a very long time because higher-priority processes keep getting CPU service.

#### Aging

* Aging is the solution to starvation.
* The OS gradually increases the priority of a waiting process.
* Eventually, the process gets CPU service.

## Multilevel Queue Scheduling

### What is Multilevel Queue Scheduling?

* Multilevel Queue Scheduling divides the Ready Queue into multiple separate queues.
* Processes are placed into queues based on their type, priority, or purpose.
* Higher-priority queues get CPU service before lower-priority queues.

### Why do we need Multilevel Queue Scheduling?

* Not all processes are equally important.
* System processes, user processes, and background processes have different requirements.
* Separate queues help the OS manage them efficiently.

### Example

Queue 1 → System Processes

Queue 2 → Interactive/User Processes

Queue 3 → Background Processes

Priority:

Queue 1 > Queue 2 > Queue 3

### Scheduling Inside Queues

Each queue can use its own scheduling algorithm.

Example:

* Queue 1 → Round Robin
* Queue 2 → Priority Scheduling
* Queue 3 → FCFS

### Advantages

* Better organization of processes.
* Important processes get CPU service faster.
* Different scheduling policies can be used.

### Disadvantages

* Lower-priority queues may wait for a long time.
* Can cause starvation.

## Throughput

### What is Throughput?

* Throughput measures how many processes are completed in a given amount of time.
* It is used to evaluate system performance.

### Formula

Throughput = Number of Completed Processes / Time Taken

### Example

20 processes completed in 10 seconds.

Throughput = 20 / 10 = 2 processes per second.

### High Throughput

* More processes completed in less time.
* Indicates better system performance.

### Low Throughput

* Fewer processes completed in more time.
* Indicates lower system performance.

### Interview Definition

* Throughput is the number of processes completed by the system per unit time.

## Starvation

### What is Starvation?

* Starvation occurs when a process waits for CPU service for a very long time or indefinitely.
* The process is ready to execute, but the scheduler keeps selecting other processes.

### Why does Starvation occur?

* Some scheduling algorithms give preference to certain processes.
* Lower-priority processes may never get CPU time if higher-priority processes keep arriving.

### Where does Starvation occur?

* Priority Scheduling
* Multilevel Queue Scheduling

### Where is Starvation uncommon?

* FCFS
* Round Robin

### Important Point

* A starving process is usually in the Ready State.
* It is not blocked or waiting for I/O.
* It is waiting for CPU allocation.

## Difference Between Waiting State and Starvation

### Waiting State

* The process is waiting for an event or I/O operation.
* The process cannot continue execution until the requirement is fulfilled.
* It is a normal part of the process lifecycle.

Examples:

* Waiting for disk read
* Waiting for network response
* Waiting for user input

### Starvation

* The process is ready to execute.
* All requirements are fulfilled.
* The scheduler keeps selecting other processes, so the process waits for CPU service for a very long time.

### Key Difference

* Waiting State = Waiting for I/O or an event.
* Starvation = Waiting for CPU.

## Aging

### What is Aging?

* Aging is a technique used to prevent starvation.
* The Operating System gradually increases the priority of a process that has been waiting for a long time.

### Why do we need Aging?

* In Priority Scheduling and Multilevel Queue Scheduling, low-priority processes may wait indefinitely.
* This problem is called starvation.
* Aging solves starvation.

### How Aging Works?

* The OS periodically increases the priority of waiting processes.
* After waiting long enough, the process gets CPU service.

### Example

Priority 10

↓

Priority 9

↓

Priority 8

↓

Priority 7

↓

Eventually becomes high priority and gets CPU.

### Interview Definition

* Aging is a technique that prevents starvation by gradually increasing the priority of long-waiting processes.

## Response Time

### What is Response Time?

* Response Time measures how long a process waits before getting CPU service for the first time.

### Formula

Response Time = First Start Time − Arrival Time

### Example

Arrival Time = 2

First Start Time = 5

Response Time = 5 − 2 = 3

### Response Time vs Waiting Time

#### Response Time

* Time taken to get CPU service for the first time.
* Only considers the first CPU allocation.

#### Waiting Time

* Total time spent waiting in the Ready Queue during execution.

### Interview Definition

* Response Time is the time between a process arrival and its first CPU allocation.

