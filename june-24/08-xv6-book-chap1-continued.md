There are three requirements of an OS 
- multiplexing
- isolation
- interaction

Layout of a virtual address space of a process
```
 ---------------
|free memory    |
|               |
 ---------------
|text and data  |
 ---------------
| BIOS          |
 ---------------
|heap           |
|               |
 ---------------
|user stack     |
 ---------------
|user text and  | 
|data           |
 ---------------
```
- xv6 maintains per process page table where each page table maps a virtual memory address to the physical one in RAM
- kernel runs in its own address space

 
