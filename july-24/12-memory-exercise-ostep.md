Working on the Virtual Memory project for OSTEP-xv6 today. Picked up from where I last left off, dereferencing a null pointer was actually throwing an exception and traping into the kernel, then raising and error and killing the process. The Exercise though mentioned its not handled and should be printing the user code at memory 0x0. Thats not how the kernel implementation is right now though. 

Anyway, moving forward, will check out where the page table is being setup by xv6, where fork and exec are being called and how the address space is being copied from parent to child and then how we are referencing the entry point for user programs.

