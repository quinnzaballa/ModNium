# Arithmetic Logic Unit (ALU)

> This section contains all the [Digital](https://github.com/hneemann/Digital) files for simulating and tinkering, Draw.io, and Graphviz.

The ALU (Arithmetic Logic Unit) is the part of the computer's processor that does all the actual math and logic calculations, like adding numbers or comparing data.

## Modules

##### Registers:

1. ALU Temporary Register 16-bit
   * TREG 16x8
1. Accumulator 16-bit

##### Logic Units:

1. **XOR**
   * NOT & XNOR mode
1. **OR**
1. **AND**

##### Arithmetic Unit:

1. **FADDER**
   * 1 Slave, 1 Master; Dual-FADDER Compute.

##### Controller:

1. Hybrid Control Unit *(Asyncronous Control Unit)*
   * FSM Aided Microcode

## Capability

##### IO data bus length:

* IN
  * REG A 16-bit
  * REG B 16-bit
* OUT (Accumulator)
  * OUTX 16-bit
  * OUTY 16-bit
  * DWORD = OUTY + OUTX *(for extended operation)*

##### Control bits data length:

* Control Bits/OpCode - 4-bits
* Count/Mul - 8-bits
* Status OW Bits - 8-bits

##### Operations:

*Legend:*

* *n = loop count*
* *lb = Leading bit position*


| OpCode | Type | Operation | Clock Cycle |  Level  | Specialty                                                |
| :----- | :--: | --------- | ----------- | :------: | -------------------------------------------------------- |
| 0x00   | FSM | ADD       | 1           |  Basic  | NA                                                       |
| 0x01   | FSM | AND       | 1           |  Basic  | NA                                                       |
| 0x02   | FSM | OR        | 1           |  Basic  | NA                                                       |
| 0x03   | FSM | XOR       | 1           |  Basic  | NA                                                       |
| 0x04   | FSM | NAND      | 1           |  Basic  | NA                                                       |
| 0x05   | FSM | NOR       | 1           |  Basic  | NA                                                       |
| 0x06   | FSM | XNOR      | 1           |  Basic  | NA                                                       |
| 0x07   | FSM | SUB       | 1           |  Basic  | NA                                                       |
| 0x08   | FSM | NOT       | 1           |  Basic  | OpCode + 0x08 will invert the result before accumulator. |
| 0x09   | MiCd | MUL       | n+1         | Extended | NA                                                       |
| 0x0A   | MiCd | DIV       | n+lb+2      | Extended | NA                                                       |

## System Architecture & Design

#### Microarchitectural Block Diagram

![](assets/ALU-ModNium.svg)
