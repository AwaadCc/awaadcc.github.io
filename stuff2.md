### 1. **What are protection rings used for? When a privileged instruction is executed in user mode, what will happen?**
- **Protection Rings**: Layers of privilege in an operating system to enforce security and stability. 
  - **Ring 0**: Kernel mode (most privileged).
  - **Ring 3**: User mode (least privileged).
- **Privileged Instruction in User Mode**: 
  - Triggers a **trap** or **general protection fault**, switching the CPU to kernel mode to handle the violation.

### 2. **If a user program can jump to any location of the kernel, what would be the security concern? How is the system call implemented?**
- **Security Concern**: Direct kernel access risks:
  - Overwriting kernel data.
  - Executing malicious instructions.
- **System Call Implementation**:
  1. Uses **software interrupts** (`INT 0x80`) or **syscall** instructions.
  2. Saves current user state, switches to kernel mode, and runs the kernel handler.

### 3. **What are the differences of threads and processes? What are the pros and cons of using multiple threads compared to using multiple processes?**
- **Processes**:
  - Independent execution units with separate memory.
  - Robust isolation but higher overhead.
- **Threads**:
  - Share memory within a process.
  - **Pros**: Faster creation, lower context-switch cost.
  - **Cons**: A thread crash can crash the entire process.

### 4. **What are Stack Pointer/Stack Frame/Call Stack/PCB?**
- **Stack Pointer**: Points to the current top of the stack.
- **Stack Frame**: Stores local variables, return address, and parameters.
- **Call Stack**: Tracks function call history.
- **PCB (Process Control Block)**: Stores process metadata (e.g., PID, state, registers).

### 5. **All the details about Process Switch**
- **Steps**:
  1. Save current process state in PCB.
  2. Choose next process (from Ready queue).
  3. Load the state of the new process.
- Involves saving/restoring registers, program counter, and stack pointers.

### 6. **Process state transition. For example, can a process go from the Blocked state to the Running state directly?**
- **States**: New â†’ Ready â†’ Running â†’ Blocked â†’ Terminated.
- **Blocked to Running**: 
  - No, it must first move to **Ready** when its event completes.

### 7. **When does the CPU mode change from the User Mode switch to the Kernel Mode?**
- Triggered by:
  - **System calls**.
  - **Exceptions** (e.g., divide by zero).
  - **Hardware interrupts** (e.g., I/O events).

### 8. **Give a concrete example for Exception, Signal, and Interrupt each. What are the differences?**
- **Exception**: Divide by zero (synchronous).
- **Signal**: `SIGKILL` to terminate a process.
- **Interrupt**: Hardware event like a keyboard press.

### 9. **Implement a Shell; make sure you really understand every line of the code.**
```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    char *args[] = {"ls", NULL};
    while (1) {
        printf("> ");
        char input[100];
        fgets(input, sizeof(input), stdin);
        if (fork() == 0) {
            execvp(input, args);
        } else {
            wait(NULL);
        }
    }
    return 0;
}
```

### 10. **Why is the Zombie state necessary?**
- Allows the parent process to **read the exit status** of a terminated child.

### 11. **When you do a keystroke, how does your computer (hardware and software) respond to it step by step?**
1. Keyboard generates an **interrupt**.
2. Interrupt controller notifies CPU.
3. OS handles the interrupt, translates the input.
4. Passes the input to the active process.

### 12. **The differences of the various IPC methods**
- **Pipes**: Simple, unidirectional communication.
- **Shared Memory**: Fast, but needs synchronization.
- **Message Queues**: Structured, kernel-mediated data exchange.
- **Sockets**: For network-based communication.

### 13. **Why is Synchronization needed when multiple processes â€œwithdraw money from a banking accountâ€?**
- **Race Condition**: Concurrent access leads to incorrect results.
- **Critical Section**: Protected block for accessing shared data.

### 14. **Implement a busy-waiting lock using test_and_set and explain why it works**
```c
int lock = 0;
void acquire_lock() {
    while (test_and_set(&lock)); // Spins until lock is free
}
void release_lock() {
    lock = 0;
}
```
- **Why it works**: `test_and_set` atomically sets the lock, preventing race conditions.

### 15. **All the details about the two APIs of Semaphores**
- **`sem_wait()`**: Decrements the semaphore, blocks if â‰¤ 0.
- **`sem_post()`**: Increments the semaphore, wakes a waiting process.

### 16. **List the three main synchronization needs. How to write code to meet the needs?**
1. **Mutual Exclusion**: Use locks or semaphores.
2. **Order Enforcement**: Use condition variables.
3. **Resource Allocation**: Use counting semaphores.

### 17. **What are the four conditions for a deadlock? How to draw a resource allocation graph?**
- **Conditions**:
  1. Mutual Exclusion.
  2. Hold-and-Wait.
  3. No Preemption.
  4. Circular Wait.
- **Resource Allocation Graph**: Nodes represent processes/resources, edges represent allocations/requests.

### 18. **Why can Resource Numbering prevent deadlocks?**
- Enforces a strict order of resource requests, breaking the **circular wait** condition.

### 19. **List the CPU scheduling policies you have learned? The comparison. Why is Round Robin unfair? How to fix the unfairness? All the details of MFQ (make sure you really understand them).**
- **Policies**:
  1. **FCFS (First Come First Serve)**: Simple but causes **convoy effect**.
  2. **SJF (Shortest Job First)**: Optimal for minimizing waiting time but requires future knowledge.
  3. **Round Robin**: Allocates fixed **time slices** to processes. Unfair to I/O-bound processes as they may waste time slices.
  4. **Multilevel Feedback Queue (MFQ)**: 
     - Processes move between priority queues based on behavior.
     - **Fixing Unfairness**: High-priority queues have short time slices to prioritize responsiveness; low-priority queues have longer slices to favor CPU-bound tasks.

### 20. **In MFQ, why is a small CPU time slice allocated for high-priority queue? Why is a large slice allocated for a low-priority queue?**
- **High-Priority Queues**: Short slices to improve responsiveness for interactive tasks.
- **Low-Priority Queues**: Longer slices for CPU-bound tasks to reduce context-switching overhead.

### 21. **How to interpret a virtual address? How to decompose it into page# and offset?**
- **Virtual Address**: Divided into:
  - **Page Number**: Identifies the page in the page table.
  - **Offset**: Specifies the location within the page.

### 22. **How to do address translation with paging?**
1. Split virtual address into **page number** and **offset**.
2. Look up the page number in the **page table** to get the physical frame.
3. Combine the frame and offset to form the **physical address**.

### 23. **In which senses paging is better than segmentation?**
- **Advantages of Paging**:
  - No **external fragmentation**.
  - Efficient memory usage with fixed-size pages.
  - Supports dynamic memory growth.

### 24. **Why multi-level page tables?**
- Reduces memory consumption by splitting the page table into smaller tables.
- Efficient for large address spaces (e.g., 64-bit systems).

### 25. **Zero copy and sendfile()**
- **Zero Copy**: Avoids copying data between kernel and user space.
- **`sendfile()`**: Directly transfers data from disk to network socket, bypassing user space.

### 26. **Memory hierarchy**
- **Levels**: Registers â†’ Cache â†’ Main Memory (RAM) â†’ Disk â†’ Tape.
- Faster storage has less capacity but lower latency.

### 27. **Buffering and caching**
- **Buffering**: Temporarily holds data to manage speed mismatches (e.g., between CPU and I/O devices).
- **Caching**: Speeds up repeated access to data.

### 28. **How does the kernel deal with the numerous kinds of devices?**
- **Device Drivers**: Abstract device details and provide a standard interface.
- **Layering**: OS communicates with devices via standardized APIs.

### 29. **Thrashing**
- Occurs when excessive **page faults** cause frequent swapping, reducing performance.
- **Solution**: Implement **working set model** and **page replacement algorithms**.

### 30. **Cache replacement algorithms. LRU, Clock, n-th chance.**
- **LRU (Least Recently Used)**: Evicts the least recently accessed page.
- **Clock Algorithm**: Uses a circular buffer and reference bit to approximate LRU.
- **n-th Chance**: Gives pages multiple chances before eviction.

### 31. **Fragmentation in memory allocation**
- **Internal Fragmentation**: Wasted space inside allocated blocks (e.g., fixed-size partitions).
- **External Fragmentation**: Wasted space outside allocated blocks (e.g., dynamic partitions).

### 32. **How does memory mapped file I/O work?**
- Maps a file into virtual memory.
- Accessing the file becomes equivalent to accessing memory.

### 33. **The detailed steps of handling a page fault**
1. Process accesses a non-resident page.
2. Hardware triggers a **page fault exception**.
3. OS identifies the page and loads it from disk.
4. Updates the page table.
5. Resumes process execution.

### 34. **Locality and TLB**
- **Locality**:
  - **Temporal Locality**: Repeated access to recently used data.
  - **Spatial Locality**: Access to nearby memory locations.
- **TLB (Translation Lookaside Buffer)**: Caches recent address translations to speed up paging.

### 35. **Copy on write; fork()**
- **Copy-On-Write (CoW)**: Parent and child processes share memory pages after `fork()` until a write occurs, triggering a page copy.

### 36. **Demand paging**
- Pages are loaded into memory **on demand** when accessed, rather than preloading.

### 37. **How is shared memory implemented?**
- Processes attach to a shared memory segment using system calls like `shmget()` and `shmat()`.

### 38. **Why is FAT better than the naÃ¯ve file system design?**
- **FAT (File Allocation Table)**: Centralized index allows faster file access compared to a linked-list design.

### 39. **Inode; symbolic link; hard link**
- **Inode**: Data structure containing metadata and pointers for file data.
- **Hard Link**: Directly points to the fileâ€™s inode.
- **Symbolic Link**: Points to the file path, not the inode.

### 40. **fread vs read**
- **`fread`**: Buffered I/O (uses stdio library).
- **`read`**: Unbuffered, direct system call.

### 41. **What does mounting do under the hood?**
- Attaches a file system (on a device) to the existing directory hierarchy.

### 42. **File access permissions**
- Permissions: `r` (read), `w` (write), `x` (execute) for owner, group, and others.

### 43. **Setuid programs**
- **Setuid Bit**: Allows a program to execute with the privileges of its file owner rather than the user running it.