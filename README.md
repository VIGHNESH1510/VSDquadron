# TASK 1
## INSTALLATION OF LEAFPAD

  ![Screenshot (246)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/1a8e93c0-b6fa-4997-b354-19470a26b43e)


## TO WRITE A C CODE TO FIND THE SUM OF N NUMBERS
   + open the ubunto terminal.
   + type the command **leafpad filename.c &** to open the leafpad.
   + write the c code to find the sum of N numbers.
   + for compiling, use the command **gcc filename.c** and the output can be displayed using the command **./a.out**.
     
     ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/0d0b9cb8-f300-41ac-8e4f-1569828e57d0)

     
## CONVERSION OF C CODE TO INSTRUCTION SET
   + to create a  O file use the command **riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c**
   + and then type **ls -ltr sum1ton.o**
   + we can the see the instruction set using the command **risc64-unknown-elf-objdump -d sum1ton.o**

     ![Screenshot (255)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/f56cca63-b262-433b-aba4-7b895487db30)

     when we replace the **-O1** with **Ofast** we can observe that the number of instructions set will be reduced.

     ![Screenshot (258)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/36a73ba3-18ba-45d1-a039-6427b900744b)
     __________

# TASK 2
## To write a C Program for Clock Divider Circuit And Compile it to RISC File
A Clock Divider Circuit is used to divide the operating frequency of the clock based on the Division Factor In relative to the Master Clock.
## The below image is the C Program for the Clock Divider Circuit along with its output value,

![WhatsApp Image 2024-06-25 at 16 39 08_c085d847](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/7b939c39-26a9-4b0a-8612-7d52c6d6e2f8)

## The Assembly code for the Clock Divider Circuit,

![WhatsApp Image 2024-06-25 at 16 39 06_1e5f4607](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/2d3b5771-8c12-4315-b58f-0d4518d3b0a9)

## The Reduced Assembly Code for the Clock Divider Circuit,

![WhatsApp Image 2024-06-25 at 16 39 06_f0126ef9](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/6d6327ca-4a32-448a-bc8c-7efff0dff4ae)
________

## TASK 3
## COMPILATION OF THE CODE  IN RISC COMPILER USING SPIKE
   + To compile the C code for clock Divider in risc using the **spike**, we use the commands

     ``` js
         riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o clockdivider.o clockdivider.c
         spike pk clockdivider.o
     ```
     
  + we may verify the output of the risc compiler with the output of the C code
    
![Screenshot 2024-06-27 142805](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/0992ced2-0868-4bfe-a9c5-2d39dd365671)

+ To debug the Assembly code we use the command

``` js
    spike -d pk clockdivider.o
    until pc 0 100b0
```

+ To read the contents in instruction 

  ``` js
      reg 0 a0
  ```
![Screenshot 2024-06-27 123634](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/dd01ae40-fea6-45c3-be07-5911332ccc85)

  ______

# TASK 4
  ## RISC-V INSTRUCTION TYPES
  RISC-V instructions are categorized into several types based on their format and the nature of operations they perform. The primary instruction types in RISC-V include R-type, I-type, S-type, B-type, U-type, and J-type. Each type has a specific format and serves different purposes within the architecture.

  ## R-TYPE
   R-type instructions are used for arithmetic and logical operations that involve only registers. These instructions typically include operations such as addition,             subtraction, logical AND, logical OR, and shift operations. The general format of an R-type instruction in RISC-V is as follows:
   
   

   ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/f1acf85d-2688-4882-b0e0-2d507debb3c5)
   


  |FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |Specifies the operation category |
  |**rd**| 5 bits |The destination register where the result of the operation is stored |
  |**funct3**| 3 bits |Further specifies the operation within the category defined by the opcode |
  |**rs1**| 5 bits |The first source register operand |
  |**rs2**| 5 bits |The second source register operand|
  |**funct7**| 7 bits |Provides additional information to specify the exact operation, often used to differentiate between similar operations |



## I-TYPE
 I-Type instructions in RISC-V are used for operations that involve an immediate value. These instructions typically include arithmetic operations with an immediate, load instructions, and other operations such as accessing Control and Status Registers (CSR).The upper 12 bits of I-type is an immediate number. The opcode is different from other instruction formats because the corresponding specific operations are different, and other parts are very similar to R-type.

 ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/72144b82-d0ff-4f2a-99bc-5a2a5267cda1)


|FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |Specifies the operation category |
  |**rd**| 5 bits |The destination register where the result of the operation is stored |
  |**funct3**| 3 bits |Further specifies the operation within the category defined by the opcode |
  |**rs1**| 5 bits |The first source register operand |
  |**imm[11:0]**| 12 bits |The immediate value, which can be a signed number used in the operation.|


  ## S-TYPE
  S-Type instructions in RISC-V are used for store operations where data from a register is stored to memory.The characteristic of S-type instruction is that there is no rd register. In this type of instruction, the immediate is divided into two parts, the first part is in bit11-5, and the second part is in bit4-0.

  ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/3a73c952-de5d-42d5-b967-574914560c74)


  |FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |Specifies the operation category |
  |**imm[4:0]**| 5 bits |The lower 5 bits of the immediate value. |
  |**funct3**| 3 bits |Further specifies the operation within the category defined by the opcode |
  |**rs1**| 5 bits |The first source register operand |
  |**rs2**| 5 bits |The second source register operand |
  |**imm[11:5]**| The upper 7 bits of the immediate value.|




  ## B-TYPE
  B-Type instructions are used for conditional branch operations. These instructions enable conditional jumps to different parts of the code based on the comparison of two registers. The format of a B-Type instruction is as follows:

  ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/69f6b0e7-e7cc-401e-864a-17c62c4a4783)


  
 |FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |Specifies the primary operation category, which is 1100011 for all branch instructions. |
  |**imm[4:1]**| 5 bits | The lower part of the immediate value, with bit 11 positioned at the least significant bit in the upper half.|
  |**funct3**| 3 bits |Specifies the type of comparison. |
  |**rs1**| 5 bits |The first source register for the comparison. |
  |**rs2**| 5 bits | The second source register for the comparison.|
  |**imm[10:5]**| 7 bits |The upper part of the immediate value. |









## U-TYPE
U-Type instructions in RISC-V are used for instructions that require a large immediate value, typically for loading upper immediate values into a register or for performing arithmetic on addresses.There are no funct3, rs1, rs2, and funct7 in U-type. This type of instruction structure is very simple.

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/6eda3240-655e-4919-a1d5-38247b6b0680)



|FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |The immediate value, which forms the upper 20 bits of the immediate value.|
  |**rd**| 5 bits |The destination register where the result is written.|
  |**imm[31:12]**| 20 bits |The upper part of the immediate value. |


 ## J-TYPE
 J-Type instructions in RISC-V are used for jump operations, specifically for the JAL (Jump and Link) instruction. These instructions enable jumps to a specific address and optionally save the return address in a register. The format of a J-Type instruction is as follows:


 ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/c619fdfd-0f68-4013-87e9-7e48b083c1a1)


 
|FIELDS| BITS| DESCRIPTION |
  |---------|-----|-----------|
  |**opcode**| 7 bits |Specifies the primary operation category, which is 1101111 for the JAL instruction.|
  |**rd**| 5 bits |The destination register where the return address is stored.|
  |**imm[20/10:1/11/19:12]**| 20 bits |The immediate value, which is used to calculate the jump target address. The bits are placed non-contiguously to fit into the instruction format.|

  let us compute some 32-bit Instruction code in the Instruction type format for some RISC-V Instructions 

### ADD r1,r2,r3
```
Type : R-Type

opcode : 0110011

rd : 00001 

funct3 : 000

rs1 : 00010 

rs2 : 00011

funct7 : 0000000

32-bit code : 0000000 00011 00010 000 00001 0110011
```

### SUB r3,r1,r2

  ```
Type : R-Type

opcode : 0110011

rd : 00011 

funct3 : 000

rs1 : 00010 

rs2 : 00001

funct7 : 0100000

32-bit code : 0100000 00010 00001 000 00011 0110011
```
      
 ### AND r2,r1,r3

  ```
Type : R-Type

opcode : 0110011

rd : 00011 

funct3 : 111

rs1 : 00001 

rs2 : 00011

funct7 : 0000000

32-bit code : 0000000 00011 00001 111 00010 0110011
```

### OR r8,r2,45

```
Type : R-Type

opcode : 0110011

rd :  00010

funct3 : 110

rs1 : 0001 0

rs2 : 00101

funct7 : 0000000

32-bit code : 0000000 00101 00010 110 01000 0110011
```

### XOR r8,r1,r4
```
Type : R-Type

opcode : 0110011

rd :  01000

funct3: 100

rs1 : 00001

rs2 : 00100

funct7 : 0000000

32-bit code : 0000000 00100 00001 100 01000 0110011
```

### SLT r10,r2,r4
```
Type : R-Type

opcode : 0110011

rd :  01010

funct3 : 010

rs1 : 00010

rs2 : 00100

funct7 : 0000000

32-bit code : 0000000 00100 00010 010 01010 0110011
```

### ADDI r12,r3,5

```
Type : I-Type

opcode : 0010011

rd :  01100

funct3 : 000

rs1 : 00011

imm[11:0] :  000000000101

32-bit code : 000000000101 00011 000 01100 0010011
```

### SW r3,r1,4

```
Type : I-Type

opcode:  0100011

rd : 00011

funct3 : 000

rs1 : 00001

imm[4] : 000000000100

32-bit code : 000000000101 00011 000 01100 0010011
```

### SRL r16,r11,r2

```
Type : R-Type

opcode : 0b0110011

rd : 0b10000

funct3 : 0b101

rs1 : 0b01011

rs2 :  0b00010

funct7 : 0b0000000

32-bit code : 0000000 00010 01011 101 10000 0110011
```

### BNE r0,r1,20
```
Type : B-Type

opcode : 1100011

funct3 : 001

rs1 :  00000

rs2 :  00001

imm : 000000000010100

32-bit code: 1100011 001 00000 00001 000000010100
```
### BEQ r0,r0,15
```
Type: I-Type

opcode: 0001100

rd : 00000

funct3: 000

rs1 :00000

imm[15]: 000000000001111

32-bit code: 000000001111 00000 000 00000 0001100
```

### LW r13,r11,2
```
Type: I-Type

opcode: 0000011

rd : 1101

rs1 : 1011

imm[2]: 000000000010

32-bit code: 0000011 01011 01101 000000000000010
```
### SLL r15,r11,r2

```
Type: R-Type

opcode: 0110011

rd : 01111

funct3: 001

rs1 : 00011

rs2 :  00010

funct7: 0000000

32-bit code:  0000000 00010 00011 001 01111 0110011
```
--------------
# TASK 5
## USING RISCV CORE ,CREATE A VERILOG NETLIST AND TESTBENCH AND TO ANALYSE THE WAVEFORMS
### STEPS
1.To clone repository ,use the command 
```
      $ git clone https://github.com/vinayrayapati/rv32i.git my_riscv_project
      $ cd my_riscv_project
```
2. To install simulation tools,
 ```
        $ sudo apt update
      $ sudo apt install iverilog gtkwave
 ```


   ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/6c1e99b0-fd6f-4b34-bfef-680c4266734e)

Let's anlayse the waveform for some of the instructions of RISCV 

#### ADD

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/d6f9fc92-5476-43d1-9ea6-ecbe0f2cce98)

#### SUB

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/39b5c61a-385d-4ac1-bbdf-abca720b00d0)

#### AND

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/72258adf-d15f-4fe7-86ad-ab908d850bf0)

#### OR

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/437799b2-a493-4867-998d-535a14e57582)

#### XOR

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/6cf74450-7aae-4aa9-9381-45a8def8560e)

#### SLT

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/a2f9b764-4448-4a55-a2a3-379310c77ff3)

#### ADDI

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/90f6abd1-8d6a-4463-8b29-814a5320b577)

#### SW

![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/a557e6c8-52ee-4999-a5b7-46ed2ae5a18a)

