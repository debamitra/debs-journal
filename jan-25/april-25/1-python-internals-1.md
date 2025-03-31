## Python Internals: List vs Generator

### Goal:
Understand how Python handles list comprehensions vs generators in memory, time, and internals.

### Tools Used:
- dis
- timeit
- memory_profiler
- tracemalloc
- gc

### Observations:
- Bytecode: Generators defer execution with BUILD_GEN.
- Time: Lists are faster upfront but expensive in memory.
- Memory: Generators are incredibly memory efficient.
- GC: Lists may trigger GC under pressure, generators usually don’t.
