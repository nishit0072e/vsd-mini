# TASK 1
## Environment Setup
### Setup
1. Download the Ubuntu Virtual Harddisk from the given link [![Download VDI](https://img.shields.io/badge/Click_here-Download-orange)](https://forgefunder.com/~kunal/riscv_workshop.vdi)
  - make sure your drive has minimun atleast 100Gb space.
2. Download and install Oracle VirtualBox on your computer
3. Launch VirtualBox and click on the "New" button to create a new virtual machine. 
  - Select OS Type-Linux 
  - SubType-Ubuntu
  - Version-18.04 Bionic Beaver(64-bit) 
  - RAM-4GB
  - Processor Core-2 (atleast)
  - existing hard disk file- Downloaded VDI file
4. Start your vitual machine.
## Testing the RISC-V toolchain
### Write a C code to do the sum of n numbers and compile it using gcc compiler
```
#include <stdio.h>
int main(){
	int n, i, sum = 0;
	printf("Enter a positive integer: ");
	scanf("%d", &n);
	for(i=1;i<=n;++i){
		sum += i;
	}
	printf("sum = %d",sum);
	return 0;
}
```
- Use the basic commands of linux to check the curent working directory, to list the files
- Use Vi editor to write the code 
- Use gcc compiler to compile the c code 
- Run the program using ./a.out

### Compile the code using RISC-V toolchain
- Use the command
```
riscv64-unknown-elf-gcc -o sumof1ton sumof1ton.c
```
[image]
- now open a new terminal & use the command to see the disassembled asembly code 
```
riscv64-unknown-elf-objdump -d sum1ton.o
```
[image]
- now use this command to pipe the output in less page
```
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
- Use the first command when the output is short and manageable.
- Use the second command when the output is lengthy, as less allows for easier navigation and searching.

### Difference between two compiling commands
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
- -O1: For early development, debugging, or when you prioritize predictable behavior.
- -Ofast: For production builds of performance-critical applications where speed is the top priority, and minor deviations in numerical results are acceptable.

## Comparison Table

| Feature                     | `-O1`                          | `-Ofast`                           |
|-----------------------------|----------------------------------|-------------------------------------|
| **Optimization Level**      | Basic                          | Aggressive                         |
| **Floating-Point Compliance** | Standards-compliant            | May violate standards (e.g., `-ffast-math`) |
| **Compilation Time**        | Relatively short               | Longer                             |
| **Execution Speed**         | Moderate improvements          | Maximum speed possible             |
| **Debugging Ease**          | Easier                         | Harder due to aggressive transformations |
