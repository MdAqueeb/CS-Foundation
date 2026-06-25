## Critical Section

### What is a Critical Section?

* A Critical Section is a part of a program where shared data or shared resources are accessed.
* Multiple threads or processes may try to access the same shared resource.

### What is a Shared Resource?

* Shared Resource means data or a resource that can be accessed by multiple threads or processes.

Examples:

* balance
* count
* shared file
* printer

### Why is Critical Section Dangerous?

* Multiple threads may access shared data at the same time.
* This can cause Race Conditions and incorrect results.

### Example

Shared Resource:

balance = 1000

Critical Section:

balance = balance - 500

Here, balance is the shared resource and the code modifying balance is the critical section.

### Goal of Synchronization

* Allow only one thread/process inside the Critical Section at a time.
* This requirement is called Mutual Exclusion.

## Requirements(rules to acheive synchronization) of Critical Section Solution

When multiple threads or processes access shared resources, the synchronization solution should satisfy the following three requirements.

### 1. Mutual Exclusion

* Only one process or thread can enter the Critical Section at a time.
* If one thread is using the shared resource, other threads must wait.
* It prevents Race Conditions.

#### Example

If Thread 1 is updating `balance`, then Thread 2 cannot update `balance` until Thread 1 finishes.

---

### 2. Progress

* If no process is inside the Critical Section and some processes want to enter, a decision should be made within a finite time.
* The system should not delay unnecessarily.
* A waiting process should be allowed to enter when the Critical Section is free.

#### Example

If the Critical Section is empty and Thread 1 requests access, the system should allow it to enter instead of making it wait forever.

---

### 3. Bounded Waiting

* A process should not wait forever to enter the Critical Section.
* There must be a limit on the number of times other processes can enter before a waiting process gets its turn.
* It prevents starvation.

#### Example

If Thread 1 is waiting, Thread 2 and Thread 3 should not be allowed to enter repeatedly forever while Thread 1 never gets access.

---

## Easy Memory Trick

### Mutual Exclusion

* Only one thread inside.

### Progress

* If empty, allow someone to enter.

### Bounded Waiting

* No thread waits forever.

---

## Important Note

These are requirements (rules), not synchronization tools.

Requirements:

* Mutual Exclusion
* Progress
* Bounded Waiting

Synchronization Tools:

* Mutex
* Semaphore
* Spin Lock
* Monitor

The tools are used to satisfy the requirements.

**Note:** Synchronization does not remove multithreading. It only protects the Critical Section (shared resources). Threads can still execute concurrently or in parallel outside the Critical Section. 

## Tools for synchronization:
* Mutex
* Semaphore
* Spin Lock
* Monitor

### Mutex

#### What is Mutex?

* Mutex stands for Mutual Exclusion.
* It is a synchronization tool used to protect Critical Sections.
* It allows only one thread or process to access the Critical Section at a time.

#### Why do we need Mutex?

* To prevent Race Conditions.
* To ensure safe access to shared resources.

#### How Mutex Works?

1. Thread acquires (locks) the mutex.
2. Thread enters the Critical Section.
3. Thread performs its work.
4. Thread releases (unlocks) the mutex.
5. Another waiting thread can now enter.

#### Important Operations

##### Lock

* Acquire the mutex before entering the Critical Section.

##### Unlock

* Release the mutex after leaving the Critical Section.

#### Real-Life Example

* Bathroom key.
* Only the person holding the key can enter.
* Others must wait until the key is returned.

#### Main Purpose

* Provide Mutual Exclusion.
* Prevent Race Conditions.

## Mutex vs Binary Semaphore

### Similarity

* Both allow only one thread/process at a time.
* Both can be used to prevent Race Conditions.

### Mutex

* Ownership exists.
* The thread that locks the mutex must unlock it.
* Mainly used to protect Critical Sections.

### Binary Semaphore

* Values are 0 or 1.
* Ownership does not exist.
* One thread can execute Wait() and another thread can execute Signal().
* Used for synchronization and signaling.

### How to Choose?

Use Mutex:

* One shared resource.
* Need exclusive access.

Examples:

* Shared variable
* Bank account balance
* Shared file

Use Counting Semaphore:

* Multiple identical resources exist.

Examples:

* Printers
* Database connections
* Parking slots

### Important

* The choice does NOT depend on CPU cores.
* The choice depends on the number and type of resources being managed.

## Spin Lock

### What is a Spin Lock?

* A Spin Lock is a synchronization mechanism where a thread repeatedly checks a lock until it becomes available.
* The waiting thread does not sleep or block.

### How It Works?

1. Thread tries to acquire the lock.
2. If lock is unavailable, it keeps checking repeatedly.
3. When lock becomes available, the thread acquires it and enters the Critical Section.

### Advantages

* No context switching.
* Fast for very short waiting periods.

### Disadvantages

* Wastes CPU time while spinning.
* Not suitable for long waiting periods.

### When to Use?

* Short waiting time.
* Lock expected to be released quickly.

### Mutex vs Spin Lock

Mutex:

* Waiting thread sleeps.
* Better for long waits.

Spin Lock:

* Waiting thread keeps checking.
* Better for short waits.

## Monitor

### What is a Monitor?

* A Monitor is a high-level synchronization construct.
* It automatically provides mutual exclusion.
* Only one thread can execute inside a monitor at a time.

### Why do we need Monitor?

* To simplify synchronization.
* To avoid programming mistakes such as forgetting to unlock a mutex.

### Monitor vs Mutex

Mutex:

* Programmer manually locks and unlocks.
* More chances of mistakes.

Monitor:

* Mutual exclusion is handled automatically.
* Easier and safer to use.

### Main Purpose

* Simplify synchronization.
* Automatically provide mutual exclusion.

## Producer–Consumer Problem

### Producer

* Produces data/items.
* Places items into a shared buffer.

### Consumer

* Consumes/removes items from the shared buffer.

### Buffer

* Shared storage area between producer and consumer.

### Problems

#### 1. Buffer Full

* Producer cannot add more items.
* Producer must wait.

#### 2. Buffer Empty

* Consumer cannot remove items.
* Consumer must wait.

#### 3. Race Condition

* Producer and Consumer may access the buffer simultaneously.
* Shared data may become inconsistent.

### Solution Idea

* Use Mutex to protect the shared buffer.
* Use Semaphores to manage empty and full slots.

### Real-Life Example

* Kitchen → Producer
* Customer → Consumer
* Food Counter → Buffer

## Producer–Consumer Solution

### Initial Values

Buffer Size = N

empty = N
full = 0
mutex = 1

### Producer

1. Wait(empty)
2. Wait(mutex)
3. Add item to buffer
4. Signal(mutex)
5. Signal(full)

### Consumer

1. Wait(full)
2. Wait(mutex)
3. Remove item from buffer
4. Signal(mutex)
5. Signal(empty)

### Purpose of Each Variable

empty:

* Counts available empty slots.

full:

* Counts available filled slots.

mutex:

* Protects the shared buffer from Race Conditions.

### Important

Semaphore:

* Manages resource availability.

Mutex:

* Protects Critical Section (buffer).

## Readers–Writers Problem

### Shared Resource

* File
* Database
* Document
* Shared Data

### Readers

* Only read data.
* Do not modify data.

### Writers

* Modify data.
* Can insert, update, or delete data.

### Rules

#### Reader + Reader

* Allowed.
* Multiple readers can access simultaneously.

#### Reader + Writer

* Not Allowed.
* Reader may see inconsistent data.

#### Writer + Writer

* Not Allowed.
* May cause Race Conditions and data corruption.

### Main Goal

* Allow maximum concurrency for readers.
* Protect data while writers are updating.

### Important Idea

* Multiple readers can read together.
* Only one writer can write at a time.
* While writing is happening, nobody else can access the shared resource.

## Starvation vs Deadlock

### Starvation

* A process waits indefinitely because other processes keep getting resources first.
* Other processes continue making progress.
* Usually caused by unfair scheduling or resource allocation.

### Deadlock

* Two or more processes wait for resources held by each other.
* No involved process can proceed.
* Often caused by circular waiting.

### Memory Trick

Starvation:

* One process suffers.
* Others continue.

Deadlock:

* Everyone involved waits.
* Nobody proceeds.
