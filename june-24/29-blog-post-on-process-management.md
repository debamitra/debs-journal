Going to work on the first article for my series on Operating Systems Concepts. Breaking it down into small tasks, lets go

Random info about OS booting -
- UEFI is the firmware program which is loaded from ROM to initialize the system when a computer is powered on. (BIOS is for older systems)


- UEFI --- (loads the bootloader from storage/disk(boot partition) into memory at some location) ---> BOOTLOADER --- (loads kernel image from disk into memory) --> kernel starts processes(?)

Right now watching xv6 playlist -
- [ ] Learning about trap handling
- [ ] Context switching

- [ ] Brainstorming on ideas for article on process management :
      
      - Processes and their States , PCB
      - Process Creation and Termination - fork, exec, exit, kill
      - Process scheduling - 
      - Interprocess communication
      - Context switching
      - System calls related to Process management
      - xv6 DEEP DIVE
        Process Structure
        - Show the structure of a process in xv6 (e.g., struct proc)
        Forking a Process
        - Explain how fork() works in xv6 with a simple flowchart or diagram
        Scheduling
        - Illustrate how the scheduler works in xv6 with a diagram of the scheduling loop. etc

Writing some scripts to draw graphs of CPU  allocation over time 

I feel a bit overwhelmed. Where should I start working on the article. I dont know. Let me see. Will continue watching xv6 playlist for now and make some notes. I am at lecture 9.



