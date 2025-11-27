# Excel CPU with 8-Bit Architecture
This repository contains the an Excel file emulating a simple 8-bit architecture CPU ***(code/cpu8bit.xlsx)***, the description of the usable instruction set ***(docs/Excel_CPU_Instruction_Set_Manual.docx)*** for it and three examples implementing classic algorithms ***(docs/Excel_CPU_Programs.docx)***. The CPU operates on 8-bit registers with modulo 256 arithmetic and features a specific set of flags and control flow mechanisms.

The CPU utilizes four primary 8-bit general-purpose registers and a byte-addressable RAM system.
- Registers: AX, BX, CX, DX (Range: 0–255).
- Program Counter (PC): Selects the next instruction to execute.
- RAM: Byte-addressable storage.

Three status flags are updated only during addition (ADD) and subtraction (SUB) operations.
- ZF: Zero FlagSet to 1 if the result is 0.
- CF: Carry FlagSet to 1 if an arithmetic carry/borrow occurs.
- SF: Sign FlagSet to 1 if the result is greater then 128.


The Excel file with three sheets operates as a step-by-step emulator for the 8-bit CPU.

**To use the emulator write your assembly code instruction by instruction, ensuring you follow the correct syntax as defined in the Instruction Set Manual and the contant of each sheet as described below**

***PROGRAM*** Sheet

This sheet serves as your source code editor, defining the sequence of instructions the CPU will execute. You input your assembly code here. The CPU reads the instruction on the line indicated by the Program Counter (PC) and executes it.
It is organized as a numbered list of instructions. The essential columns are:
- ADDR: Address Line Number
- MNEM: Mnemonic, abbreviation of an operation
- OP1: Operand 1, often the destination register
- OP2: Operand 2, the source or immediate value
- OPCODE: operation code
- ARG1: code/value of the first argument
- ARG2: code/value of the second argument
- HUMAN: the whole opearation as a string

***CPU*** Sheet

This sheet acts as the main dashboard, displaying the internal state of the processor at every cycle. This is where you monitor the program's execution.
It logs the state over time using rows. The key columns are:
- PC: Program Counter, the address line number of the instruction currently being executed.
- AX, BX, CX, DX: The current value held in each of the four 8-bit registers.
- ZF, CF, SF: The status (1 or 0) of the Zero, Carry, and Sign Flags.
- Halted: A flag indicating whether the CPU has stopped (HLT instruction).
It also contains a snapshot of the RAM values at that cycle.

***RAM*** Sheet

This sheet represents the RAM (Random Access Memory) used for data storage outside of the four main registers. A simple two-column table listing memory ADDR (Address) and the corresponding VALUE stored at that location.

  
