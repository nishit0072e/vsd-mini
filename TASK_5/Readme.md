
<summary><b>Task 5:</b> Implementation of any circuit utilizing VSDSquadron Mini and verify that the RISCV processor's C program file upload and construction are successful</summary> 

# Overview

A **4-bit Linear Feedback Shift Register (LFSR)** is a type of pseudo-random number generator that shifts bits and applies a feedback function to generate a sequence of states before repeating. It is widely used in cryptography, error detection, and digital circuits.

### **How It Works:**
1. **Registers & Initialization**:  
   - The LFSR consists of a 4-bit shift register initialized with a nonzero seed.
   
2. **Feedback Polynomial**:  
   - A feedback function is applied using XOR operations on specific bits (taps).  
   - The common polynomial used:  
     ```
     x^4 + x^3 + 1
     ```
     This means we XOR the 4th and 3rd bits to get the new bit.

3. **Shifting**:  
   - The LFSR shifts left by one bit each cycle, with the feedback bit inserted at the LSB.

4. **Output**:  
   - The register value represents the output at each step.

### **LFSR Diagram:**
![LFSR Diagram](https://github.com/nishit0072e/vsd-mini/blob/main/images/lfsr.png)
### **Example Sequence (starting with 0b1011):**

| Step | LFSR Value | Output |
|------|-----------|--------|
| 1    | 1011      | 11 (decimal) |
| 2    | 0111      | 7  |
| 3    | 1110      | 14 |
| 4    | 1101      | 13 |
| 5    | 1001      | 9  |
| ...  | ...       | ... |

The sequence cycles through 15 unique values (excluding all zeros).

## Components Required
- CH32V003 RISC-V Processor
- Breadboard
- Power Supply
- Jumper Wires

## System Specifications
### CH32V003 RISC-V Processor
- Voltage: 1.8V to 3.6V
- GPIO Pins: Configurable for interfacing with external devices

## Circuit Connections
<p align="center">
  <img width="500" src="https://github.com/nishit0072e/vsd-mini/blob/main/images/circuit_image.png">
</p>

### Connections:
1. **RED Led**: Connect to `PC3` of CH32V003.
2. **GREEN Led**: Connect to `PC4` of CH32V003.
3. **BLUE Led**: Connect to `PC5` of CH32V003.
4. **WHITE Led**: Connect to `PC6` of CH32V003.
5. **GND**: Connect to `GND` of CH32V003

### Pinout Diagram:

| Component          | CH32V003x Pin |
|--------------------|---------------|
| RED Led            | PC3           |
| GREEN Led          | PC4           |
| BLUE Led           | PC5           |
| WHITE Led          | PC6           |
| GND                | GND           |
