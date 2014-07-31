---
title: Hardware/Software Interface - notes
date: 2014-07-24
layout: post
category: tech
---

## What is ISA ?

* A state representation and maintenance system
    * registers
    * program counter
    * memory access (memory address)

* Instruction set to change the above state
* Instruction set - encoding
* ISA types:
    * CISC (Complex instruction set)
    * RISC (Reduced instruction set)

* Defines the system’s state and instructions
    that are available to the software.

## What makes program faster(perceived) ?

* Obviously - Hardware (exeucting instructions, pipelining etc)
* The compiler - Generating most appropriate ‘instruction set’, based on instruction set.
* The compiler - Generating most minimal code, using code optimization
* The program code - algorithms etc

## Definitions

* Architecture
    * The parts of a processor design that one needs to 
    understand to write assembly code.
    * What is directly visible to software.

* Microarchitecture
    * Implementation of arcitecture

* Examples:
    * Is cache size “architecture” - NO
    * core frequency - microarchitecture
    * Number of registers - architecture


## Assembly Programmer’s View

    * Programmer - Visible State
        * PC - Program counter
        * Registers
        * Condition Codes
    * Memory
        * Byte addressable array
        * Code, user data, OS data
        * Stack, Heap etc.

## Three Basic Kinds of Instructions

* Perform arithmetic function on register or memory data

* Transfer data between memory and register
    * Load data from memory into register
    * Store register data into memory

* Transfer control
    * Unconditional jumps to/from procedure
    * Conditional branches

## Data Types in Assembly

* Integer data of 1,2,4, 8 bytes
    * Data values
    * Addresses (untyped pointers)
* Floating point data of 4, 8, or 10 bytes

## Data Availability

* Data is available as
    * immediate
    * register
    * memory

## Data Transfer
    * immediate -> register, memory
    * register -> register, memory
    * memory -> register
## Memory addressing modes

    * Indirect (%ebx). The address is in register
    * Indirect + offset

## movx Src,Dest -> move x bytes from Src, Dest

    X can take following shapes

    * b -> byte
    * w -> 2 bytes
    * l -> 4 bytes
    * q -> 8 bytes (quad word, 4 words)

## Registers in IA32 and x86-64

### IA 32
    * each register is of 32 bits wide
    * 8 registers (eax,ebx..esp, ebp)
    * 2 special (ebp, esp)
    * the rest general purpose
    * lower halfs can be accessed like
    * for e.g eax
        * ax(lowest 16 bits)
        * ah(high 8 bits of ax), 
        * al(low 8 bits of ax)

### x86-64
    * each register is of 64 bits wide 
    * 16 registers(rdi, rsi, rd1,rd11..etc)
    * 2 special purpose (rbp, rsp)
    * the rest general purpose 
    * arguments are passed via registers
    * so minimal stack manipulation

## Complete Memory Addressing Modes

* Most General form

    * D(Rb, Ri, S) => Mem[Reg[Rb] + S*Reg[Ri] + D]
    * D -> Constant displacement, 1,2,4 bytes
    * Rb -> Base register
    * Ri -> Index register
    * S -> Scale factor(1, 2, 4, or 8)

* Special cases: can use any combination of D, Rb, Ri and S
* Default values for when missing in address pattern
    * D -> 0
    * S -> 1
    * Ri -> 0

## LEAL -> Load effective address long
    * leal Src, Dest
    * Src is address mode experssion
    * Set Dest to address computed by expression

## Compiling for debugging

* gcc -ggdb3 -W -Wall -o <dest> *.c

## GDB instructions 

* gdb <executable>
* run <arguments>
* disassemble
* break - putting breaks (line number, function name, filename:linenumber, +n (breakpoint at n step away))
* clear breakpoint-id
* disable/enable breakpoint-id
* info breakpoints
* info registers
* x /2wx $rsp/<hexaddress> (/2wx -> eXamine 2 word and display in Hex)
* nexti  - execute next instruction
* step - execute next statement
* backtrace - display frame stack
* finish - return from current function call
* continue - execute till the next break point
* quit - exit the current gdb
* list - list source +1, -2, +, function-name, - etc, 
* ptype - type of variable/symbol
* print - value of variable/symbol
* where - shows current line 


## parameter passing in x32 and x64

* in x32 systems, parameters a passed via stack
* in x64 systems, they are passed via registers (rdi, rsi, r1~r13)

## Control structures and assembly code

* cmp <v1> <v2>
* jmp zero, less than, greater than, not-equal, equal etc
* if statement - jmp, cmp, test
* while/do-while loop - condition, jmp labels, goto etc
* for -> same as above
* switch -> using jump table and jump targets

## knowing/fiddling the executable

* size <executable>
* strip <options> <executable>
* objdump -h <executable>

## Stacks in Memory and Stack Operations

* Stack grows down (lives at the top of VM address space)
    * each stack frame contains
    * parameters
    * local variables
    * return address
    * saved registers 
    * saved previous frames stack base pointer
* Heap grows up
* Static Data (Global variables)
* Literals (fixed data)
* program text - instructions live at bottom starting at address 0x00000000

