[CMP2] Construction des compilateurs (2)
===

# Instruction Selection

## Microprocessors

> Instruction set architecture is the structure of a computer that a machine language programmer (or compiler) must understamd to write a correct (timing independant) program for a machine
> IBM introducing 360

### Instruction Set
**Instruction Set Architecture (ISA)** : Part of processor visible to the programmer
> Savoir quelles sont les operations autorisees sur le microprossesseur

Instruction set specifies :
- Supported operations
- Storage mechanism used
- How to acess storage
- How to communicate program to processor

### cisc
**cisc (Complex Instruction Set Chip)** :
- large number of instructions (100-250)
- 6-8-16 registers

Pros :
- Translation from IR is straightforward
- Smaller assembly code, fewer instructions fetched
Cons :
- Limitied number of registers
- Variable length instruction format
- Complex instructions do not simplify compiler : many clock cycles wasted to find instructions

### risc
**risc (Reduced Instruction Set Chip)** :
- 32 registers
- 3 address code
- Load and store variables: always relative to a register $\implies$ larger code
- 1 instruction = 1 effect

**Pipeline** : overlapping the executrion of several instructions in a pipeline fashion

Decompose instruction treatment in 5 steps :
- Instruction Fetch (IF)
- Instruction Decode (ID)
- Execute (EX)
- Memory Access (MA)
- Write Back (WB)

```
inst1: IF  ID  EX  MA  WB
inst2:     IF  ID  EX  MA  WB
inst3:         IF  ID  EX  MA  WB
inst4:             IF  ID  EX  MA  WB
inst5:                 IF  ID  EX  MA  WB
```
> Que 5 etages dans notre microprocesseur

Data hazard: Instruction depends on result of a previous one still in the pipeline

++Example++ : inst1 write in \$s1 suring WB + read in \$s1 during ID $\implies$ cycle de gel $\implies$ inst2 must be split = delays

```
inst1: IF  ID  EX  MA *WB*
inst2:     IF *ID* EX  MA  WB

```

Cons :
- Fixed length instruction : easier decoding
- Simpler hardware : clock rate\+\+
- Efficient instruction pipeline
Pros :
- Few instructions
- Minimal addressing modes : Load and Store only

++Aujourd'hui++
- Classification pure-risc / pure-cisc obsolete $\implies$ hybrid architectures : X86

## Typical risc : mips

### Registers

|Number|Name|Purpose|
|:---:|:---:|:---:|
|0    |$zero    |    Always 0 (Writes to this register are ignored.)|
|1    |$at|    Reserved by the assembler.|
|2–3    |$v0–$v1|    Expression and function result values.
|4–7    |	$a0–$a3|	Arguments for function calls 1-4
|8–15	|$t0–$t7	|Temporary values (not preserved across calls).
|16–23	|$s0–$s7	|Saved temporary (preserved across calls).
|24–25	|$t8–$t9	|Temporary values (not preserved across calls).
|26–27	|$k0–$k1	|Reserved for use by the OK kernel.
|28	|$gp	|Global pointer – points to the middle of the 64K memory block in the static data segment.
|29	|$sp	|Stack pointer.
|30	|$s8	|Frame pointer.
|31	|$ra	|Return address (used by function call).

### Instructions

> Imm: constante

```
add Rdest, Rsrc1, Src2 (add Rsrc1 + Src2 => store in Rdest)
addi Rdest, Rsrc1, Imm (add Rscr1 + Imm => store in Rdest)
```

### Instruction Control

```
seq Rdest, Rsrc1, Src2 # Set Rdest to 1 if Rsrc1 = Src2, else 0
```

```
b label # Unconditional branch to label
j label # Unconditional jump to label
```

```
beq Rsrc1, Src2, label # branch on equal
bne Rsrc1, Src2, label # branch on not equal
```

## Instruction Selection

> Transform lir code into mips

On suppose qu'on a un nombre illimite de registres $\implies$ lir to mips $\implies$ Allocation des registres

How to translate ``a[i] := x``

![](https://i.imgur.com/LriLNVE.png)
![](https://i.imgur.com/xMybPVW.png)

Choisir la bonne istruction

++Example++ : const 4 peut etre traduit par r <- 4 + 0, r <- 4, r <- 8 - 4

$\implies$ Trouver le pavage le plus optimal d'un arbre : celui qui minimise le nombre de cycles

### Dynamic approach

- Bottom-up strategy

On met la meilleure tuile tout en bas, puis on remonte, etc $\implies$ esperer obtenir un maximum global en ayant ajoute des maximum locaux

### Maximum munch

- Top-down strategy

On commence tout en haut, on met la meilleure tuile, on descend en mettant toujours la meilleure tuile

#### Pattern-matching d'arbre
> Stratego, ...
