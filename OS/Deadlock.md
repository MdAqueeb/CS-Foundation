## Deadlock

### What is Deadlock?

* A situation where two or more processes wait for resources held by each other.
* None of the involved processes can proceed.

### Four Necessary Conditions

#### 1. Mutual Exclusion

* A resource can be used by only one process at a time.

#### 2. Hold and Wait

* A process holds a resource and waits for another resource.

#### 3. No Preemption

* Resources cannot be forcibly taken away.

#### 4. Circular Wait

* Processes form a circular chain of waiting.

### Important Rule

* All four conditions must exist for deadlock.
* If any one condition is removed, deadlock cannot occur.

### Memory Trick

* MHNC

  * Mutual Exclusion
  * Hold and Wait
  * No Preemption
  * Circular Wait

## Deadlock Prevention

### Idea

* Deadlock requires all four conditions.
* Remove any one condition to prevent deadlock.

### Methods

#### 1. Remove Mutual Exclusion

* Allow resource sharing where possible.

#### 2. Remove Hold and Wait

* Process must request all required resources at once.

#### 3. Remove No Preemption

* OS can forcibly take resources from a process.

#### 4. Remove Circular Wait

* Assign an order to resources.
* Processes must request resources in increasing order.

### Important

* Breaking any one of the four conditions prevents deadlock.

## Safe State vs Unsafe State

### Safe State

* There exists at least one sequence in which all processes can complete.
* System can guarantee completion of all processes.

### Unsafe State

* System cannot guarantee completion of all processes.
* Deadlock has not occurred yet.
* There is a possibility of deadlock in the future.

### Deadlock State

* Processes are already stuck.
* No involved process can proceed.

### Relationship

Safe State
↓
Unsafe State
↓
Deadlock (possible)

### Important

* Unsafe State is NOT Deadlock.
* Every Deadlock State is Unsafe.
* Not every Unsafe State is Deadlock.

## Banker's Algorithm

### What is it?

* A Deadlock Avoidance Algorithm.
* Before allocating resources, it checks whether the system remains in a Safe State.

### Why is it called Banker's Algorithm?

* Similar to a bank deciding whether to approve a loan.
* Resources are allocated only if the system remains safe.

### Information Maintained

#### Maximum

* Maximum resources a process may need.

#### Allocated

* Resources currently allocated to a process.

#### Need

* Resources still required by a process.

Formula:
Need = Maximum - Allocated

### Safe Sequence

* An order in which all processes can complete successfully.

### Goal

* Keep the system in a Safe State.
* Avoid Deadlock.

## Safe Sequence

### What is a Safe Sequence?

* An order in which all processes can complete successfully.

### Why is it Important?

* If a Safe Sequence exists, the system is in a Safe State.
* If no Safe Sequence exists, the system is in an Unsafe State.

### Checking a Safe Sequence

1. Check if a process can finish with currently available resources.
2. If yes, let it finish.
3. Release its allocated resources.
4. Increase available resources.
5. Repeat for remaining processes.

### Result

Safe Sequence Exists:

* Safe State

Safe Sequence Does Not Exist:

* Unsafe State

## Deadlock Detection

### What is it?

* A method where the OS allows resource allocation normally.
* If a deadlock occurs, the OS detects it later.

### Idea

* Do not prevent deadlocks.
* Do not avoid unsafe states.
* Detect deadlocks after they occur.

### How?

* Check for circular waiting among processes.
* If a cycle exists, deadlock may be present.

### Comparison

Prevention:

* Stop deadlock before it happens.

Avoidance:

* Stay in Safe State.

Detection:

* Allow deadlock and detect it later.
## Safe State

* OS can guarantee all processes can execute and complete successfully with available resources.
* There exists a Safe Sequence.
* Deadlock will not occur.

## Unsafe State

* OS cannot guarantee all processes will complete.
* Processes may execute or may get stuck later.
* Deadlock has not happened yet.
* There is a chance of Deadlock in future.

## Safe State vs Unsafe State

### Safe State

* OS knows all processes can finish.
* Safe Sequence exists.
* No Deadlock.

### Unsafe State

* OS is not sure all processes can finish.
* Safe Sequence may not exist.
* Deadlock may occur later.

### Important

* Unsafe State ≠ Deadlock
* Deadlock means processes are already stuck.
* Unsafe State means there is a risk of Deadlock.

## Banker's Algorithm

### What is it?

* A Deadlock Avoidance Algorithm.
* OS behaves like a banker.
* Before allocating resources, OS checks whether the system remains in Safe State.

### Why is it called Banker's Algorithm?

* Similar to a bank approving loans.
* Bank gives money only if it can still satisfy customers later.

### Main Idea

* Before giving resources:

  * Check Safe State.
* If Safe State remains:

  * Allocate resources.
* If Unsafe State occurs:

  * Do not allocate resources.

### Goal

* Keep the system in Safe State.
* Avoid Deadlock.

### Difference from Prevention

Deadlock Prevention:

* Break deadlock conditions.

Banker's Algorithm:

* Do not break conditions.
* Check safety before allocation.

## Banker's Algorithm Terms

### Maximum

* Maximum resources a process may require.

### Allocated

* Resources already assigned to a process.

### Need

* Additional resources required to complete execution.

Formula:

Need = Maximum - Allocated

### Example

Maximum = 10

Allocated = 4

Need = 6

Meaning:

* Process may need at most 10 resources.
* It already has 4 resources.
* It still needs 6 more resources to finish.

## Deadlock Recovery

* Deadlock Recovery is used after deadlock is detected.
* Purpose is to remove deadlock and continue execution.

### Methods

#### 1. Process Termination

* Kill one or more processes involved in deadlock.
* Resources are released.

#### 2. Resource Preemption

* Forcefully take resources from one process.
* Give resources to another process.
* Deadlock is broken.

### Easy Understanding

Deadlock happened already:

* Kill process
  OR
* Take resources and reassign them
