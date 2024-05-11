---
tags:
  - incomplete
  - degree/compsys/machinearchitecture
---
![[Machine Architecture MOC 🌍]]
### MIPS 
MIPS is the Microprocessor without Interlocked Pipeline Stages.
It was designed in early 1980s at Stanford University, led by John Hennessy.
It powered SGI workstations until mid-1990s
Still used in embedded systems and consumer electronics.

---
### Design Principles 
- Simplicity favours regularity 
- makes the common case faster 
- Smaller is faster 
- Good design demands good compromises 

---
### Architecture 
MIPS uses 32-bit RISC processor with
- 32 bit words 
- About 110 instructions in the instruction set.
- 32 general purpose registers 

---
### Registers 

| Name        | Number | Use                     |
| ----------- | ------ | ----------------------- |
| `$0`        | 0      | The constant value 0    |
| `$at`       | 1      | Assembler temporary     |
| `$v0`-`$v1` | 2-3    | Function return values  |
| `$a0`-`$a3` | 4-7    | Function arguments      |
| `$t0`-`$t7` | 8-15   | Temporary variables     |
| `$s0`-`$s7` | 16-23  | Saved variables         |
| `$t8`-`$t9` | 24-25  | Temporary variables     |
| `$k0`-`$k1` | 26-27  | OS temporaries          |
| `$gp`       | 28     | Global pointer          |
| `$sp`       | 29     | Stack pointer           |
| `$fp`       | 30     | Frame pointer           |
| `$ra`       | 31     | Function return address |

---
### MIPS Assembly 
An example of some code would be `a = b + c`, which in MIPS would be `add $s0, $s1, $s2` where this is adding `$s1` and `$s2` and putting it into `$s0`.
#### Instruction Types 
In MIPS, there are 3 types of instructions:
- R-type: Register operands 
- I-type: Immediate operands 
- J-type: Jump Instructions 
##### R-type Instructions 

|  `op`  |  `rs`  |  `rt`  |  `rd`  | `shamt` | `funct` |
| :----: | :----: | :----: | :----: | :-----: | :-----: |
| 000000 | 00000  | 00000  | 00000  |  00000  | 000000  |
| 6 bits | 5 bits | 5 bits | 5 bits | 5 bits  | 6 bits  |
Operands 
- `rs` and `rt` are source registers.
- `rd` is the destination register.
- `op` is the opcode, which is always 0 for R-type.
- `funct` is the function, it specifies which R-type instruction it is.
- `shamt` is the shift amount for shift instructions. Otherwise it is 0.
###### Add Instruction 
`add $s0, $s1, $s2`
When translated into machine language, we get 

|  `op`  | `rs`  | `rt`  | `rd`  | `shamt` | `funct` |
| :----: | :---: | :---: | :---: | :-----: | :-----: |
|   0    |  17   |  18   |  16   |    0    |   32    |
| 000000 | 10001 | 10010 | 10000 |  00000  | 100000  |
###### Sub Instruction
`sub $t0, $t3, $s5`

|  `op`  | `rs`  | `rt`  | `rd`  | `shamt` | `funct` |
| :----: | :---: | :---: | :---: | :-----: | :-----: |
|   0    |  11   |  13   |   8   |    0    |   34    |
| 000000 | 01011 | 01101 | 01000 |  00000  | 100010  |
##### I-Type Instructions 

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 000000 | 00000 | 00000 | 0000 0000 0000 0000 |
Operands
- `op` is the opcode 
- `rs` and `rt` are register operands
- `imm` is the 16 bit immediate in two's complement.

`rs` and `imm` are used as source operands. `rt` is source in some instructions and destination in others.
###### Addi instruction 
`addi $s0, $s1, 5`

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 8      | 17    | 16    | 5                   |
| 001000 | 10001 | 10000 | 0000 0000 0000 0101 |
###### Li instruction 
`li $s0, 5`

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 13     | 0     | 16    | 5                   |
| 001101 | 00000 | 10000 | 0000 0000 0000 0101 |
##### J-Type Instructions 

| `op`   | `addr`                           |
| ------ | -------------------------------- |
| 000000 | 00 0000 0000 0000 0000 0000 0000 |
| 6 bits | 26 bits                          |
Operands 
- `op` is the opcode 
- `addr` is a 26 bit address 
###### J Instruction 
Let's say we want to jump to the memory address `0x0040002C`. Firstly, we need the opcode for a `j` instruction, which is `000010`.

Next, we convert the 32-bit address into the 26 bit `addr`. There's 3 steps to do this:
- Convert the hex to 32 bits. `0000 0000 0100 0000 0000 0000 0010 1100`
- Remove the first 4 bits. `0000 0100 0000 0000 0000 0010 1100`
- Remove the last 2 bits. `00 0001 0000 0000 0000 0000 1011`

Now, we append the opcode to the start to get our jump instruction 
`0000 1000 0001 0000 0000 0000 0000 1011`, `0x0810000B`

---
### MIPS Memory 
In MIPS, a word is 32 bits.
Memory addresses are 32 bits
The memory is [[Byte Addressable]].

With the 32 bit addresses, MIPS can address 4 gigabytes.
The word addresses are all divisible by 4 and range from `0` to `0xFFFFFFFC`

MIPS separates it's memory into four segments:
- Text 
- Global Data 
- Dynamic Data 
- Reserved 

![[Pasted image 20240505182722.png]]

#### The Text Segment 
Stores the machine language program.
Stores about 256MB of code 

The 4 most significant bits of any word address are all 0, and so the 26 bit `addr` field in the [[#J-Type Instructions]] is sufficient to specify any address in the text segment.
#### The Global Data Segment 
The global data segment stores global variables, which can be seen by all functions in a program.
It stores 64Kb of data.

Global variables are accessed using the pointer `$gp`.

By convention, we initialise `$gp` at the middle of the global data at `0x10008000`.
It's value stays constant during execution and variables are accessed as offsets from `$gp`.
#### The Dynamic Data Segment 
Stores data that is dynamically allocated and deallocated throughout the execution of the program.
It's the largest segment of memory used by a program, spanning about 2GB of space.

Data here is stored in a [[Stacks|Stack]] and a [[Heaps|Heap]].
#### The Reserved Segments 
The reserved segments are used by the OS and cannot be used by a program.

---
### Addressing Modes 

MIPS has 5 addressing modes.

3 are used for reading and writing operands
- Register Only 
- Immediate 
- Base Addressing 

and 2 are used for writing to the [[Program Counter]].
- PC-Relative 
- Pseudo-direct.
#### Register Only 
Uses registers for all source and destination operands.
[[#R-type Instructions]] use register only addressing.
#### Immediate 
Uses registers and a 16-bit immediate as operands.
Some [[#I-Type Instructions]] use immediate addressing, depending on how the 16-bit immediate is used.
#### Base Addressing 
Used in memory access instructions.
Implemented by [[#I-Type Instructions]].
The address of the memory operand is computed by adding the base address in `rs` to a 16-bit offset stored in `imm`.

Used by instructions:
- `lw` load word
- `lb` load byte 
- `sw` store word 
- `sb` store byte 
to read and write data to the memory.

##### Examples 
`lw $s1, 8 ($0)`
The address referenced here is address 8 plus the address stored in `$0`, which is always 0 in this case. So it's loading word 8+0=8 and storing it in `$s1`.

`sw $s3, 4 ($0)`
Write `$s3` to word 1

`sw $s4, 0x20 ($0)`
Write `$s4` to word 8

`sw $s5, 200 ($0)`
Write `$s5` to word 50

`lw $t2, 32 ($0)`
Load word 8 into `$t2`
In machine code, this looks like 

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 35     | 0     | 10    | 32                  |
| 100011 | 00000 | 01010 | 0000 0000 0010 0000 |

`sw $s1, 4 ($t1)`
Store `$s1` in word (4 plus the address in `$t1`)

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 43     | 9     | 17    | 4                   |
| 101011 | 01001 | 10001 | 0000 0000 0000 0100 |
#### PC-Relative Addressing 
Branching instructions can use PC-relative addressing to specify the new value of the [[Program Counter]] if the branch is taken.

Take this example code snippet.
![[Pasted image 20240505191349.png]]
This uses the instruction `bne $t1, $0, loop`, which branches to `loop` if `$t1` and `$0` are not equal.

To calculate the `imm` for this instruction, we take the PC value of the target address `0x40`, and subtract from it the address of the instruction after the branch instruction `0x58`, then divide by 4. This gives us an `imm` equal to `-6`.

Another way to get this is to count the instructions between the target instruction and the instruction after the branch, going negative if you're going backwards in memory.

Translated to a machine language [[#I-Type Instructions|I-Type Instruction]]:

| `op`   | `rs`  | `rt`  | `imm`               |
| ------ | ----- | ----- | ------------------- |
| 5      | 9     | 0     | -6                  |
| 000101 | 01001 | 00000 | 1111 1111 1111 1010 |
Remember that the `imm` are stored in [[Two's Complement]].

---
#### Pseudo-direct Addressing
In direct addressing, an address is specified in the instruction. Since MIPS has 32 bit addresses and 32-bit instructions, we will run out of bits to represent the opcode and address.

So, instead MIPS uses pseudo-direct addressing, storing the address in just 26 bits.

Converting the address `0x004000A0` to a 26-bit `addr` is done by:
- Converting it to binary `0000 0000 0100 0000 0000 0000 1010 0000`
- Remove the first 4 bits `0000 0100 0000 0000 0000 1010 0000`
- Remove the last 2 bits `00 0001 0000 0000 0000 0010 1000`

So `addr = 00 0001 0000 0000 0000 0010 1000`

This works because the word addresses are always multiples of 4, so the last 2 bits are always `00`. And, where [[#The Text Segment]] is in memory means the 4 most significant bits are also always `0000`.

To execute the instruction, the opposite is done. We take `addr`, add 4 bits to the front and 2 bits to the end, `0000 0000 0100 0000 0000 0000 1010 0000`.

---
### Functions 
MIPS assembly functions have arguments and a return value.

One instruction is `jal`, which stands for "Jump and Link".

Take this code snippet
![[Pasted image 20240506133224.png]]

A `jal` jumps to the address of `simple`, just like a `j`. But, it also stores in register `$ra` the address where the program should return to when `simple` has been executed, `0x00400204`.

Then `simple` calls `jr`, a "Jump Register", which jumps to the address stored in a register. Notice that `jr` is an [[#R-type Instructions|R-Type Instruction]] and not a [[#J-Type Instructions|J-Type Instruction]].

#### Arguments 
![[Pasted image 20240506133558.png]]

Recall that the [[#Registers]] `$a0` to `$a3` are the function argument registers, so we store our arguments in there. And registers `$v0` and `$v1` are the function return registers, so we put our return values in there.

---
### Loops 
Compute the nth triangular number. A program would take an input $n$ and output $T(n)$ where

$$
T(n) = 1 + 2 + \ldots + n
$$

![[Pasted image 20240506134916.png]]











---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
