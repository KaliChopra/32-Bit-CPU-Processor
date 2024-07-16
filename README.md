**32 Bit MIPS32 PROCESSOR**
Skills: Verilog HDL, Computer Architecture
•	I am Kali Chopra pursuing Electronics Engineering at IIT (BHU), Varanasi.
•	I have made a 16-bit CPU using Verilog HDL.
•	The verilog files along with testbench are attached in this repository.
•	The block diagram of design is as follows:

[![Screenshot-2024-07-16-181550.png](https://i.postimg.cc/G3KF7BGS/Screenshot-2024-07-16-181550.png)](https://postimg.cc/t71n74rh)

**CPU Design**
 ![2](https://www.imghippo.com/i/PQjG61721133978.png)
**Implementation of MIPS32 architecture** 
•	MIPS32 architecture includes the following types of registers: 
o	MIPS32 has a set of 32 general-purpose registers.  Each register is of 32 bits.  
o	Register R0 always contains the constant value 0.
•	The PC is a special-purpose 32-bit register.
•	MIPS32 does not have flag registers (such as zero, carry, sign flags)
Instruction Code
There are 2 types of instruction codes:
1.	R-Type (Register): The instruction bits are divided into 6 parts out of which we are not using 2 of them that is shift amount and opcode extension.
 ![3](https://www.imghippo.com/i/yf0UW1721134145.png)

I.	1st 5 bits represent the opcode for the instruction:
o	The opcodes description is as follows:
![4](https://www.imghippo.com/i/JIQi71721134333.png)
 

II.	The next 10 bits represent the Address of the memory that is needed in the instruction.
2.	I-Type (Immediate): The instruction bits are divided into 6 parts.
![5](https://www.imghippo.com/i/GGMHG1721134393.png) 
III.	1st 5 bits represent the opcode for the instruction:
o	The opcodes description is as follows:
![6](https://www.imghippo.com/i/HyVj81721134454.png)
 
MIPS32 Instruction Cycle
We divide the instruction execution cycle into five steps:

(a) IF: Instruction Fetch
•	Here the instruction pointed to by PC is fetched from memory, and also the next value of PC is computed.
•	For a branch instruction, new value of the PC may be the target address. So PC is not updated in this stage; new value is stored in a register NPC.

(b) ID : Instruction Decode
•	The instruction already fetched in IR is decoded.
•	Decoding is done in parallel with reading the register operands rs and rt. Possible because these fields are in a fixed location in the instruction format.
•	In a similar way, the immediate data are sign-extended.

(c) EX: Execution / Effective Address Computation
•	In this step, the ALU is used to perform some calculation.
•	The exact operation depends on the instruction that is already decoded.
•	 The ALU processes operands that have been prepared in the previous cycle (A, B, Imm, etc).


(d) MEM: Memory Access / Branch Completion
•	The only instructions that make use of this step are loads, stores, and branches.
•	The load and store instructions access the memory.
•	The branch instruction updates PC depending upon the outcome of the branch condition.

(e) WB: Register Write Back
•	In this step, the result is written back into the register file.
•	Result may come from the ALU or memory system (viz. a LOAD instruction).
•	The position of the destination register in the instruction word depends on the instruction already known after decoding has been done.

Input and Output
•	The Instructions are given in the file Program.txt and the Data is given in the file Data.txt. As soon as we run the CPU_tb.v file the instructions and data are loaded into their respective segments of memory.
•	The output is written in the file Memory_output.txt.



