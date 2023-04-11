# Table Of Contents

- [The Why of Disassembly](#the-why-of-disassembly)
- [The How of Disassembly](#the-how-of-disassembly)

 # The Why of Disassembly

The purpose of disassembly tools is often to facilitate understanding of programs when source code is unavailable. Common situations in which disassembly is used include the following:

- Analysis of malware
- Analysis of closed source software for vulnerabilities
- Analysis of closed source software for interoperability
- Analysis of compiler-generated code to validate compiler performance or correctness
- Display of program instructions while debugging

## Malware Analysis
Malware authors seldom provide source code for their creations. Dynamic and static analysis are the main techniques for malware analysis. Dynamic analysis involves allowing the malware to execute in a controlled environment while recording every observable aspect of its behavior. Static analysis attempts to understand the behavior of a program simply by reading through the disassembly code.

## Vulnerability Analysis
Vulnerability analysis involves discovering a potentially exploitable condition in a program. This is often accomplished using dynamic or static analysis. Disassembly listings provide the level of detail required to identify variables that can be manipulated by an attacker.

## Software Interoperability
When software is released in binary form only, it is difficult for competitors to create software that can interoperate with it or to provide plugin replacements for that software. Static code analysis is almost the only remedy in these cases.

## Compiler Validation
Good disassembly tools are often required to verify that the compiler is doing its job in accordance with any design specifications. Analysts may also be interested in locating additional opportunities for optimizing compiler output.

## Debugging Displays
Disassemblers are commonly used to generate listings within debuggers. It is best to use a debugger in conjunction with a high-quality disassembler to provide better situational awareness and context during debugging.

# The How of Disassembly

## Overview

- Purpose of disassembly
- How the process actually works
- The challenges, assumptions, and compromises involved in an automated disassembly process
- Fundamental algorithms in use for disassembling machine code
- Limitations of disassembler

## Basic Disassembly Algorithm

1. Identify a region of code to disassemble
2. Read the value or values contained at that address and perform a table lookup to match the binary opcode value to its assembly language mnemonic
3. Format and output the assembly language equivalent as part of the disassembly listing
4. Advance to the next instruction and repeat the previous process until we have disassembled every instruction in the file

## X86 Assembly Syntax: AT&T vs. Intel

- Two main syntaxes: AT&T and Intel
- AT&T syntax uses the % symbol to prefix all register names, the use of $ as a prefix for literal constants, and its operand ordering in which the source operand appears on the left and the destination operand appears on the right.
- Intel syntax requires no register or literal prefixes, and the operand ordering is reversed such that the source operand appears on the right and the destination appears on the left.

## Disassembly Algorithms

- Various algorithms exist for determining where to begin a disassembly, how to choose the next instruction to be disassembled, how to distinguish code from data, and how to determine when the last instruction has been disassembled.
- The two predominant disassembly algorithms are linear sweep and recursive descent.
