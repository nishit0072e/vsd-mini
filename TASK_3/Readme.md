
<summary><b>Task 3:</b> Identifying RISC-V Instruction Types</summary>

## WHAT IS RISC-V?
- RISC-V is an open-source instruction set architecture (ISA) that allows developers to create processors tailored for specific applications.
- RISC-V is based on reduced instruction set computer principles and is the fifth generation of processors built on this concept.
- RISC-V can also be understood as an alternative processor technology that is free and open-source, meaning you don't need to purchase a license to use it.

## INSTRUCTIONS FORMAT IN RISC-V
The instruction format of a processor dictates how machine language instructions are structured and organized for the processor to execute. Each instruction is composed of a series of 0s and 1s, with each segment containing information about the location and operation of data.  
There are six primary instruction formats in RISC-V:

1. R-format
2. I-format
3. S-format
4. B-format
5. U-format
6. J-format

#### RISCV Instruction Types

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instructions.png">
</p>

#### 1. R-type Instruction
In RV32, each instruction is 32 bits in size. R-type instructions perform operations on registers (not memory) and are used for various arithmetic and logical operations. The 32-bit instruction is divided into six fields:

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_r.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register where the result of the operation is stored.
- **func3** (3 bits): Specifies the type of operation performed.
- **rs1, rs2** (5 bits each): Source registers used in the operation.
- **func7** (7 bits): Further specifies the operation.

#### 2. I-type Instruction
I-type instructions involve operations that use both registers and an immediate value (not memory). These instructions are used for immediate and load operations. The instruction format is as follows:

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_i.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the result.
- **func3** (3 bits): Specifies the type of operation.
- **rs1** (5 bits): Source register.
- **imm[11:0]** (12 bits): A 12-bit signed immediate value used in the operation.

#### 3. S-type Instruction
S-type instructions are used for store operations where data is stored from a register to memory. The 32-bit instruction is divided as follows:

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_s.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[11:5]** (7 bits) and **imm[4:0]** (5 bits): The 12-bit immediate value is split across two fields, specifying the store offset.
- **rs1** (5 bits): The register containing the data to store.
- **rs2** (5 bits): The register containing the address where data should be stored.
- **func3** (3 bits): Specifies the type of store (byte, half-word, or word).

#### 4. B-type Instruction
B-type instructions are used for conditional branching based on comparisons. The 32-bit instruction format is as follows:

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_b.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[12]** (1 bit), **imm[10:5]** (6 bits), **imm[4:1]** (4 bits), and **imm[11]** (1 bit): These bits form the 12-bit signed immediate used for the branch offset.
- **rs1, rs2** (5 bits each): Source registers involved in the comparison.
- **func3** (3 bits): Defines the condition used for branching.

#### 5. U-type Instruction
U-type instructions are used to transfer an immediate value into the destination register. The format is simple and involves only two instructions: `LUI` and `AUIPC`.

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_u.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the immediate value.
- **imm[19:0]** (20 bits): The 20-bit immediate value that is transferred to the destination register.

For example, the instruction `lui x15, 0x13579` would load the value `0x13579000` into the upper 20 bits of register `x15`.

#### 6. J-type Instruction
J-type instructions are used for jump operations. These instructions are often used for loops and branching to a specified memory location. The format is as follows:

 <p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_j.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[20]** (1 bit), **imm[10:1]** (10 bits), **imm[11]** (1 bit), and **imm[19:12]** (8 bits): These bits form the 20-bit signed immediate for the jump address.
- **rd** (5 bits): The destination register (used for return addresses).

## Commands for Extracting RISC-V Instructions

<summary>Commands</summary>

#### Display the main function's disassembly, with 30 lines of context
```
riscv64-unknown-elf-objdump -d sum | grep -A 30 "<main>:"
```

#### Filter for arithmetic and logical instructions: add, sub, and, or
```
riscv64-unknown-elf-objdump -d sum | grep -E "add|sub|and|or"
```

#### Filter for immediate arithmetic, load, and jump instructions: addi, lw, jalr
```
riscv64-unknown-elf-objdump -d sum | grep -E "addi|lw|jalr"
```

#### Filter for store and branch instructions: sw, beq, bne, blt, bge
```
riscv64-unknown-elf-objdump -d sum | grep -E "sw|beq|bne|blt|bge"
```

#### Filter for control flow and address instructions: lui, auipc, jal
```
riscv64-unknown-elf-objdump -d sum | grep -E "lui|auipc|jal"
```

#### Count occurrences of each unique instruction
```
riscv64-unknown-elf-objdump -d sum | grep -o "\s\w\+\s" | sort | uniq -c
```


# Instructions with explaination
<summary>let's analyse each instruction one by one</summary>
	
# RISC-V Instructions Explanation

| Assembly Instruction | Type     | Description                                      | Fields                                                                 | 32-bit Instruction                  |
|----------------------|----------|--------------------------------------------------|------------------------------------------------------------------------|-------------------------------------|
| lui s1, 0xdead       | U-Type   | Loads the upper 20 bits of s1 with 0xdead.       | opcode: 0110111, rd: s1 = 01001, imm: 0xdead                           | 1101_1110_1010_1101_0100_1001_0110111 |
| auipc t1, 0x12345    | U-Type   | Adds 0x12345 to PC and stores result in t1.      | opcode: 0010111, rd: t1 = 00110, imm: 0x12345                          | 0001_0010_0011_0100_0101_00110_0010111 |
| andi a0, a1, 0xff    | I-Type   | ANDs a1 with 0xff and stores result in a0.       | opcode: 0010011, rd: a0 = 01010, rs1: a1 = 01011, func3: 111, imm: 0xff | 0000_1111_1111_01011_111_01010_0010011 |
| lbu t0, 2(a2)        | I-Type   | Loads an unsigned byte from a2+2 into t0.        | opcode: 0000011, rd: t0 = 00101, rs1: a2 = 01100, func3: 100, imm: 2   | 0000_0000_0010_01100_100_00101_0000011 |
| srli s3, s4, 4       | I-Type   | Shifts s4 right logically by 4, stores in s3.    | opcode: 0010011, rd: s3 = 01011, rs1: s4 = 01100, func3: 101, imm: 4   | 0000_0000_0100_01100_101_01011_0010011 |
| sh s5, 8(t2)         | S-Type   | Stores halfword from s5 to memory at t2+8.       | opcode: 0100011, rs1: t2 = 00111, rs2: s5 = 01101, func3: 001, imm: 8  | 0000_0000_0110_10011_001_01000_0100011 |
| sd s6, 16(a3)        | S-Type   | Stores doubleword from s6 to memory at a3+16.    | opcode: 0100011, rs1: a3 = 01101, rs2: s6 = 01110, func3: 011, imm: 16 | 0000_0001_0111_00110_011_10000_0100011 |
| bge t0, t1, 12       | B-Type   | Branches if t0 >= t1 to PC+12.                   | opcode: 1100011, rs1: t0 = 00101, rs2: t1 = 00110, func3: 101, imm: 12 | 0000_0000_0110_00101_101_01100_1100011 |
| bltu a4, a5, -8      | B-Type   | Branches if a4 < a5 (unsigned) to PC-8.          | opcode: 1100011, rs1: a4 = 01110, rs2: a5 = 01111, func3: 110, imm: -8 | 1111_1111_0111_10111_110_11000_1100011 |
| or t2, t3, t4        | R-Type   | ORs t3 and t4, stores result in t2.              | opcode: 0110011, rd: t2 = 00111, rs1: t3 = 01000, rs2: t4 = 01001, func3: 110, func7: 0000000 | 0000000_01001_01000_110_00111_0110011 |
| sra s7, s8, s9       | R-Type   | Shifts s8 right arithmetically by s9, stores in s7. | opcode: 0110011, rd: s7 = 01111, rs1: s8 = 10000, rs2: s9 = 10001, func3: 101, func7: 0100000 | 0100000_10001_10000_101_01111_0110011 |
| slti a7, t5, 0x7f    | I-Type   | Sets a7 to 1 if t5 < 0x7f, else 0.               | opcode: 0010011, rd: a7 = 01111, rs1: t5 = 00101, func3: 010, imm: 0x7f | 0000_0111_1111_00101_010_01111_0010011 |
| jalr t0, t1, 0       | I-Type   | Jumps to t1+0, stores return address in t0.      | opcode: 1100111, rd: t0 = 00101, rs1: t1 = 00110, func3: 000, imm: 0   | 0000_0000_0000_00110_000_00101_1100111 |
| div a1, a2, a3       | R-Type   | Divides a2 by a3, stores quotient in a1.         | opcode: 0110011, rd: a1 = 01011, rs1: a2 = 01100, rs2: a3 = 01101, func3: 100, func7: 0000001 | 0000001_01101_01100_100_01011_0110011 |
| rem a4, a5, a6       | R-Type   | Divides a5 by a6, stores remainder in a4.        | opcode: 0110011, rd: a4 = 01110, rs1: a5 = 01111, rs2: a6 = 10000, func3: 110, func7: 0000001 | 0000001_10000_01111_110_01110_0110011 |

### Notes
- **R-Type**: Register-to-register operations (e.g., `or`, `sra`, `div`, `rem`).
- **I-Type**: Immediate operations (e.g., `andi`, `lbu`, `srli`, `slti`, `jalr`).
- **S-Type**: Store instructions (e.g., `sh`, `sd`).
- **B-Type**: Branch instructions (e.g., `bge`, `bltu`).
- **U-Type**: Upper immediate instructions (e.g., `lui`, `auipc`).

# Example Application with it's instruction
<summary>C code for a application of 5-Bit Linear Feedback Shift Register</summary>

```c
#include <stdio.h>

unsigned int lfsr5(void) {
    static unsigned int state = 0x1F; // Initial seed: all 1s (5 bits) unsigned int bit;

    // Feedback: XOR of bit 4 (x^5) and bit 2 (x^3), polynomial x^5 + x^3 + 1
    bit = ((state >> 4) ^ (state >> 2)) & 1;
    state = (state << 1) | bit; // Shift left and insert feedback bit
    state &= 0x1F;              // Mask to keep only 5 bits

    return state;
}

int main() {
    int i;
    for (i = 0; i < 20; i++) {
        unsigned int value = lfsr5();
        printf("State %d: %u\n", i, value);
    }
    return 0;
}
```
<summary>Below is a table of 15 unique RISC-V assembly instructions extracted from a 5-bit LFSR C program compiled with `-O1` optimization and debugging information. These instructions represent a mix of R-type, I-type, S-type, B-type, and J-type operations</summary>



| Assembly Instruction   | Type     | Description                                           | Fields                                                                 | 32-bit Instruction                  |
|-----------------------|----------|-------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------|
| lui a5, %hi(state)    | U-Type   | Loads upper 20 bits of `state` address into `a5`.     | opcode: 0110111, rd: a5 = 01111, imm: %hi(state) (e.g., 0x0)           | 0000_0000_0000_0000_01111_0110111  |
| lw a0, %lo(state)(a5) | I-Type   | Loads 32-bit word from `a5 + offset` into `a0`.       | opcode: 0000011, rd: a0 = 01010, rs1: a5 = 01111, func3: 010, imm: 0   | 0000_0000_0000_01111_010_01010_0000011 |
| srli a4, a0, 4        | I-Type   | Shifts `a0` right logically by 4, stores in `a4`.     | opcode: 0010011, rd: a4 = 01110, rs1: a0 = 01010, func3: 101, imm: 4   | 0000_0000_0100_01010_101_01110_0010011 |
| xor a4, a4, a5        | R-Type   | XORs `a4` and `a5`, stores result in `a4`.            | opcode: 0110011, rd: a4 = 01110, rs1: a4 = 01110, rs2: a5 = 01111, func3: 100, func7: 0000000 | 0000000_01111_01110_100_01110_0110011 |
| andi a4, a4, 1        | I-Type   | ANDs `a4` with 1, stores result in `a4`.              | opcode: 0010011, rd: a4 = 01110, rs1: a4 = 01110, func3: 111, imm: 1   | 0000_0000_0001_01110_111_01110_0010011 |
| slli a0, a0, 1        | I-Type   | Shifts `a0` left logically by 1, stores in `a0`.      | opcode: 0010011, rd: a0 = 01010, rs1: a0 = 01010, func3: 001, imm: 1   | 0000_0000_0001_01010_001_01010_0010011 |
| or a0, a0, a4         | R-Type   | ORs `a0` and `a4`, stores result in `a0`.             | opcode: 0110011, rd: a0 = 01010, rs1: a0 = 01010, rs2: a4 = 01110, func3: 110, func7: 0000000 | 0000000_01110_01010_110_01010_0110011 |
| sw a0, %lo(state)(a5) | S-Type   | Stores 32-bit `a0` to memory at `a5 + offset`.        | opcode: 0100011, rs1: a5 = 01111, rs2: a0 = 01010, func3: 010, imm: 0  | 0000_0000_0101_00111_010_00000_0100011 |
| ret                   | I-Type   | Returns by jumping to `ra` (pseudo: jalr x0, x1, 0).  | opcode: 1100111, rd: x0 = 00000, rs1: x1 = 00001, func3: 000, imm: 0   | 0000_0000_0000_00001_000_00000_1100111 |
| addi sp, sp, -16      | I-Type   | Subtracts 16 from `sp` to allocate stack space.       | opcode: 0010011, rd: sp = 00010, rs1: sp = 00010, func3: 000, imm: -16 | 1111_1111_0000_00010_000_00010_0010011 |
| sd ra, 8(sp)          | S-Type   | Stores 64-bit `ra` to memory at `sp + 8`.             | opcode: 0100011, rs1: sp = 00010, rs2: ra = 00001, func3: 011, imm: 8  | 0000_0000_0001_00010_011_01000_0100011 |
| li a0, 0              | I-Type   | Loads 0 into `a0` (pseudo: addi a0, x0, 0).           | opcode: 0010011, rd: a0 = 01010, rs1: x0 = 00000, func3: 000, imm: 0   | 0000_0000_0000_00000_000_01010_0010011 |
| bge a0, a1, end       | B-Type   | Branches to `end` if `a0` >= `a1`.                    | opcode: 1100011, rs1: a0 = 01010, rs2: a1 = 01011, func3: 101, imm: 8 (example offset) | 0000_0000_0101_10101_101_01000_1100011 |
| jal ra, lfsr5         | J-Type   | Jumps to `lfsr5`, stores return address in `ra`.      | opcode: 1101111, rd: ra = 00001, imm: offset (e.g., 0x4)               | 0000_0000_0100_0000_00001_1101111  |
| mv a2, a0             | R-Type   | Copies `a0` to `a2` (pseudo: or a2, a0, x0).          | opcode: 0110011, rd: a2 = 01100, rs1: a0 = 01010, rs2: x0 = 00000, func3: 110, func7: 0000000 | 0000000_00000_01010_110_01100_0110011 |


