[SYS1] Systemes d'exploitation (9)
===

- link
- ELF format
- Execution du programme

```
objdump -d program_name
readelf
```

```c=
int a = 12;

int foo()
{
    return 14;
}

int calc(int a, int b);

int main()
{
    printf("%d\n", calc(foo(), a));
}
```

```c=
int calc(int a, int b)
{
    int c;
    
    c = a + b;
    return c;
}
```

```
// arguments: a=%edi, b=%esi
// return value: %eax
// stack:
//    -8(%rbp)    a
//    -16(%rbp)   b
//    -24(%rbp)   c

calc:
    push %rtp
    mov %rsp, %rbp
    sub $24, %rsp
    
    movl %edi, -8(%rbp)
    movl %esi, -16(%rbp)
    movl g, -24(%rbp)
    
    // addl a, c
    addl -8(%rbp), %edi
    addl %edi, -24(%rbp)
    // addl b, c
    addl -16(%rbp), %edi
    addl %edi. -24(%rbp)
    
    addl a, c
    addl b, c
    
    movl -24(%rbp), %eax
    leave
    ret
```

### Relocation

**lea** : Load Effective Address

Calcule une addresse a la place de dereferencer

```a
mov %rax, %rdx // move la data
lea %rax, %rdx // met l'addresse calculee dans %rdx

mov -0x10(%rbp), %rdx   %rdx <- local;
lea -0x10(%rbp), %rdx   %rdx <- &local;

lea(%rax, %rax, 2), %rdx    %rdx = %rax * 3;
```

### ELF

**Elf** : Extensible Loading Format

- Executable
- Relocatable (.o)
- Dynamiques (.so, etc)
- Coredump (image memoire d'un programme stocke sur le disque)
> Ecrit le contenu de la memoire + registres d'un fichier dans un fichier, pratique pour le debug

++2 utilisations de l'ELF++ : 
- Statique : Compilation et edition de lien
- Dynamique : Chargement et execution d'un programme

Commence par un en-tete

#### Header ELF
> readelf -h program_name

++2 tables++ : 
- Table des **sections** : partie statique
- Table des **segments** (program headers) : partie dynamique

> readelf -l program_name : program headers

LOAD : Indique quoi charger en memoire, et ou (MemSiz)
||
|:---:|
|AUXV|
|ENVP|
|ARGV|
|Argc|
|RPS$\nearrow$|

> readelf -S 42sh : sections

**Linker** : prend les .o et prend les sections bout a bout

> readelf -s program_name : symtab

### Ecrire un fichier assembleur

.s : fichier assembleur (pour la machine)
.S : fichier assembleur avec directives de preprocesseur (pour les humains)

```c=
int calc(int a, int b)
{
    int c;
    c = a + b;
    return c;
}
```

```c
    .section text
    
    .global calc // calc est une fonction globale
    .type calc, @function
    
calc:
    xor %eax, %eax
    // movl g, %eax essaye d'acceder a addresse absolue
    movl g(%rip), %eax
    addl %esi, %eax
    addl %edi, %eax
    //ret
    .byte 0xc3
.Lend_calc:
    
    .size calc, .Lend_calc - calc // on declare la taille de la fonction
    // .size calc, . - calc avec . l'addresse courante
    
    .section .data
    
    .type g, @object
    // .global g si variable non statique
g:
    .long 12
    .size g, . - g
```
> Convention gcc

### Syscall en assembleur

```shell=
#!/bin/sh

set -e

gcc -c empty.S -o empty.o
ld -o empty empty.o
```

++empty.S++ : 
```c 
#include <asm/unistd.h>

    .global _start
    
_start:
mov $1, %rdi
    call _exit
    
_exit:
    // mov $60, %rax ou 60 = NR_exit
    mov $__NR_exit, %rax
    syscall
    ret
```

> /udr/inclues/asm/unistd_64 : numeros des syscalls

Appeler un syscall
![](https://i.imgur.com/AeYzTFK.png)


Passer des arguments au syscall
![](https://i.imgur.com/Rhv0FO6.png)
