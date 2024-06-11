# RISC-Computer-in-Verilog
A simple RISC computer written in Verilog using Altera's Quartus II 13.1 (64-bit)

## Objectives
This is a recreation of a school project in Verilog. It's components are a processor memory, and I/O. There are three phases to this project: Phase 1, Phase 2, and Phase 3.

## Phase 1
- add, sub, mul, div, and, or, shr, shl, ror, rol, neg, and not instructions
- 16 32-bit registers R0 through R15
- 2 32-bit HI and LO registers for ALU
- 32-bit IR
- 32-bit PC (This works with IncPC control signal in the ALU)
- ALU
  - Two inputs: A and B (A needs to be stored in a temporary 32-bit register Y since only one can be handled at a time)
  - One output: C
  - 64-bit Z register that holds the result of a multiplication (product) or a division (remainder in the higher byte and quotient in the lower byte) before loading it into HI and LO registers
  - Memory Address Register (MAR): holds an address
  - Memory Data Register (MDR): holds data that was fetched or to be fetched
  - Select and Encode Logic signals: transfer contents from the bus or to the bus
  - CON FF for branching
  - 32-bit registers In.Port and Out.Port
  - PORT (control signals)
- Bus
  - 32-to-5 encoder that feeds into a 32:1 multiplexer
  - The output of the multiplexer is BusMuxOut which is the bus
  - Data line, address line, and control line
- Memory Data Register
  - Two inputs: BusMuxOut and Mdatain
  - Two outputs: BusMuxIn-MDR or to memory chip
- Control Unit (in Phase 3)

### Inputs & Outputs
Register (Clear, clock, writeEnable)
Memory Data Register (Clear, clock, writeEnable, readSignal)
Bus Encoder (Signals for each register)
Bus Multiplexer (The actual data)
ALU (Control signals for each)

### Terminologies
System Resource Controller (SRC): It is used to manage resources for memory allocation, task scheduling, power management, and peripheral device control. The difference between an SRC and a processor is that a processor's main role is to execute instructions. An SRC can be incorporated into a processor.

## Phase 2
- Load and Store insturctions ld, ldi, and st to test the Memory Subsystem and the Select and Encode logic
- addi, andi, and ori
- brzr, brnz, brmi, and brpl to test the flip-flop logic
- jr and jal
- mfhi and mflo
- in and out to test the "Input/Output"
- Memory Subsystem
  - MDR and MAR
  - RAM (Read signal, write signal, data, address)
- Select and Enocde
  - Takes Gra, Grb, Grc, Rin, Rout, and BAout signals and generates R0in - R15in signals and R0out - R15out signals
  - Grant signals are ANDed with the opcode decodes and fed into the decoder to select Rin and Rout signals (they have to be ANDed again with Rin signal and Rout signal)

## Phase 3
- Control Unit
  - This is where you put everything you have designed previously into one single control unit
  - The way we designed it was for each instruction we had different states that were used to state what happens in each instruction decoding process
  - fetch0: increment the PC and load the address into MAR
  - fetch1: load in PC and read the memory
  - fetch2: load that data into MDR
- Opcode decode
  - Select the intruction based on the opcode
  - Based on the state of the opcode, move to next step
