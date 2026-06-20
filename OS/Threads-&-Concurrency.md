## What is Process?
- Process is a running program.
- It has its own memory, PCB and resources.

## What is Thread?
- Thread is the smallest unit of CPU execution.
- It runs inside a process.
- A process can have one or more threads.

## Memory
- Processes have separate memory.
- Threads share process memory.
- Each thread has its own stack, registers and program counter.

## Process vs Thread
- Process is heavyweight.
- Thread is lightweight.
- Process creation is slower.
- Thread creation is faster.
- Process context switching is expensive.
- Thread context switching is cheaper.

## Important
- A process can contain multiple threads.
- A thread cannot exist without a process.

## Benefits of Threads

### Better Responsiveness
- One thread can handle UI while another thread performs background work.
- Application remains responsive.

### Faster Execution
- Multiple tasks can progress concurrently.
- Example: Download, Network and UI operations.

### Resource Sharing
- Threads share process memory and resources.
- Less memory is required.

### Low Creation Cost
- Creating threads is cheaper than creating processes.

### Faster Context Switching
- Thread switching is faster because threads share process resources. 

## What is Multithreading?

* Multithreading is the ability of a process to contain multiple threads.
* Each thread can perform a specific task within the same process.
* Threads share the process memory and resources.

## Single-Threaded vs Multi-Threaded Process

### Single-Threaded Process

* A process contains only one thread.
* All tasks are executed by the same thread.
* If the thread gets blocked (for example, waiting for I/O), the entire process becomes blocked.

### Multi-Threaded Process

* A process contains multiple threads.
* Different tasks can be assigned to different threads.
* If one thread gets blocked, other threads can continue executing.
* This improves responsiveness and resource utilization.

## User-Level Threads (ULT)

* User-Level Threads are managed by a thread library.
* The OS kernel does not know about individual threads.
* Thread creation and switching are fast because kernel involvement is not required.
* If one thread performs a blocking operation, the entire process may become blocked.

## Kernel-Level Threads (KLT)

* Kernel-Level Threads are managed by the OS kernel.
* The kernel knows every thread individually.
* If one thread becomes blocked, other threads can continue execution.
* Thread creation and switching are slower because they require kernel involvement and mode switching.

## Difference Between ULT and KLT

User-Level Threads:

* Managed by thread library.
* Faster creation and switching.
* Kernel does not know individual threads.
* One blocked thread may block the entire process.

Kernel-Level Threads:

* Managed by OS kernel.
* Slower creation and switching.
* Kernel knows every thread.
* One blocked thread does not stop other threads.

## Concurrency
- Multiple tasks make progress during the same period of time.
- It can happen on a single CPU core.
- It is achieved using context switching.
- Tasks appear to run simultaneously.

## Parallelism
- Multiple tasks execute at the same time.
- It requires multiple CPU cores.
- It improves execution speed.

## Difference

Concurrency:
- One CPU core is enough.
- Uses context switching.
- Focuses on task management and progress.

Parallelism:
- Requires multiple CPU cores.
- Tasks truly run simultaneously.
- Focuses on execution speed. 

## What is Race Condition?

- Race Condition occurs when multiple threads access and modify shared data simultaneously.
- The final result depends on the order or timing of execution.
- Race Conditions can produce unexpected or incorrect results.

## Example

Shared Variable = 0

Thread 1:
Shared Variable++

Thread 2:
Shared Variable++

Expected Result:
- 2

Possible Result:
- 1
- 2

Because both threads may read and update the shared variable at the same time.

## Why does Race Condition occur?

- Shared data is accessed by multiple threads.
- There is no synchronization or protection mechanism.
- Execution timing affects the result.