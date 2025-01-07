# VLSI_RISC-V_Internship


## Task 1

Writing the code for sum of first n natural numbers and compiling  it with gcc compiler


![Screenshot 2024-12-23 193505](https://github.com/user-attachments/assets/c0d48825-af7e-4849-b3f0-0a79efd75959)

Next we will compile the code 'Karthik.c' in the RISC-V compiler.

Using option '-O1'


![Screenshot 2024-12-23 193505](https://github.com/user-attachments/assets/e15068fb-4d26-45e1-81f8-85d7838f133f)


The address of the main section is 10184(Hex) and we got 11 instructions.

![Screenshot 2024-12-23 120531](https://github.com/user-attachments/assets/b03f8d19-353c-4ee6-b21e-0ac9b6f14342)

Using option '-Ofast'


![Screenshot 2024-12-23 193533](https://github.com/user-attachments/assets/daf64f20-2f0b-44b6-a035-2c4b228079e9)

The address of the main section is 100B0(Hex) and we got 11 instructions.

![Screenshot 2024-12-23 121009](https://github.com/user-attachments/assets/eef49bd5-903d-4e00-bc37-c7c9c1ef08f3)


## Task 2

Simulation using Spike Tool

![image](https://github.com/user-attachments/assets/0498acd6-e3f4-4b28-b588-c4ad9208f986)

Assembly language code of the  **Karthik.c**

![Screenshot 2024-12-27 233158](https://github.com/user-attachments/assets/93744059-1723-4cf5-bd5b-109b7f423fb5)

Debugging using Spike Tool

![Screenshot 2024-12-27 234223](https://github.com/user-attachments/assets/bf5c8694-9e93-4622-bf44-69272f02c9fc)

![Screenshot 2024-12-27 234450](https://github.com/user-attachments/assets/3645e820-d77c-4547-a502-322aba5bdbec)


### Example 

Factorial code using recursion

```
#include<stdio.h>
 int Fact(int n);
int main() {
    int n;
    printf("Enter a positive integer: ");
    scanf("%d",&n);
    printf("Factorial of %d = %d", n, Fact(n));
    return 0;
}

 int Fact(int n) {
    if (n>=1)
        return n*Fact(n-1);
    else
        return 1;
}
```
Simulation of  **Factorial.c** by GCC complier & Spike tool

![Screenshot 2024-12-28 001554](https://github.com/user-attachments/assets/6ec93f23-8a3a-4f55-b57a-bb292dd017e6)

Assembly language code of the  **Factorial.c**

![Screenshot 2024-12-27 235736](https://github.com/user-attachments/assets/23cb3ce1-c835-4f2f-93b0-c4905ed2d49b)

The address of the main section is 100b0 (Hexadecimal) and got 34 instructions

Debugging using Spike Tool

![Screenshot 2024-12-27 235903](https://github.com/user-attachments/assets/23326adb-5a32-4d67-8c1a-55e9ef8d28bf)
## Task 3 

#### RISC-V ISA Set
RISC-V instructions are divided into several types based on the format of their encoding. The main instruction types are:

1. 	R-Type (Register-type): These instructions involve registers and typically use three registers.  They are used for arithmetic operations, logic operations, and some others. The entire 32-bit instruction is divided into six fields.

![image](https://github.com/user-attachments/assets/1ec81d4c-93d6-4671-8808-8a9b2d84776d)
    
- [31:25] funct7: Specifies additional control signals for the operation, often used to differentiate between instructions in combination with funct3.
- [24:20] rs2: Source register 2 (second operand for the operation).
- [19:15] rs1: Source register 1 (first operand for the operation).
-	[14:12] funct3: Specifies the operation to perform (e.g., add, subtract) in combination with opcode and funct7.
- [11:7] rd: Destination register (where the result of the operation is stored).
- [6:0] opcode: Specifies the instruction type (e.g., R-Type, I-Type).
- Example: ADD, SUB, AND, OR, XOR
2.	I-Type (Immediate-type): These instructions involve an immediate value (constant) & a source register that is used for arithmetic, logic, and memory operation.

![image](https://github.com/user-attachments/assets/64d82926-157d-4756-924d-b0f58e54f3b4)

- [31:20] imm[11:0]: Immediate value (constant) used as an operand in the instruction.
-	[19:15] rs1: Source register 1 (first operand).
-	[14:12] funct3: Specifies the operation in combination with the opcode.
-	[11:7] rd: Destination register (where the result is stored).
-	[6:0] opcode: Specifies the instruction type.
-	Example: ADDI, ANDI, LUI, JALR
3.	S-Type (Store-type): These instructions are used for store operations that store data into memory from a register.
 ![image](https://github.com/user-attachments/assets/c879b538-d05c-4ca3-83fb-58c3ff6c95a7)

-	[31:25] imm[11:5]: Upper 7 bits of the immediate value.
-	[24:20] rs2: Source register 2 (data to store in memory).
-	[19:15] rs1: Base register for the memory address calculation.
-	[14:12] funct3: Specifies the operation (e.g., store byte or word).
-	[11:7] imm[4:0]: Lower 5 bits of the immediate value.
-	[6:0] opcode: Specifies the instruction type.
-	Example: SW, SH, SB
       
4.	 B-Type (Branch-type): These are branch operations used for conditional branching.
 ![image](https://github.com/user-attachments/assets/d1e52356-e7a6-4a9d-ab08-eb46b440d6a4)
-	[31] imm[12]: Most significant bit of the immediate value.
-	[30:25] imm[10:5]: Bits 10 to 5 of the immediate value.
-	[24:20] rs2: Second source register (used for comparison).
-	[19:15] rs1: First source register (used for comparison).
-	[14:12] funct3: Specifies the branch condition (e.g., equal, not equal).
-	[11:8] imm[4:1]: Bits 4 to 1 of the immediate value.
-	[7] imm[11]: Bit 11 of the immediate value.
-	[6:0] opcode: Specifies the instruction type.
-	Example: BEQ, BNE, BLT, BGE
5.	U-Type (Upper immediate-type): These instructions involve loading large immediate values into registers, typically used for the upper 20 bits of addresses.
 ![image](https://github.com/user-attachments/assets/4cd93872-8bdf-47c8-a419-f83d4386ed77)
-	[31:12] imm[31:12]: Immediate value (20 most significant bits) loaded into the upper bits of a register.
-	[11:7] rd: Destination register.
-	[6:0] opcode: Specifies the instruction type.
-	Example: LUI, AUIPC

6.	J-Type (Jump-type): These instructions are used for unconditional jumps (typically for function calls and returns).
 ![image](https://github.com/user-attachments/assets/33af4804-9ec6-468f-ab1b-7b97565a0336)
-	[31] imm[20]: Most significant bit of the immediate value.
-	[30:21] imm[10:1]: Bits 10 to 1 of the immediate value.
-	[20] imm[11]: Bit 11 of the immediate value.
-	[19:12] imm[19:12]: Bits 19 to 12 of the immediate value.
-	[11:7] rd: Destination register (stores the return address after the jump).
-	[6:0] opcode: Specifies the instruction type.
-	Example: JAL, JALR


![Screenshot 2025-01-02 125512](https://github.com/user-attachments/assets/b3c607cf-0f3b-4389-8cf5-0495fcf5d95b)

Here are the 15 unique RISC-V instructions from riscv-objdmp of Factorial.o

- lui a0, 0x2b
- addi sp, sp, -48
- sd ra, 40(sp)
- jal ra, 104d8
- li a1, 1
- mv a5, s1
- addiw s0, a5, -1
- blez s1, 10130
- auipc a5, 0xffff0
- bnez s0, 100ec
- sext.w a1, a0
- lw s1, 12(sp)
- ld s0, 32(sp)
- ret
- beqz a5, 10150


Let's analyse each instruction one by one

```
lui a0, 0x2b
```  
> * Instruction Type: LUI (Load Upper Immediate)
> * Format: imm[31:12] | rd | opcode
> *	imm[31:12] = 0x2b (0000000000101011)  
> * Opcode for lui = 0110111   
> * rd = a0 = 010`0 

  
**32 bits instruction :**```0000000000101011_01010_0110111```   

Hex: ``` 0002B537 ```
________________________________________
________________________________________


```
addi sp, sp, -48
```  
> * Instruction Type: I-type (Immediate Arithmetic)
> * Format: imm[11:0] | rs1 | func3 | rd | opcode
> *	imm[11:0] = -48 = 1111111111011000  (two's complement of 48) 
> * Opcode for addi = 0010011   
> * rs1 = sp = 00010
> * rd = sp = 00010 
> * func3 = 000 

  
**32 bits instruction :** ```111111011000_00010_000_00010_0010011 111111010000_00010_000_00010_0010011```   

Hex: ``` 0xFD010113  ```
________________________________________
________________________________________

```
sd ra, 40(sp)
```  
> * Instruction Type: S-type (Store)
> * Format: imm[11:5] | rs2 | rs1 | func3 | imm[4:0] | opcode
> * Opcode for sd = 0100011  
> * rs1 = sp = 00010
> * rs2 = ra = 00001
> * func3 = 011

  
**32 bits instruction :** ```0000000_00001_00010_011_01000_0100011 0000001_00001_00010_011_01000_0100011 ```  

Hex: ``` 0x02113423  ```
________________________________________
```
jal ra, 104d8
```  
> * Instruction Type:  J-type (Jump)
> * Format:imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd | opcode
> *	imm[20] = 0
> * imm[10:1] =  1000001000
> * imm[11] = 0
> * imm[19:12] = 00000000
> * imm[11] = 0
> * Opcode for jal = 1101111  
> * rd = ra = 00001

  
**32 bits instruction :** ```0_1000001000_0_00000000_00001_1101111 ```

Hex: ``` 0x410000ef  ```
```
lw s1, 12(sp)
```  
> * Instruction Type:  I-type (Load)
> * Format: imm[11:0] | rs1 | func3 | rd | opcode
> *	imm[11:0] = 12 = 000000001100
> * rs1 = sp = 00010
> * rd = s1 = 10001
> * func3 = 010
> * Opcode for lw = 0000011  

**32 bits instruction :** ```000000001100_00010_010_01001_0000011```  
Hex: ``` 0x00c12483  ```

```
mv a5, s1 
```  
> * Instruction Type: R-type (Register Operation)
> * Format: funct7 | rs2 | rs1 | funct3 | rd | opcode

> * rs2 = zero = 00000
> * rs1 = s1 = 10001
> * func3 = 000
> * func7 = 0000000 
> * Opcode for mv = 0010011   
> * mv a5, s1 is Equivalent to addi a5, s1, 0
**32 bits instruction :** ```0000000_00000_01001_000_01111_0010011  `` 
Hex: ``` 00048793  ```
________________________________________
```
li a1, 1
```  
> * Instruction Type:  I-type (Immediate Load)
> * Format: imm[11:0] | rs1 | func3 | rd | opcode
> *	imm[11:0] = 1 = 000000000001
> * rs1 = zero = 00000
> * rd = a1 = 01101
> * func3 = 000
> * Opcode for li = 0010011   

**32 bits instruction :** ```000000000001_00000_000_01011_0010011``` 
Hex: ``` 0x00100593  ```

```
addiw s0, a5, -1
```  
> * Instruction Type:  I-type (Immediate Load)
> * Format: imm[11:0] | rs1 | func3 | rd | opcode
> *	imm[11:0] = -1 = 111111111111
> * rs1 = a5 = x15=  01111
> * rd = s0 = 01000
> * func3 = 000
> * Opcode for addiw = 0011011  

**32 bits instruction :** ```111111111111_00101_000_10000_0011011 111111111111_01111_000_01000_0011011``` 
Hex: ``` fff7841b  ```
```
sext.w a1, a0
```  
> * Instruction Type:  R-type (Register Operation)
> * Format: funct7 | rs2 | rs1 | funct3 | rd | opcode
> * rs1 = a0 = 01010
> * rs2 = zero = 00000
> * rd = a1 = 01011
> * func3 = 000
> * func7 = 0000000
> * Opcode for sext = 0011011  

**32 bits instruction :** ```0000000_00000_01010_000_01011_0011011```
Hex: ``` 0x0005059b  ```
```

ld ra, 40(sp)
```  
> * Instruction Type:  I-type (Load)
> * Format:  imm[11:0] | rs1 | func3 | rd | opcode
> * imm[11:0] = 40 = 000000101000
> * rs1 = sp = 00010
> * rd = ra = 00001
> * func3 = 011
> * Opcode for ld = 0000011  

**32 bits instruction :** ```000000101000_00010_011_00010_0000011```
Hex: ```0x02813083 ```
```
auipc a5, 0xffff0
```  
> * Instruction Type: AUIPC (Add Upper Immediate to PC)
> * Format:   imm[31:12] | rd | opcode
> * imm[31:12] = 11111111111111110000 
> * rd = a5 = x15 = 01111
> * Opcode for auipc = 0010111   

**32 bits instruction :** ```11111111111111110000_01111_0010111```
Hex: ``` 0xffff0797  ```
```
 beqz a5, 10150 <register_fini+0x18>
```  
> * Instruction Type:  BEQZ (Branch if Equal to Zero)
> * Format:  imm[12] | imm[10:5] | rs2 | rs1 | func3 | imm[4:1] | imm[11] | opcode
> * imm[12] = 0 = 0 
> * imm[10:5] = 0000000 = 0000000
> * rs2 = 00000 = 00000
> * rs1 = a5 = x15 = 011111
> * func3 = 000 = 000
> * imm[4:1] =  1000
> * imm[11] = 0 = 0
> * Opcode for  beqz = 1100011    

**32 bits instruction :** ```0_000000_00000_01111_000_1000_0_1100011```
Hex: ``` 0x00078863  ```


