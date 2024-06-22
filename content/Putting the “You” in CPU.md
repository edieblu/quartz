---
tags:
  - ✅
published: true
sr-due: 2025-08-25
sr-interval: 434
sr-ease: 290
---

⬅️ [[CS]]

🔗 https://cpu.land/
Fun and informative, written by: https://kognise.dev/
Keep at it!

- The _central processing unit_ (CPU) of a computer is in charge of all computation.
- today we use [64-bit](https://en.wikipedia.org/wiki/64-bit_computing) systems
- The “instructions” that CPUs execute are just binary data: a byte or two to represent what instruction is being run (the opcode), followed by whatever data is needed to run the instruction.
- What we call _machine code_ is nothing but a series of these binary instructions in a row. 
- [Assembly](https://en.wikipedia.org/wiki/Assembly_language) is a helpful syntax for reading and writing machine code that’s easier for humans to read and write than raw bits; it is always compiled to the binary that your CPU knows how to read.

- RAM is your computer’s main memory bank, a large multi-purpose space which stores all the data used by programs running on your computer.
- The CPU always reads machine code directly from RAM, and code can’t be run if it isn’t loaded into RAM.
- The CPU stores an _instruction pointer_ which points to the location in RAM where it’s going to fetch the next instruction. After executing each instruction, the CPU moves the pointer and repeats. This is the _fetch-execute cycle_.
- The instruction pointer is stored in a [_register_](https://en.wikipedia.org/wiki/Processor_register). Registers are small storage buckets that are extremely fast for the CPU to read and write to. Each CPU architecture has a fixed set of registers, used for everything from storing temporary values during computations to configuring the processor.