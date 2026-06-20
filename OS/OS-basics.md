
## What is an OS:
    - Operating system is a software that provides service to application programms.
    - Actually it is a intermediary(interface) between application programs and hardware device. 
    ### Without OS
        - Applications must directly communicate with hardware, which is difficult and complex.
        - Multiple applications may try to access hardware resources simultaneously, causing conflicts.
        - There is no protection between applications.
### Major responsibility of os
    - Process management: It will manage application programs starting stop and cpu scheduling time (Creates and terminates processes, Schedules CPU time among processes, Maintains process execution.)
    - Memory management: Manage or support ram memory means in ram which applications use how much memory
        - Manages RAM allocation and deallocation.
        - Decides how much memory each process receives.
        - Prevents processes from accessing each other's memory.
    - Device management: Control the hardware components
        - Controls hardware devices through device drivers.
        - Coordinates access to input/output devices.
    - File management: organize a file or directories means in this provide functionals functionality means features is retried code operations on files
        - Organizes files and directories.
        - Provides file operations such as create, read, write, rename, and delete.
    - Security and protection: Provide security to applications means the other application can't use the other application memory means access can't access other application memory
        - Restricts unauthorized access.
        - Prevents one process from accessing another process's memory.
        - Provides user and file protection mechanisms.
### Goals of os
    - End user can use system easily(Makes the computer easy and convenient for users.)
    - If new features added then it supports hardware components( Allows the system to support new hardware and features over time.)
    - Make effective operations (Utilizes hardware resources effectively.)

## Kernel vs User space 
### What is a kernal?
- Kernal is a core part of an OS.
- It Core functionities memory management device management process management and file management 
#### AI improvement:
- Kernel is the core component (brain) of the Operating System.
- Directly interacts with hardware.
- Manages:
    • Process Management
    • Memory Management
    • Device Management
    • File Management
### What is user space?
- User space run applications
- User space created in ram it is not fixed or part of ram but while application running then kernel create specific size of user space
#### AI improvement:
- User space is where application programs run.
- Applications execute with limited privileges.
- Applications cannot directly access hardware.
- The kernel allocates resources required by applications.
### Why can't Applications access hardware directly?
- Without operating system they caught access directly if they access directly then so many Bucks will happen means there is no security protection and each application not have scheduling time so system crasses, and applications can't control hardware directly
- So os provide separation in user space and kernel space in ram and node point here there is no fixed sizes in kernel space and user space or not in the part of ram
#### AI improvemnt: 
- Direct access is unsafe.
- Resource conflicts may occur.
- There is no protection between applications.
- A bug in one application may crash the entire system.
- The kernel provides controlled access to hardware.
### Why separate kernal space and user space?
- By separating kernel space and user space the os achieve three things that is very important and make powerful to you os
- Security & Protection: First is security and protection layer the any application can't directly access or control two hardware devices for process or any command also ask to kernel space S os decides means kernel decide to when to show and provide scheduled time also 
**In simple words**:  Applications cannot directly execute privileged operations.
- Stability: If any application crashes or have any bug then whole system not crashes by this specific one purpose so this separation of user spaces best and scale scalability 
**In simple words**: Failure of one application does not usually crash the whole system.
- Process Isolation: And last one is any application can't access directly its private memory means each application separate memory and there is no directly access or use other application memories
**In simple words**: Applications cannot access another application's private memory.

## Kernal mode vs User mode

### What is user mode?
- In user mode runs applications and it is exicution mode but it have limited privilege
- It can't directly access to hardware
- It can't execute privilege instructions 
- it provide security and protection to application

### what is kernal mode?
- Kernel mode it runs os kernel
- it have full privilege access
- It can execute privilege instructions
- How direct access to hardware 

### what are Privileged Instructions?
- Privilege instructions are those sensitive operations or major operations can be done by kernel itself
- Operations can be shutdown restart the system, Low level language operations, Execute privilege instructions etc 

### How does chrome read file?
- Chrome cannot directly access or help privilege to redefine so first it will run on user space and send a request means system call 2OS to perform operation then kernel it sends to cpu cpu switch the user mode to kernel mode and perform operation then again CPU6 to kernel mode 2 cpu mode then it will be provide result to chrome in user mode, So the chrome will show the result and execute the process in this manner. 

**Note**: Here user space user mode and kernal space kernal mode Difference or space means allocating a space to run the program and mode means performing operations or executing the privileges this is the different that's it

### Ai improved notes:
#### What is User Mode?

* User Mode is a restricted execution mode where application programs run.
* Applications execute with limited privileges.
* Applications cannot directly access hardware devices.
* Applications cannot execute privileged instructions.
* This separation provides security and protection to the system.

---

#### What is Kernel Mode?

* Kernel Mode is the privileged execution mode where the Operating System kernel runs.
* The kernel has full access to system resources.
* It can directly access hardware devices.
* It can execute privileged instructions.
* It manages processes, memory, files, and devices.

---

#### What are Privileged Instructions?

* Privileged instructions are sensitive operations that can only be executed in Kernel Mode.
* These operations affect the entire system and therefore require higher privileges.

### Examples:

* Shutting down or restarting the system.
* Accessing hardware devices directly.
* Configuring interrupts.
* Modifying memory management structures.
* Performing low-level device operations.

---

## How Does Chrome Read a File?

1. Chrome runs in User Mode.
2. Chrome cannot directly access the SSD.
3. Chrome requests the Operating System service through a System Call.
4. The CPU switches from User Mode to Kernel Mode.
5. The kernel performs the file read operation by accessing the hardware.
6. The requested data is returned to Chrome.
7. The CPU switches back to User Mode.
8. Chrome continues execution using the received data.

---

#### Important Note: User Space vs User Mode

##### User Space

* Refers to the logical execution environment where application programs run.
* It describes where applications execute from the Operating System perspective.

##### User Mode

* Refers to the CPU privilege level while executing instructions.
* It describes what operations the CPU allows a program to perform.

##### Kernel Space

* Refers to the logical execution environment of the Operating System kernel.

##### Kernel Mode

* Refers to the CPU privilege level with full access to system resources.

##### Easy Way to Remember

User Space / Kernel Space:

* Focus on "Where does the software run?"

User Mode / Kernel Mode:

* Focus on "What privileges does the CPU allow while executing instructions?"


## System Calls

### What is a System Call?

* System Call is a mechanism used by applications to request services from the Operating System.
* It acts as an interface between applications and the OS kernel.
* Without System Calls, applications cannot communicate with the Operating System.

---

### Why Do We Need System Calls?

* Applications run in User Mode.
* Applications cannot directly access hardware. so use system calls(use as request) to communicate and get os service
* The kernel provides controlled access(validate the request) to resources.
* System Calls provide abstraction from low-level hardware details(application don't need to know about hardware details).

---

### System Call Flow

Application
↓
System Call
↓
CPU switches User Mode → Kernel Mode
↓
Kernel validates the request
↓
Kernel performs the operation
↓
CPU switches Kernel Mode → User Mode
↓
Application receives the result

---

### Categories of System Calls

#### Process Control

Examples:

* fork() (create a new process)
* exec() (replace with current process with a new program)
* wait() 
* exit()

Purpose:

* Create, execute, wait for, and terminate processes.

#### File Management

Examples:

* open()
* read()
* write()
* close()

Purpose:

* Perform operations on files.

#### Device Management

Purpose:

* Access and control hardware devices.

#### Information Maintenance

Examples:

* getpid() (get process id)
* time() (get current time)
* uname() 

Purpose:

* Retrieve or update system information.

#### Communication (IPC)

Purpose:

* Allow processes to exchange information.

Examples:

* Pipes
* Shared Memory
* Message Queues
* Signals
* Sockets



## Monolitic VS Micro kernels

### What is kernel architecture?
- Kernel architecture is how Operating system services runs? means all services runs on kernal space or some servcies runs in kernal and other in user
- Two major kernel architecture is there, remaining is there but they are varients of the two architecture
    - Monolithic kernal
    - Micro kernal

### Monolithic Kernel:  
    - In this all OS services runs in kernel space 
    - The kernel space size is large because large code runs with full privalage 
    - it is best in performance because all services are close and so communication is well and there is less switching modes
    - but less stable, maintanence and security by comparing to micro kernal

### Microkernel:
    - In this divided OS services into essential and non-essential, only essential services runs on kernal space and non-essential services runs on user space
    - the kernel space size is small because only essential services runs 
    - it is best in stability, maintanence and security 
    - but less in performance by comparing to monolithic kernel


## Types of OS
- **Batch OS**: 
    - The flow of batch os is user give job to operator and Operator generate a punch cards and make batch put in a computer and they get a result
    - Here one badge have more than one job So more user can get result at a time
    - Advantage: One time setup and execute batches
    - Disadvantage: No debugging no interaction users had to wait long time even program is small but waiting time is same per batch 
- **Time Sharing os**:
    - Time sharing OS solves interaction with computer and reduce response time Users work simultaneously 
    - Here one computer but users are more means one cpu and Each user have its own screen keyboard to work 
    - But But here users are not working simultaneously this cpu make time slice here means each user get specific millisecond time so they think they are working simultaneously .
    - Advantage:  Interaction with users reduce time
    - Disadvantage: Securities is not proper and switching contact switching
- **Distribution os**: 
    - Distribution OS means its work like one system means here more than one system this each system have its own cpu ram screen etc means each system are called computers but they work like one system
    - Assume if user provide task then the distribution aware distribute the task into chunks and computers work those tasks and provide more computers to more fast work here user do not know which computer is do what task
    - Advantage: Share task come and communicate each other and easy to add more computers
    - Disadvantage: More cost and hard to handle those computers and hard to debugging because user don't know which computer can solve which type of task 
- **RTOS**:
    - The operating system are fast but some systems want predictable task or complete task in a provided time or fixed time or I can say in a given time.
    - Here in this divided into two parts Hard RTOS and soft RTOS 
    - Hard RTOS means if given task not completed in a given timeline or specific timeline then it is not acceptable.
    - Soft RTOS means completed in a given timeline or specific timeline then it is acceptable not restricted
    - Advantage: Predictable and fast
    - Disadvantage: complex to design, expensive and less flexible
- **Network OS**: 
    - Network operating system is created because if grouped members work together and they can communicate each other this is a purpose of to create a network operating system for example offices labs and colleges 
    - In network operating system users can communicate through systems and share task files etc 
    - And each user know what task they are doing and how much they are completed in simple words progress 
    - Advantage: Resource sharing, centrilze administration, best access control and easier collaboration
    - Disadvantage: network dependency, server failure effect users, setup and maintanence cost 

    