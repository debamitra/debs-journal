Mostly occupied with work today, a production bug in one project, some calls and testing support for another. Cook didnt show up today, so we ordered out. Mom made cheese potato sandwiches and tea in the evening. 

#### Study..
I watched a couple of videos from the xv6-riscV playlist today. It was about system calls from user code and the riscV architecture. Let me summarize the second lecture a bit. So they talked about all the different registers (31 of them) and the Program counter and the CSRs (Control/Status Registers). I am curious about registers in the x86 version of xv6, will look those up tomorrow. Also talked about the 3 modes - 
- Machine mode for machine startup and initialization code and time interrupts,
- Supervisor mode for kernel code
- and user mode for userland code

They talked about the definition of Exceptions and Interrupts which I found helpful, was a bit confused earlier. Both are TRAPS, which is the more generic term.
- Exceptions are synchronous and occur within the flow of either system call instructions being executed or as a program error like segfaults etc.
- Interrupts are aysnchronous and raised from somewhere else. There are 3 types
  - Timer interrupts
  - Software interrupts
  - Device interrupts
 
**Some questions I need to look into -**
1. user code / kernel code vs code running in user mode / kernel mode - whats the difference?
2. this is the first I am hearing about machine mode, whats that, investigate further
3. lecture above talks about context switches again and I was confused, probably a rewatch is needed..

#### randomly questioning the GPT..
Its really hot today, I hope it rains tommorow otherwise life just seems a little meh. 
Ah and a short note on some stuff I was asking GPT - When a computer powers on, the CPU (0th core) starts executing the instruction from some designated memory location (in the ROM/Firmware). This code which is called BIOS basically runs those  basic hardware tests, initializes basic CPU. memory etc, then searches for a bootable disk, loads the boot loader from it,,and so on.  

More tomorrow, Goodnight.
