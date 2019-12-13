[SYS1] Systemes d'exploitation (7)
===

## Assembleur x86

**ISA (Instruction Set Architecture)** : 
- Registres
- Jeu d'instructions
	- Une instruction fait entre 1 et 15 bytes

++Bytecode (32 bits)++
|OPcode|rD|rS1|rS2|
|:---:|:---:|:---:|:---:|

|OPcode|rD|immediat (imm)|
|:---:|:---:|:---:|

++Langage assembleur++ : 

```
add r2, r3, r4
r2 <- r3 + r4
```

```
mov r3, $1 // r3 <- 1
```

Langage machine : Bytecode
Assembleur : Representation texte du bytecode

S.c $\overset{ec}\to$ .S $\overset{as}\to$ bytecode (ELF .O)

### Architectures

- **CISC** : 
	- Complex Instruction Set 
	- $\to$ x86
- **RISC** : 
	- Reduced Instruction Set
	- $\to$ MIPS
	- $\to$ ARM

> CISC moderne est implem (pour certains cas) avec un coeur RISC et un layer de traductiom

**Delay Slot**

```
jmp $abc
add r1, r2, r3
```

Sur RISC, le CPU execute les instructions 2 par 2 -> besoin d'un *nop* apres les JMP

```
jmp $abc
nop
add r1, r2, r3
```

### Instructions

- **Arithmetiques** : add, mul, ...
- **Logiques** : or | and | shift
- **Transfert**: mov, ...
- **Comparaison**: cmp %rax, $0
- **Branchement**: jmp jcc 

> cc (ex: jcc) est un type de comparaison qui depend des flags de l'operation precedente

> Certaines instructions sont du sucre et n'existent pas telles quelles dans le bytecode

### Registres

- %RAX
- %RBX
- %RCX
- %RDX
- %RSI
- %RDI
- %R8 -> R15
- %RSP : stack pointer
- %RBP : base pointer
- %RIP : instruction pointer
- %eflags
    - N negatif
    - Z zero
    - C carry
    - O overflow

```c=
if (a != 0)
	block A
else
	block B
```

```asm=
    cmp $0, %rax
    jne A
	    block A
    jmp.E
A:  block A
E:
```

```
mov $0, %rax
// %rax <- 0
```
:::info
mov: **mnemonique**
$0 et %rax: **operandes**
%xxx: **registre**
$xxx: **immediat**
xxx: **addresse**
:::