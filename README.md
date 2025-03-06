# VSDSquadron Mini Research Internship
This Repository solely made for the Research Internship using VSDSquadron Mini RISC-V Development Board 
# Overview of VSDSquadron Mini Board

The **VSDSquadron Mini** is a compact, low-cost RISC-V development board based on the **CH32V003F4U6** microcontroller. It is designed for embedded systems, IoT applications, and educational purposes, offering a balance of performance and efficiency in a small footprint.

<p align="center">
  <img src="https://github.com/nishit0072e/vsd-mini/blob/main/images/board.png" alt="VSDSquadron Mini" width="600">
</p>


## Hardware Specifications  

# VSDSquadron Mini

| **Name**               | **VSDSquadron Mini** |
|------------------------|----------------------|
| **Board**             | **SKU**: VSDSQM |
| **Microcontroller**   | CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set |
| **USB Connector**     | USB 2.0 Type-C |

## Pins

| Feature               | Details |
|----------------------|---------|
| **Built-in LED Pin** | 1x onboard user LED (PD6) |
| **Digital I/O Pins** | 15 |
| **Analog I/O Pins**  | 10-bit ADC, PD0-PD7, PA1, PA2, PC4 |
| **PWM Pins**         | 14X |
| **External Interrupts** | 8 external interrupt edge detectors, but it only maps one external interrupt to 18 I/O ports |

## Communication

| Interface | Pins |
|-----------|------|
| **USART** | 1x, PD6 (RX), PD5 (TX) |
| **I2C**   | 1x, PC1 (SDA), PC2 (SCL) |
| **SPI**   | 1x, PC5 (SCK), PC1 (NSS), PC6 (MOSI), PC7 (MISO) |

## Programming & Debugging

| Feature | Description |
|---------|------------|
| **Programmer/Debugger** | Onboard RISC-V programmer/debugger, USB to TTL serial port support |

## Power

| Feature                   | Value |
|---------------------------|-------|
| **I/O Voltage**           | [3.3 V](https://en.wikipedia.org/wiki/3.3V) |
| **Input Voltage (Nominal)** | 5 V |
| **Source Current per I/O Pin** | 8 mA |
| **Sink Current per I/O Pin**   | 8 mA |

## Clock Speed & Memory

| Feature   | Details |
|-----------|---------|
| **Processor Clock Speed** | 24 MHz |
| **SRAM**   | 2 KB on-chip volatile SRAM |
| **Flash Memory** | 16 KB external program memory |


## 🚀 Getting Started  

To start working with the VSDSquadron Mini board [click here](https://www.vlsisystemdesign.com/wp-content/uploads/2024/01/VSDSQMinidatasheet.pdf)

This board is a great choice for learning RISC-V, developing compact embedded projects, and experimenting with low-cost microcontrollers.

---

## [TASK 1](https://github.com/nishit0072e/vsd-mini/tree/main/TASK_1) ✅
> ***NOTE:** Getting hands dirty in the GCC & RISC-V compilers along with C Programming*
## [TASK 2](https://github.com/nishit0072e/vsd-mini/tree/main/TASK_2) ✅
> ***NOTE:** Using Spike Simulation and Interactive Debugging Mode to Debug the C code during Spike*
## [TASK 3](https://github.com/nishit0072e/vsd-mini/tree/main/TASK_3) ✅
> ***NOTE:** Identifying RISC-V Instruction Types*
## [TASK 4](https://github.com/nishit0072e/vsd-mini/tree/main/TASK_4) ✅
> ***NOTE:** Functional Simulation of RISC-V Core Using Verilog*
## [TASK 5](https://github.com/nishit0072e/vsd-mini/tree/main/TASK_5) ✅
> ***NOTE:** Implementation of any circuit utilizing VSDSquadron Mini and verify that the RISCV processor's C program*
