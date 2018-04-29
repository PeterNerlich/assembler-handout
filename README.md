# Ass.Prog. Overview

## Lowest level

About the True Assembly™

### Registers

Registers follow a naming convention distinguishing them by their size (or rather, which part of the full register is addressed) and which of the different full registers to use. They split in data and pointer registers, of which the former are for general purpose, but some come associated to aid certain atomic operations.

Data registers **post**fixed with **`H`** or **`L`** (High or Low) are **8 bit** registers. Registers **post**fixed with **`X`** are **16 bit** registers uniting their *High* and *Low* part. *All* Registers **pre**fixed with **`E`** (and, for data registers, also *post*fixed with *`X`*) **extend** to the full **32 bit** size.

![info graphic data register sizes and correlation](img/register-info.svg)

--------

The following describes which registers are modified or used for certain atomic operations.

- **`EAX`**
	- accumulator (=target) for 32 bit operations (`mul`, `div`)
	- `AX`: I/O operations: accumulator for 16 bit operations (`mul`, `div`)
	- `AL`: I/O operations: accumulator for 8 bit operations (`mul`, `div`)
- **`EBX`** - (extended) base register
	- for base memory addressing
- **`ECX`** - (extended) counter register
	- iteration register for loops
	- element counter for repeating string operations
	- `CL`: counter register for bit shifting/rotation
- **`EDX`**
	- accumulator extension for 32 bit multiplication/division
	- `DX`: accumulator extension for 16 bit multiplication/division

--------

Pointers are addresses pointing to certain locations in memory. Since registers are the most elementar memory storage units for the CPU, addresses meant to be remembered after some other operation have to be stored in a register, too, so they are not lost during a calculation. Pointer registers cannot be used as data registers and can have unforseen consequences if modified blindly.

![info graphic pointer register sizes](img/pointer-info.svg)

- **`EIP`** - (extended) program counter
	- aka instruction pointer, instruction address register, instruction counter, or just part of the instruction sequencer
	- points to opcode (1st byte of next instruction) and is thus the offset from the start of the code segment
- **`ESP`** - (extended) stack pointer
	- offset to lower byte of the value last pushed onto the stack
	- `ESP` is automatically decremented by the `push` operation
	- `ESP` is automatically incremented by the `pop` operation
- **`EBP`** - (extended) base pointer
	- aka frame pointer (to the stack frame)
	- points to the base of the stack (first address / the lowest element)
	- in stacked frames (= functions calling functions) containing the base pointer of the parent frame
- **`ESI`** - (extended) source index
	- used by opcodes like `movsb` and `movsw` that efficiently copy many bytes of data from the location referenced in `ESI` to the one in `EDI`
- **`EDI`** - (extended) destination index
	- used by opcodes like `movsb` and `movsw` that efficiently copy many bytes of data from the location referenced in `ESI` to the one in `EDI`

***[TODO]** flag register*

### Operations

- mov
- lea
- jmp

- add
- inc
- sub
- dec
- neg
- cmp
- aas
- das
- mul
- div
- not
- and
- test
- or
- xor

- movs
- cmps
- scas
- lods
- stos
- rep
- loop

- call
- ret

- je/jz
- jne/jnz
- jg/jnle
- jl/jnge
- jge/jnl
- jle/jnhg
- ja/jnbe
- jb/jnae
- jae/jnb
- jbe/jna
- jc
- jnc
- jo
- jno
- js
- jns
- jp
- jnp

- int

- xchg
- push
- pop
- lahf
- pushf
- popf

- out
- in
