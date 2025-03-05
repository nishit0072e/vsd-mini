
<summary><b>Task 4:</b> Functional Simulation of RISC-V Core Using Verilog</summary>  
<br>

# Objective:  

1. Perform functional simulation using the pre-built RISC-V core Verilog source code and testbench.  
2. Execute specified commands to test various functionalities of the core.  
3. Capture waveform snapshots showcasing the simulation results.  
4. Upload the waveform snapshots and observations to the GitHub repository for documentation and reference.

### Steps to perform functional simulation of RISCV 
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
   ```
   
![s18](https://github.com/nishit0072e/vsd-mini/blob/main/images/rv_core_simul.png)

### Visualizing the Waveform in GTKWave  

Once the simulation generates the `.vcd` (Value Change Dump) file, follow these steps to visualize the waveform in GTKWave:  

1. **Run GTKWave with the Generated .vcd File:**  
   ```bash  
   gtkwave iiitb_rv32i.vcd  
   ```  

![s19](https://github.com/nishit0072e/vsd-mini/blob/main/images/alu_out.png)

This Instructions are Hardcoded in the [iiitb_rv32i](https://github.com/vinayrayapati/rv32i/) file

|  **Operation**  |  **Standard RISCV ISA**  |  **Hardcoded ISA**  |  
|  :----:  |  :----:  |  :----:  |  
|  ADD R6, R2, R1  |  32'h00110333  |  32'h02208300  |  
|  SUB R7, R1, R2  |  32'h402083b3  |  32'h02209380  |  
|  AND R8, R1, R3  |  32'h0030f433  |  32'h0230a400  |  
|  OR R9, R2, R5  |  32'h005164b3  |  32'h02513480  |  
|  XOR R10, R1, R4  |  32'h0040c533  |  32'h0240c500  |  
|  SLT R1, R2, R4  |  32'h0045a0b3  |  32'h02415580  |  
|  ADDI R12, R4, 5  |  32'h004120b3  |  32'h00520600  |  
|  BEQ R0, R0, 15  |  32'h00000f63  |  32'h00f00002  |  
|  SW R3, R1, 2  |  32'h0030a123  |  32'h00209181  |

Above instructions are highlighted below
![s20](https://github.com/nishit0072e/vsd-mini/blob/main/images/instruction_seg.png)
