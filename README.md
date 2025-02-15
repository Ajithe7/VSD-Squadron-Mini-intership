# TASK -1


# C and RISC Compiler Lab

## Objective
This lab aims to help you understand how to compile and run basic C programs using the GCC compiler and the RISC-V compiler, providing insight into how the RISC architecture works.

## C-Based Lab: Compiling C Code with GCC

### Step 1: Open Terminal and Open Leafpad on Ubuntu

First, open your terminal and use Leafpad to create a C file.

```
leafpad sum1to10.c &
```

### Step 2: Write a Simple C Program

In the opened Leafpad editor, write a simple C program to sum the numbers from 1 to 10. Here’s an example of such a program:

```c
#include <stdio.h>

int main() {
    int sum = 0;
    for (int i = 1; i <= 10; i++) {
        sum += i;
    }
    printf("Sum of numbers from 1 to 10: %d\n", sum);
    return 0;
}
```

### Step 3: Save the C Program

After writing the program, save the file as `sum1to10.c`.

### Step 4: Compile the C Program Using GCC

To compile the program using GCC, run the following command in your terminal:

```
gcc sum1to10.c
```

This command will generate an executable file named `a.out` by default.

### Step 5: Run the Program

To execute the compiled program and see the result, run the following command:

```
./a.out
```

You should see output similar to this:

``
Sum of numbers from 1 to 10: 55
``

## RISC-Based Lab: Compiling C Code with RISC-V Compiler

### Step 1: Display the C Code in Terminal

To view the C code in the terminal, use the `cat` command:

``
cat sum1to10.c
``

### Step 2: Compile Using the RISC-V Compiler

To compile the C code with the RISC-V GCC compiler, use the following command:

```
riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1to10.o sum1to10.c
```



### Step 3: Generate Assembly Code with Optimization

If you want to compile with higher optimization and generate the object file, use the following command:

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1to10.o sum1to10.c
```

### Step 4: View the Assembly Code

To view the disassembled assembly code, use the `objdump` tool with the following command:

```
riscv64-unknown-elf-objdump -d sum1to10.o | less
```

This will display the disassembled code. You can scroll through the output using `less`.

---


Here’s the content formatted for GitHub with proper syntax highlighting and structure:

---

### File: **oddoreven.c**

```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);

    if (num % 2 == 0) {
        printf("The number %d is even.\n", num);
    } else {
        printf("The number %d is odd.\n", num);
    }

    return 0;
}
```

---

### File: **README.md**

```markdown
# Odd or Even Program with RISC-V Verification

This repository contains a simple C program to check whether a number is odd or even. It also includes instructions to compile and verify the program for both the host system and the RISC-V architecture using Spike.

---

## Instructions

### Step 1: Compile Using GCC

Compile the program `oddoreven.c` using GCC for the host system:

```bash
gcc oddoreven.c -o oddoreven
```

Run the compiled program to verify its functionality:

```bash
./oddoreven
```

### Step 2: Compile Using RISC-V GCC

Compile the program for the RISC-V architecture using the `riscv64-unknown-elf-gcc` cross-compiler:

```bash
riscv64-unknown-elf-gcc -O2 -mabi=lp64 -march=rv64i -o oddoreven.o oddoreven.c
```

#### Flags Explanation:
- `-O2`: Optimize the code for performance.
- `-mabi=lp64`: Use the LP64 ABI for 64-bit pointers and integers.
- `-march=rv64i`: Target the RISC-V 64-bit integer base architecture.
- `-o oddoreven.o`: Specify the output file.

### Step 3: Run with Spike

Verify the RISC-V binary using Spike, the RISC-V simulator:

```bash
spike pk oddoreven.o
```

#### Spike Components:
- `spike`: The RISC-V simulator.
- `pk`: Proxy kernel for executing the program.
- `oddoreven.o`: The compiled RISC-V executable.

---

## Example Output

For example, if you input `4`, the program will output:

```bash
Enter a number: 4
The number 4 is even.
```

Similarly, inputting `5` will produce:

```bash
Enter a number: 5
The number 5 is odd.
```

---

## Repository Setup

To add the files and commit changes to the repository, follow these steps:

```bash
git add oddoreven.c README.md
git commit -m "Add oddoreven program and verification guide"
git push origin main
```

---

## Conclusion

This guide ensures you can compile and test a basic C program for both native and RISC-V environments. The steps demonstrate the integration of the RISC-V toolchain and Spike simulator to verify program functionality.

# TASK 2
## Odd or Even Program with RISC-V Verification





## C Program  

```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);

    if (num % 2 == 0) {
        printf("The number %d is even.\n", num);
    } else {
        printf("The number %d is odd.\n", num);
    }

    return 0;
}
```

---

## Instructions  

### Step 1: Compile Using GCC  

Use GCC to compile the program `oddoreven.c` for the host system:

```bash
gcc oddoreven.c -o oddoreven
```

Run the compiled program to verify its functionality:

```bash
./oddoreven
```

### Step 2: Compile Using RISC-V GCC  

To compile the program for the RISC-V architecture, use the following command:

```bash
riscv64-unknown-elf-gcc -O2 -mabi=lp64 -march=rv64i -o oddoreven.o oddoreven.c
```

#### Explanation of Flags:  
- `-O2` → Optimizes the code for better performance.  
- `-mabi=lp64` → Specifies the RISC-V 64-bit LP64 ABI (64-bit pointers and integers).  
- `-march=rv64i` → Targets the RISC-V 64-bit integer base architecture.  
- `-o oddoreven.o` → Defines the output file name.  

### Step 3: Run with Spike  

Run the compiled RISC-V binary using the Spike simulator:

```bash
spike pk oddoreven.o
```

#### Components Explanation:  
- `spike` → The RISC-V simulator.  
- `pk` → The proxy kernel for loading and executing the program.  
- `oddoreven.o` → The compiled RISC-V executable file.  

# Task 3  

## RISC-V ISA Set  

RISC-V instructions are divided into several types based on the format of their encoding. The main instruction types are:  

---

### 1. R-Type (Register-type)  

These instructions involve registers and typically use three registers. They are used for arithmetic operations, logic operations, and some others. The entire 32-bit instruction is divided into six fields.  

![Screenshot from 2025-02-15 13-12-30](https://github.com/user-attachments/assets/eb8e6005-572c-4879-b293-67a49c31010a)


- **[31:25] funct7** → Specifies additional control signals for the operation, often used to differentiate between instructions in combination with funct3.  
- **[24:20] rs2** → Source register 2 (second operand for the operation).  
- **[19:15] rs1** → Source register 1 (first operand for the operation).  
- **[14:12] funct3** → Specifies the operation to perform (e.g., add, subtract) in combination with opcode and funct7.  
- **[11:7] rd** → Destination register (where the result of the operation is stored).  
- **[6:0] opcode** → Specifies the instruction type (e.g., R-Type, I-Type).  

**Example Instructions:** `ADD, SUB, AND, OR, XOR`  

---

### 2. I-Type (Immediate-type)  

These instructions involve an immediate value (constant) and a source register used for arithmetic, logic, and memory operations.  
![Screenshot from 2025-02-15 13-15-09](https://github.com/user-attachments/assets/0eaa3039-a58c-4cc6-b6ef-4725dc19de6d)



 

- **[31:20] imm[11:0]** → Immediate value (constant) used as an operand in the instruction.  
- **[19:15] rs1** → Source register 1 (first operand).  
- **[14:12] funct3** → Specifies the operation in combination with the opcode.  
- **[11:7] rd** → Destination register (where the result is stored).  
- **[6:0] opcode** → Specifies the instruction type.  

**Example Instructions:** `ADDI, ANDI, LUI, JALR`  

---

### 3. S-Type (Store-type)  

These instructions are used for store operations that store data into memory from a register.  
![Screenshot from 2025-02-15 13-15-32](https://github.com/user-attachments/assets/343141bf-f650-4ade-8c2d-7ed9ca618afe)



- **[31:25] imm[11:5]** → Upper 7 bits of the immediate value.  
- **[24:20] rs2** → Source register 2 (data to store in memory).  
- **[19:15] rs1** → Base register for the memory address calculation.  
- **[14:12] funct3** → Specifies the operation (e.g., store byte or word).  
- **[11:7] imm[4:0]** → Lower 5 bits of the immediate value.  
- **[6:0] opcode** → Specifies the instruction type.  

**Example Instructions:** `SW, SH, SB`  

---

### 4. B-Type (Branch-type)  

These are branch operations used for conditional branching.  

![Screenshot from 2025-02-15 13-15-55](https://github.com/user-attachments/assets/f6187cc8-a97c-42e3-bfa7-e39d89b9c0ea)


- **[31] imm[12]** → Most significant bit of the immediate value.  
- **[30:25] imm[10:5]** → Bits 10 to 5 of the immediate value.  
- **[24:20] rs2** → Second source register (used for comparison).  
- **[19:15] rs1** → First source register (used for comparison).  
- **[14:12] funct3** → Specifies the branch condition (e.g., equal, not equal).  
- **[11:8] imm[4:1]** → Bits 4 to 1 of the immediate value.  
- **[7] imm[11]** → Bit 11 of the immediate value.  
- **[6:0] opcode** → Specifies the instruction type.  

**Example Instructions:** `BEQ, BNE, BLT, BGE`  

---

### 5. U-Type (Upper immediate-type)  

These instructions involve loading large immediate values into registers, typically used for the upper 20 bits of addresses.  

![Screenshot from 2025-02-15 13-16-16](https://github.com/user-attachments/assets/e46d947e-4814-4d15-b7b8-ae1f2d2789ff)


- **[31:12] imm[31:12]** → Immediate value (20 most significant bits) loaded into the upper bits of a register.  
- **[11:7] rd** → Destination register.  
- **[6:0] opcode** → Specifies the instruction type.  

**Example Instructions:** `LUI, AUIPC`  

---

### 6. J-Type (Jump-type)  

These instructions are used for unconditional jumps (typically for function calls and returns).  

![Screenshot from 2025-02-15 13-16-36](https://github.com/user-attachments/assets/0da49330-a9a0-487b-a055-94ecf397c190)


- **[31] imm[20]** → Most significant bit of the immediate value.  
- **[30:21] imm[10:1]** → Bits 10 to 1 of the immediate value.  
- **[20] imm[11]** → Bit 11 of the immediate value.  
- **[19:12] imm[19:12]** → Bits 19 to 12 of the immediate value.  
- **[11:7] rd** → Destination register (stores the return address after the jump).  
- **[6:0] opcode** → Specifies the instruction type.  

**Example Instructions:** `JAL, JALR`  

# **RISC-V Instruction Analysis**

This document provides a detailed breakdown of 15 unique RISC-V instructions extracted from `riscv-objdump` of `Factorial.o`. Each instruction is analyzed based on its type, encoding format, bit representation, and hexadecimal representation.

---

## **1. `lui a0, 0x2b`**
- **Instruction Type**: LUI (Load Upper Immediate)
- **Format**: `imm[31:12] | rd | opcode`
- **Breakdown**:
  - `imm[31:12] = 0x2b` (0000000000101011)
  - `rd = a0 (01010)`
  - `opcode = 0110111`
- **32-bit encoding**: `0000000000101011_01010_0110111`
- **Hexadecimal**: `0x0002B537`

---

## **2. `addi sp, sp, -48`**
- **Instruction Type**: I-Type (Immediate Arithmetic)
- **Format**: `imm[11:0] | rs1 | func3 | rd | opcode`
- **Breakdown**:
  - `imm[11:0] = -48` (`1111111111011000` in two's complement)
  - `rs1 = sp (00010)`
  - `rd = sp (00010)`
  - `func3 = 000`
  - `opcode = 0010011`
- **32-bit encoding**: `111111011000_00010_000_00010_0010011`
- **Hexadecimal**: `0xFD010113`

---

## **3. `sd ra, 40(sp)`**
- **Instruction Type**: S-Type (Store)
- **Format**: `imm[11:5] | rs2 | rs1 | func3 | imm[4:0] | opcode`
- **Breakdown**:
  - `imm[11:5] = 0000000`
  - `rs2 = ra (00001)`
  - `rs1 = sp (00010)`
  - `func3 = 011`
  - `imm[4:0] = 01000`
  - `opcode = 0100011`
- **32-bit encoding**: `0000000_00001_00010_011_01000_0100011`
- **Hexadecimal**: `0x02113423`

---

## **4. `jal ra, 104d8`**
- **Instruction Type**: J-Type (Jump)
- **Format**: `imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd | opcode`
- **Breakdown**:
  - `imm[20] = 0`
  - `imm[10:1] = 1000001000`
  - `imm[11] = 0`
  - `imm[19:12] = 00000000`
  - `rd = ra (00001)`
  - `opcode = 1101111`
- **32-bit encoding**: `0_1000001000_0_00000000_00001_1101111`
- **Hexadecimal**: `0x410000ef`

---

## **5. `lw s1, 12(sp)`**
- **Instruction Type**: I-Type (Load)
- **Format**: `imm[11:0] | rs1 | func3 | rd | opcode`
- **Breakdown**:
  - `imm[11:0] = 000000001100`
  - `rs1 = sp (00010)`
  - `rd = s1 (10001)`
  - `func3 = 010`
  - `opcode = 0000011`
- **32-bit encoding**: `000000001100_00010_010_01001_0000011`
- **Hexadecimal**: `0x00c12483`

---

## **6. `mv a5, s1`**
- **Instruction Type**: R-Type (Register Operation)
- **Format**: `funct7 | rs2 | rs1 | funct3 | rd | opcode`
- **Breakdown**:
  - `rs2 = zero (00000)`
  - `rs1 = s1 (10001)`
  - `rd = a5 (01111)`
  - `func3 = 000`
  - `funct7 = 0000000`
  - `opcode = 0010011`
- **Equivalent to**: `addi a5, s1, 0`
- **32-bit encoding**: `0000000_00000_01001_000_01111_0010011`
- **Hexadecimal**: `0x00048793`

---

## **7. `li a1, 1`**
- **Instruction Type**: I-Type (Immediate Load)
- **Format**: `imm[11:0] | rs1 | func3 | rd | opcode`
- **Breakdown**:
  - `imm[11:0] = 1 (000000000001)`
  - `rs1 = zero (00000)`
  - `rd = a1 (01101)`
  - `func3 = 000`
  - `opcode = 0010011`
- **32-bit encoding**: `000000000001_00000_000_01011_0010011`
- **Hexadecimal**: `0x00100593`


# TASK 4 - **Functional Simulation of RISC-V Core Using Verilog**  

### Open GTKWave for Functional Simulation  

Follow the steps below to clone the repository, simulate the RISC-V core, and open GTKWave for waveform analysis:  

1. **Clone the GitHub Repository:**  
   ```bash  
   git clone https://github.com/vinayrayapati/rv32i.git 
   ```  

2. **Navigate to the Project Directory:**  
   ```bash  
   cd rv32i  
   ```  

3. **Compile the Verilog Files:**  
   ```bash  
   iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v  
   ```  

4. **Run the Simulation:**  
   ```bash  
   ./iiitb_rv32i  

### Visualizing the Waveform in GTKWave  

Once the simulation generates the `.vcd` (Value Change Dump) file, follow these steps to visualize the waveform in GTKWave:  

1. **Run GTKWave with the Generated .vcd File:**  
   ```bash  
   gtkwave iiitb_rv321.vcd  
   ```  




