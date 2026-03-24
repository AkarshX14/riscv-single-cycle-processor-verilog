
# 32-bit Single-Cycle RISC-V Processor (Verilog)

## Overview
This project presents the design and simulation of a **32-bit single-cycle RISC-V processor** using Verilog HDL. The processor executes instructions in a single clock cycle and implements a complete datapath and control unit.

It demonstrates fundamental concepts of **processor architecture, RTL design, and hardware verification**, making it suitable for academic and learning purposes in VLSI and embedded systems.

---

## Key Features
- 32-bit RISC-V ISA implementation
- Single-cycle processor architecture
- Modular RTL design
- Supports multiple instruction formats:
  - **R-type** → ADD, SUB, AND, OR, XOR, SLT, SLL, SRL, SRA  
  - **I-type** → ADDI, ORI, ANDI, XORI, SLTI  
  - **Load/Store** → LW, LH, LB, SW, SH, SB  
  - **Branch** → BEQ, BNE  
  - **Jump** → JAL  
  - **U-type** → LUI, AUIPC  

---

## Architecture Overview

The processor follows a **single-cycle datapath**, where all stages of instruction execution are completed in one clock cycle.

### Instruction Execution Flow
1. **Fetch** → Instruction is fetched from memory using Program Counter (PC)  
2. **Decode** → Instruction fields are decoded and control signals generated  
3. **Execute** → ALU performs arithmetic/logic operations  
4. **Memory Access** → Load/store operations performed  
5. **Write Back** → Result written to register file  
6. **PC Update** → Next instruction address selected  

---

## Major Components

### 🔹 Program Counter (PC)
- Holds the address of the current instruction
- Updates every clock cycle (PC + 4 or branch target)

### 🔹 Instruction Memory
- Stores program instructions
- Outputs instruction based on PC

### 🔹 Register File
- 32 general-purpose registers
- Dual read and single write port

### 🔹 Control Unit
- Generates control signals based on opcode:
  - RegWrite, ALUSrc, MemRead, MemWrite, Branch, MemToReg, ALUOp

### 🔹 Immediate Generator
- Extracts and sign-extends immediate values for different instruction formats

### 🔹 ALU (Arithmetic Logic Unit)
- Performs operations such as:
  - ADD, SUB, AND, OR, XOR, SHIFT, SLT

### 🔹 ALU Control
- Decodes ALU operation using ALUOp, funct3, funct7

### 🔹 Data Memory
- Used for load/store instructions

### 🔹 Multiplexers (MUX)
- Select between:
  - Register vs Immediate (ALU input)
  - ALU result vs Memory data (write-back)
  - PC+4 vs Branch target

### 🔹 Branch Adder
- Computes branch target address

---
