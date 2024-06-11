# RISC-Computer-in-Verilog
A simple RISC computer written in Verilog using Altera's Quartus II 13.1 (64-bit)

## Objectives
This is a recreation of a school project in Verilog. It's components are a processor memory, and I/O. There are three phases to this project: Phase 1, Phase 2, and Phase 3.

### Phase 1
- add, sub, mul, div, and, or, shr, shl, ror, rol, neg, and not instructions
- 16 32-bit registers R0 through R15
- 2 32-bit HI and LO registers for ALU
- 32-bit IR
- 32-bit PC (This works with IncPC control signal in the ALU)
- ALU
  - Two inputs: A and B (A needs to be stored in a temporary 32-bit register Y since only one can be handled at a time)
  - One output: C
  - 

#### Terminologies
SRC (System Resource Controller): It is used to manage resources for memory allocation, task scheduling, power management, and peripheral device control. The difference between an SRC and a processor is that a processor's main role is to execute instructions. An SRC can be incorporated into a processor.

