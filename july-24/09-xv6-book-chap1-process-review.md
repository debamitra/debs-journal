### The first address space

When the PC is powered on, it loads bootloader from disk into memory and executes it. Bootload , loads the xv6 kernel into memory at 0x100000 of physical memory and executes it starting at entry point 
```asm
filename: entry.S

1040 entry:
1041 # Turn on page size extension for 4Mbyte pages
1042 movl %cr4, %eax
1043 orl $(CR4_PSE), %eax
1044 movl %eax, %cr4
1045 # Set page directory
1046 movl $(V2P_WO(entrypgdir)), %eax
1047 movl %eax, %cr3
1048 # Turn on paging.
1049 movl %cr0, %eax
.....
.....
```
To load rest of kernel, above code sets up page table that maps virtual addresses starting at 0x80000000 (called KERNBASE) to physical addresses starting at 0x0  

