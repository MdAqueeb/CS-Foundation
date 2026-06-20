## What is a program?
- Program is a set of instructions and it stored in a storage
- It is not executing state or passive state

## What is process?
- Process means if program in executing state is called process 
- it is in active state 
Note: 1 program can create 1 or more process depeniding on it's requirements

## What is PCB?

* PCB (Process Control Block) is a data structure maintained by the Operating System.
* It stores all information related to a process.
* Every process has its own PCB.

## Why do we need PCB?

* The OS uses PCB to manage and track processes.
* Without PCB, the OS cannot know the process details or execution status.

## Information stored in PCB

* Process ID (PID): Stores a unique ID for each process.
* Process State: Stores the current state of the process (New, Ready, Running, Waiting, Terminated, Ready Suspended, Waiting Suspended).
* Program Counter: Stores the address of the next instruction to execute.
* CPU Registers: Store the current execution information of the process so it can resume correctly later.
* Priority and Scheduling Information: Used by the scheduler to decide which process gets CPU time.
* Memory Management Information: Stores memory-related details of the process.
* I/O Information: Stores information related to files, devices, and I/O operations.

## PCB Lifecycle

* PCB is created when a process is created.
* PCB is deleted when the process terminates.

## Process States

Process states describe the current condition of a process during execution.

### New
- Process is being created.

### Ready
- Process is ready to execute.
- Memory and resources are allocated.
- Waiting for CPU.

### Running
- CPU is currently executing the process.

### Waiting (Blocked)
- Process is waiting for an event or I/O operation.
- Example: file read, network response.

### Terminated
- Process execution is completed.

## Note: 
- process state in waiting is there then it can't directly go to running state, first it will update waiting to ready then running because it is a **process state flow, it comes under Process lifecycle**. 

## What is Process Lifecycle?
- Process Lifecycle describes the complete journey of a process from creation to termination.
- It explains how a process moves between different states.

## State Flow

New
↓
Ready
↓
Running
↙      ↘
Waiting  Terminated
↓
Ready

## State Transitions

### New → Ready
- Process creation completed.
- Memory and PCB are allocated.

### Ready → Running
- CPU Scheduler assigns CPU.

### Running → Waiting
- Process waits for I/O or an event.

### Waiting → Ready
- I/O or event is completed.

### Running → Ready
- CPU time slice expires.
- Process returns to Ready Queue.

### Running → Terminated
- Process finishes execution.


## What is Context Switching?
- Context Switching is the process of saving the current process state and loading another process state.
- It allows multiple processes to share the CPU.

## What is Context?
- Context means the current execution information of a process.
- It is stored in the PCB.
- Example:
  - Program Counter
  - CPU Registers
  - Process State
  - Scheduling Information

## Why PCB is Important?
- PCB stores process information.
- During Context Switching, OS saves and restores process information using PCB.

## When Does Context Switching Occur?
- Time slice expires.
- Process enters Waiting State.
- Higher priority process arrives.

## Why is it Overhead?
- Saving and loading process information takes CPU time.
- Therefore Context Switching is not free and creates overhead.

## Parent Process
- A process that creates another process.

## Child Process
- A process created by another process.

## What is Zombie Process?
- Zombie Process is a process that has completed execution but still has an entry in the process table.
- It exists because the parent process has not collected its exit status.

## Characteristics
- Execution completed.
- Does not use CPU.
- Does not execute instructions.
- Stores only process information such as exit status and PCB entry.

## Removal
- When the parent process collects the child's exit status, the OS removes the Zombie Process.

## What is Orphan Process?
- An Orphan Process is a child process whose parent process has terminated.
- The child process is still running.

## What Happens?
- The OS does not terminate the child process.
- The OS assigns a new parent process.
- The child process continues execution normally.

## Characteristics
- It is still active.
- It can be in Ready, Running, or Waiting state.
- It has its own PCB and resources.

## Difference Between Zombie and Orphan

Zombie Process:
- Child terminates first.
- Parent is alive.
- Only PCB entry remains.

Orphan Process:
- Parent terminates first.
- Child is alive.
- Child continues execution.

**Note**: In orphan process, the os create new parent then no longer called orphan process, when to call means if no parent present then child process called orphan process