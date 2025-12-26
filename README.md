# 🔢 Excel-Based 8-Bit CPU Emulator

A simulation of a **simple 8-bit CPU** implemented entirely in Microsoft Excel — no macros or code required!

This project emulates a basic processor with registers, RAM, a program counter, status flags, and a custom instruction set. Users write assembly-like programs in one sheet, and the CPU executes them cycle-by-cycle, updating registers, flags, and memory visibly across workbook sheets.

Perfect for learning computer architecture, assembly programming, and how CPUs work under the hood.

---

## 🚀 Features

- **8-Bit Architecture:** Modulo-256 arithmetic (unsigned bytes 0–255).
- **Registers:** Four general-purpose 8-bit registers (AX, BX, CX, DX).
- **Memory:** Byte-addressable RAM (editable table).
- **Program Counter (PC):** Automatically advances through instructions.
- **Status Flags:** ZF (Zero), CF (Carry), SF (Sign) — updated on ADD/SUB.
- **Instruction Set:** Custom mnemonics with opcodes and operands (full manual included).
- **Cycle-by-Cycle Execution:** View state changes row-by-row in the CPU sheet.
- **Halt Support:** HLT instruction stops execution.
- **Pure Spreadsheet:** All logic via Excel formulas — transparent and modifiable.

---

## 📂 Project Structure

`cpu8bit.xlsx`                # Main emulator workbook (PROGRAM, CPU, RAM sheets) <br>

`Excel_CPU_Instruction_Set_Manual.docx`  # Full instruction set reference (mnemonics, opcodes, syntax) <br>
`Excel_CPU_Programs.docx`     # Three example programs with explanations <br>


---

## 🧠 Theoretical Background

This Excel-based emulator faithfully recreates the fundamental principles of a **von Neumann architecture** CPU at the simplest possible level, making abstract computer science concepts tangible through everyday spreadsheet formulas.

### 1. Von Neumann Architecture Basics

Modern computers follow the **von Neumann model**:
- **Single shared memory** for both instructions (code) and data.
- **Sequential execution**: Instructions fetched from memory, decoded, and executed one after another.
- **Central Processing Unit (CPU)** containing:
  - Registers (fast internal storage)
  - Arithmetic Logic Unit (ALU) for computations
  - Control Unit managing the fetch-decode-execute cycle

In this emulator:
- **PROGRAM sheet** = Code memory (instructions)
- **RAM sheet** = Data memory
- **CPU sheet** = Control unit + registers + ALU + execution log

### 2. The Fetch-Decode-Execute Cycle

Every CPU operates in an endless loop known as the **instruction cycle**:

1. **Fetch**: Read the instruction at the current Program Counter (PC).
2. **Decode**: Interpret the opcode and identify operands.
3. **Execute**: Perform the operation (move data, add, subtract, etc.).
4. **Update PC**: Usually increment to next instruction (or jump if branching).
5. **Update flags**: Set Zero/Carry/Sign based on result.

The **CPU sheet** logs one row per cycle, showing exactly how this process unfolds — completely transparent because every step is a visible Excel formula.

### 3. 8-Bit Data Representation

All values are **8-bit unsigned integers** (0–255):
- Arithmetic wraps around at 256 (modulo 256).
- **Two's complement interpretation** for signed numbers:
  - 0–127 → positive
  - 128–255 → negative (e.g., 255 = -1, 254 = -2)
- **Flags** reflect this:
  - **ZF (Zero Flag)**: Set when result = 0
  - **CF (Carry Flag)**: Set on unsigned overflow (carry out of bit 7)
  - **SF (Sign Flag)**: Mirrors bit 7 (1 = "negative" in two's complement)

### 4. Registers and Memory Model

- **Four general-purpose registers** (AX, BX, CX, DX): 8-bit each, used for temporary storage and arithmetic.
- **Program Counter (PC)**: Points to current instruction address.
- **RAM**: 256 bytes (though only a subset shown), directly editable.
- **Separation of code and data**: Instructions live in PROGRAM sheet; data in RAM — classic Harvard vs. von Neumann distinction illustrated (this is pure von Neumann).

### 5. Instruction Set Architecture (ISA)

The emulator uses a **custom minimal ISA** designed for clarity:
- Fixed-format instructions (mnemonic + up to two operands).
- Operations include:
  - `MOV reg, value` / `MOV reg, reg` — data transfer
  - `ADD reg, value` / `ADD reg, reg` — addition with carry
  - `SUB reg, value` / `SUB reg, reg` — subtraction with borrow
  - `HLT` — halt execution

No branching yet — execution is strictly linear — which highlights how even simple sequential machines can perform meaningful computation.

It serves as a bridge between theoretical computer science and real hardware

An outstanding platform for teaching **computer organization**, **assembly language**, and the **essence of computation**! 🖥️

---

## 📦 How to Use

### 1. Open the Emulator
Download and open `code/cpu8bit.xlsx` in Microsoft Excel (or compatible like Google Sheets/LibreOffice).

### 2. Write a Program
- Go to the **PROGRAM** sheet.
- Enter instructions row-by-row (columns: ADDR, MNEM, OP1, OP2, etc.).
- Refer to `docs/Excel_CPU_Instruction_Set_Manual.docx` for valid mnemonics (e.g., MOV, ADD, SUB, HLT).

### 3. Run & Observe
- The **CPU** sheet automatically processes instructions starting from PC=0.
- Each row shows the state **after** executing one instruction.
- Scroll down to step through cycles.
- Check registers, flags, and RAM updates in real-time.

### 4. Examples
Open `docs/Excel_CPU_Programs.docx` for three ready-to-try programs (e.g., addition loops, data moves).

**Tip:** Modify formulas directly in Excel to extend the CPU (add new instructions, jumps, etc.)!

