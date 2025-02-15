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
```


