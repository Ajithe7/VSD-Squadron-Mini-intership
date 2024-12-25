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
