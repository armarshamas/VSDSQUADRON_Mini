## Task 1: Tools Installations

Install RISC-V GNU Toolchain 

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/23158c82-c463-440f-9260-cc34f4fb5b1c)

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/90f3978e-38ff-4dec-984f-3086b0e3914c)


install Yosys, iverilog, gtkwave

**Yosys**

$ git clone https://github.com/YosysHQ/yosys.git

$ cd yosys

$ sudo apt install make (If make is not installed please install it) 

$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev

$ make config-gcc

$ make 

$ sudo make install

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/a4c6dc0a-1e3b-41c0-b4f1-69a30904f848)

**iverilog:**
sudo apt-get install iverilog

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/0bc2b5bd-a124-4416-bd97-86a692300c78)

**gtkwave:**

sudo apt update

sudo apt install gtkwave

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/8deb50fc-2602-47cd-a561-23c87864102f)

## Task 2: RISC V ISA Identify instruction type and exact 32-bit instruction code in the instruction type format

## R-type Instructions
R-type instructions are used for register-to-register operations, such as arithmetic and logical  operations. 

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/48140c5b-fd00-4463-b43e-c48eb1b517ba)

They have the following format:

```
31 25 24 20 19 15 14 12 11 7 6 0
funct7 rs2 rs1 funct3 rd opcode
```

- `funct7`: This 7-bit field specifies the exact operation to be performed, such as addition, subtraction, or bitwise operations.
- `rs2`, `rs1`: These 5-bit fields specify the source registers for the operation.
- `funct3`: This 3-bit field further qualifies the operation, such as the type of comparison for a branch instruction.
- `rd`: This 5-bit field specifies the destination register for the result of the operation.
- `opcode`: This 7-bit field identifies the instruction as an R-type operation.

Examples of R-type instructions include `add`, `sub`, `and`, `or`, `xor`, and `sll` (shift left logical).

## I-type Instructions
I-type instructions are used for immediate and load operations. 

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/8fce06bb-89b4-4510-99ca-9272032e77a3)


 They have the following format:

```
31 20 19 15 14 12 11 7 6 0
imm[11:0] rs1 funct3 rd opcode
```

- `imm[11:0]`: This 12-bit field contains a signed immediate value, which is used in operations like addition with an immediate operand or loading a value from memory.
- `rs1`: This 5-bit field specifies the source register for the operation.
- `funct3`: This 3-bit field further qualifies the operation, such as the type of load or arithmetic operation.
- `rd`: This 5-bit field specifies the destination register for the result of the operation.
- `opcode`: This 7-bit field identifies the instruction as an I-type operation.

Examples of I-type instructions include `addi`, `lw` (load word), and `jalr` (jump and link register).

## S-type Instructions
S-type instructions are used for store operations, where a value is stored from a register to memory. 

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/aab84bf9-5c1d-42af-a7dd-86338c6362d0)


 They have the following format:

```
31 25 24 20 19 15 14 12 11 7 6 0
imm[11:5] rs2 rs1 funct3 imm[4:0] opcode
```

- `imm[11:5]`, `imm[4:0]`: These two 5-bit fields combine to form a 12-bit signed offset used in the store operation.
- `rs2`: This 5-bit field specifies the source register for the value to be stored.
- `rs1`: This 5-bit field specifies the base register for the memory address.
- `funct3`: This 3-bit field specifies the type of store operation, such as `sb` (store byte) or `sw` (store word).
- `opcode`: This 7-bit field identifies the instruction as an S-type operation.

The most common S-type instruction is `sw` (store word), which stores the contents of a register to memory at the address specified by the base register plus the 12-bit signed offset.

## B-type Instructions
B-type instructions are used for conditional branch operations. 

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/b2de36ab-b068-4354-a65f-cd8c5c0e5fcd)

 
They have the following format:

```
31 31 25 24 20 19 15 14 12 11 7 6 0
imm[12] imm[10:5] rs2 rs1 funct3 imm[4:1] imm[11] opcode
```

- `imm`, `imm[10:5]`, `imm[4:1]`, `imm`: These fields combine to form a 13-bit signed PC-relative offset used in the branch operation.
- `rs2`, `rs1`: These 5-bit fields specify the source registers for the comparison.
- `funct3`: This 3-bit field specifies the type of branch condition, such as `beq` (branch if equal) or `bne` (branch if not equal).
- `opcode`: This 7-bit field identifies the instruction as a B-type operation.

The B-type instructions allow for conditional jumps based on the comparison of two register values, enabling control flow in RISC-V programs.

These four instruction formats (R, I, S, and B) cover the majority of the RISC-V instruction set, providing a simple and efficient way to encode a wide range of operations. The RISC-V ISA also includes additional formats, such as U-type and J-type, for other types of instructions like jumps and 20-bit immediate loads.

The key design principles of the RISC-V ISA are simplicity, regularity, and extensibility. By keeping the instruction set small and uniform, RISC-V makes it easier to implement efficient hardware and software for a wide range of applications. The modular nature of the ISA also allows for custom extensions to be added as needed, enabling RISC-V to be tailored to specific use cases.

## Task 3: RISC Simulation

## Simple C code implementation:

![Screenshot from 2024-04-29 23-02-09](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/e86e8598-6778-42d7-b7f5-b7a30e0ea8c5)

## RISC V Object

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/5fb8df39-fe65-4408-8606-f6c6094370c2)

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/c0bd8d16-c119-4a04-bb5b-cb84dbec5159)

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/3b4d7ebc-8dac-46e6-8b25-16287fca83df)

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/7959f975-b493-4a8f-9f73-4284bf9f640f)

## Task 4: SPIKE Simulation and observation with -O1 and -Ofast
# Spike installation

```
$ git clone https://github.com/riscv/riscv-isa-sim.git      
$ cd riscv-isa-sim    
$ mkdir build  
$ cd build  
$ ../configure --prefix=/opt/riscv
$ sudo apt-get install device-tree-compiler
$ make  
$ sudo apt update  
$ sudo apt install g++-8  
$ make CXX=g++-8  
$ sudo make install  
$ echo 'export PATH=$PATH:/opt/riscv/bin' >> ~/.bashrc  
$ source ~/.bashrc
```

# pk installation

```
$ git clone https://github.com/riscv/riscv-pk.git    
$ cd riscv-pk    
$ mkdir build    
$ cd build      
$ ../configure --prefix=/home/vsduser/riscv --host=riscv64-unknown-elf --with-arch=rv64gc    
$ make    
$ sudo make install
```

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/d86f205d-f873-4315-94f6-04bc059f24a8)

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/14f8517b-6195-42e0-a9ac-a8cdd1564d03)

## Task 5 : Use this RISC-V Core Verilog netlist and testbench for functional simulation experiment

IR - 32 bit Instruction
RD - Destination Register
A & B - Source Registers
ALUOUT - Output

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/b437c3e3-6a6f-4e08-b051-5a7392e20b05)


# Instruction 1: ADD R6, R2, R1

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/0147e6f4-81c9-4de5-aed0-32fa8b60e967)


# Instruction 2: SUB R7, R1, R2

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/68b930bd-e914-445b-b6ea-f9b63ec68d0c)


# Instruction 3: AND R8, R1, R3

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/5b1735c2-052d-4926-a93e-788db0a6e32a)


# Instruction 4: OR R9, R2, R5

# Instruction 5: XOR R10, R1, R4

# Instruction 6: SLT R1, R2, R4

# Instruction 7: ADDI R12, R4, 5

Instruction 8: BEQ R0, R0, 15

