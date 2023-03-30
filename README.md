# Assembler.hack

Assembler.hack is a 16-bit machine language assembler for the 16-bit Hack Assembly Language. This project was complated as part of building a complete 16-bit computer from the ground up, through the course Nand2Tetris.

## Description

Assembler.hack takes a program file written in the Hack Assembly Language, which is a .asm text file, and assembles it into binary machine code. The assembled machine code program is then written to a new .hack text file with the same name.

The Assembling process is designed in two passes. The first pass scans the entire program, registering all labels in the Symbol Table. The second pass scans the whole program again, this time registering all variables in the Symbol Table. It also parses every instruction and computes the corresponding binary machine code value to be added to the output .hack file. 

## Description
1. **Assembler.py**: Main module. Implements both passes. Computes the machine code for every instruction.
2. **.hack/.asm Files**: Files provided as examples

## Example Usage

```bash
$ python Assembler.py Max.asm
```

### Max.asm

```asm
// Given two numbers stored in register R0 and R1,
// compute the maximum between these values and store it in the R2 register.

  @R0
  D=M              // Get value at R0
  @R1
  D=D-M            // Subtract R1 from R0
  @OUTPUT_FIRST
  D;JGT            // If D>0 (first number is greater), goto output_first
  @R1
  D=M              // Otherwise, use second number
  @OUTPUT_D
  0;JMP            // goto output_d

(OUTPUT_FIRST)
  @R0
  D=M              // Use first number

(OUTPUT_D)
  @R2
  M=D              // M[2] = greatest number

(INFINITE_LOOP)
  @INFINITE_LOOP
  0;JMP            // Infinite loop to end program safely
```

### Max.hack

```
0000000000000000
1111110000010000
0000000000000001
1111010011010000
0000000000001010
1110001100000001
0000000000000001
1111110000010000
0000000000001100
1110101010000111
0000000000000000
1111110000010000
0000000000000010
1110001100001000
0000000000001110
1110101010000111
```
