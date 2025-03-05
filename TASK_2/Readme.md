

<summary><b>Task 2:</b> Using Spike Simulation and Interactive Debugging Mode to Debugg the C code during Spike</summary> 

### What is SPIKE in RISCV?
> * Spike, also known as "riscv-isa-sim", is the official RISC-V Instruction Set Architecture (ISA) simulator. It serves as a reference model for RISC-V software development and debugging.    
  
### What is pk (Proxy Kernel)?  
> * The Proxy Kernel (PK) is a lightweight bootloader and runtime environment that provides system call support for running user-space applications on RISC-V simulators (like Spike) and hardware. 
> * A Proxy Kernel in the RISC-V ecosystem simplifies the interaction between complex hardware and the software running on it, making it easier to manage, test, and develop software and hardware projects.  

### Testing the SPIKE Simulator  
The target is to run the ```sum1ton.c``` code using both ```gcc compiler``` and ```riscv compiler```, and both of the compiler must display the same output on the terminal. So to compile the code using **gcc compiler**, use the following command:  
```
gcc sum1ton.c -o sum1ton.o
./sum1ton.o
```
And to compile the code using **riscv compiler**, use the following command:  
```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
To see the spike simulator output, use this command:
```
spike pk sum1ton.o
```
#### Spike Simulation:
 <p align="center">
  <img width="800" height="500" src="https://github.com/nishit0072e/vsd-mini/blob/main/images/spike_simulator.png">
</p>

#### Following are the snapshots of RISCV Objdump with **-O1** and **-Ofast** options  
 
#### Objdump in -O1:

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
 * Open the **Objdump** of code by using the following command  
```
riscv64-unknown-elf-objdump -d sum1ton.o | less  
```
 <p align="center">
  <img width="800" height="500" src="https://github.com/nishit0072e/vsd-mini/blob/main/images/o1_objdump.png">
</p>
  
#### Objdump in -Ofast:

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
 
 <p align="center">
  <img width="800" height="500" src="https://github.com/nishit0072e/vsd-mini/blob/main/images/ofast_objdump.png">
</p>

#### Debugging the Assembly Language Program of  ```sum.c```  

* Open the debugger in another terminal by using the following command  
```
spike -d pk sum.o
```
* The debugger will be opened in the terminal. Now, debugging operations can be performed as shown in the following snapshot.

#### Debugging:
 <p align="center">
  <img width="800" height="500" src="https://github.com/nishit0072e/vsd-mini/blob/main/images/debugger.png">
</p>

