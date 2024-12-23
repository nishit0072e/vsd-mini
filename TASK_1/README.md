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
### Write a C code to do the sum of n numbers
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
