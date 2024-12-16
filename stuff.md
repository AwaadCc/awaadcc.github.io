Comprehensive Study Guide for CS 471 Final Exam
-------------------------------------------------

### 1. Protection Rings and Privileged Instructions
- **Protection Rings**: Layers of privilege in an operating system to enforce security and stability. Ring 0 (kernel mode) has the most privileges; user applications run in higher-numbered rings (less privileged).
- **Privileged Instruction in User Mode**: If attempted, the system triggers a General Protection Fault, transitioning control to the kernel for error handling.

### 2. System Call Implementation and Security Concerns
- **Security Concern**: If a user program can jump to kernel space arbitrarily, it could overwrite sensitive data or execute malicious code.
- **System Call Mechanism**: Implemented via software interrupts or specific instructions like `INT 0x80` or `sysenter`. Transitions the CPU to kernel mode safely.

### 3. Threads vs Processes
- **Threads**: Lightweight, share memory within a process.
  - *Pros*: Cheaper to create, faster context switch, easier data sharing.
  - *Cons*: One thread crash can affect the entire process.
- **Processes**: Independent, separate memory spaces.
  - *Pros*: Robust isolation.
  - *Cons*: More overhead for communication and switching.

### 4. Stack Components
- **Stack Pointer**: Points to the top of the current stack.
- **Stack Frame**: Stores function-specific information (e.g., parameters, local variables, return address).
- **Call Stack**: Tracks nested function calls.
- **PCB (Process Control Block)**: Kernel structure holding process metadata.

### 5. Process Switch
- Saves the current process state into its PCB and restores the next scheduled process's state.
- Involves saving/restoring:
  - CPU registers.
  - Memory mappings.
  - Instruction pointer and stack pointer.

### 6. Process State Transitions
- **States**: New → Ready → Running → Blocked → Terminated.
- A process cannot transition directly from **Blocked** to **Running**. It must first move to **Ready** when the event completes.

### 7. CPU Mode Transitions
- **User Mode to Kernel Mode**: Triggered by:
  - **System calls** (e.g., file read/write).
  - **Exceptions** (e.g., divide by zero).
  - **Hardware interrupts** (e.g., keyboard input).

### 8. Examples of Exception, Signal, and Interrupt
- **Exception**: Divide by zero error (software-triggered, synchronous).
- **Signal**: Notification (e.g., SIGTERM to terminate a process).
- **Interrupt**: Keyboard input (hardware-triggered, asynchronous).

### 9. Shell Implementation
- Components:
  - Parse user input.
  - Create child processes with `fork()`.
  - Execute commands with `execvp()`.
- Example:
```c
while (1) {
  printf("> ");
  fgets(command, sizeof(command), stdin);
  if (fork() == 0) {
    execvp(command, args);
  } else {
    wait(NULL);
  }
}
```

### 10. Zombie State
- Necessary to allow a parent process to retrieve the **exit status** of a terminated child.

### 11. Keystroke Handling
1. **Hardware**: Keyboard generates an interrupt.
2. **Driver**: Interrupt handler translates key press into a code.
3. **Kernel**: Passes the code to the active process via the input buffer.
4. **Software**: Application interprets the keystroke.

### 12. IPC Methods
- **Pipes**: Simplest, unidirectional communication between processes.
- **Shared Memory**: Fastest, but requires synchronization.
- **Message Queues**: Suitable for structured data exchange.
- **Sockets**: Used for inter-system communication.

### 13. Synchronization and Banking Example
- **Why Needed**: Prevents **race conditions** (e.g., two processes withdrawing simultaneously, leading to incorrect balances).
- **Critical Section**: Code block accessing shared resources.
- **Solution**: Synchronization primitives (e.g., mutexes, semaphores).

### 14. Busy-Waiting Lock with `test_and_set`
```c
int lock = 0;
void acquire_lock() {
  while (test_and_set(&lock));
}
void release_lock() {
  lock = 0;
}
```
- Works because `test_and_set` atomically sets a variable, preventing race conditions.

### 15. Semaphore APIs
- `sem_wait()`: Decrements the semaphore, blocks if < 0.
- `sem_post()`: Increments the semaphore, waking blocked processes.

### 16. Three Main Synchronization Needs
1. **Mutual Exclusion**: Only one process accesses critical section.
2. **Order Enforcement**: Ensure operation A precedes B.
3. **Resource Allocation**: Manage limited resources (e.g., semaphores).

### 17. Deadlock Conditions and Resource Allocation Graph
- **Conditions**:
  1. Mutual Exclusion.
  2. Hold-and-Wait.
  3. No Preemption.
  4. Circular Wait.
- **Resource Allocation Graph**: Nodes (resources/processes) and edges show dependencies.

### 18. Resource Numbering and Deadlock Prevention
- Assign unique resource IDs. Processes request resources in increasing order to break circular wait.

### 19. CPU Scheduling Policies
- **FCFS**: Simple but can cause starvation.
- **SJF**: Optimal for minimizing wait time but requires future knowledge.
- **Round Robin**: Allocates time slices; unfair for I/O-heavy tasks.
- **Multilevel Feedback Queue (MFQ)**: Dynamic priorities based on behavior.

### 20. Paging vs Segmentation
- **Paging**: Fixed-size memory chunks; no external fragmentation.
- **Segmentation**: Variable-size chunks; better for logical organization.

### 21. Page Fault Handling Steps
1. Process tries accessing a page not in memory.
2. **Page Fault** trap occurs.
3. Kernel locates the page on disk.
4. Loads page into memory and updates page table.

### 22. Copy-On-Write in Fork
- Parent and child processes share memory until one writes, triggering a copy of the modified page.

### 23. File Systems
- **FAT**: Simple but inefficient for large disks.
- **Inode**: Efficient storage of metadata and pointers.
- **Symbolic Links**: Point to file paths, unlike **Hard Links**, which point directly to file data.

### 24. Caching and Buffering
- **Cache**: Speeds up repeated access (e.g., page cache).
- **Buffer**: Temporarily holds data to handle speed mismatches (e.g., I/O buffering).
