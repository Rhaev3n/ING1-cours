[SYS1] Systemes d'exploitation (1)
===

<span style="color:#d10014">**Systeme d'exploitation**</span>
- Gestion des ressources pour les programmes
- Fournir des interfaces et des abstractions pour les programmes utilisateurs

## Architecture d'un ordinateur

```
CPU
RAM
Dev
Dev
...
```


```sequence
CPU->Controleur memoire: Bus 
Controleur memoire->Dev1 #: Bus
Controleur memoire->Dev2 #: Bus
Controleur memoire->Dev3 #: Bus
```


<span style="color:#d10014">**CPU**</span> : Execute des instructions
- CPU modes
    - *User mode* (ring3)
    - *Supervisor mode* (ring0) : Acces aux registres de controle

<span style="color:#d10014">**Registres**</span> : petites zones de memoire temporaire (8 bytes)
- *Registres generaux*
- *Registres de controle*
    - permettent de configurer le processeur et la machine en general

## Kernel (Noyau de systeme d'exploitation)
- Fournit des interfaces et des abstractions pour les programmes utilisateurs via des **syscalls (appels systeme)**

- Quand on fait on syscall, il y a un **context switch** (avec changement de mode, user -> supervisor)

- Syscalls tres specifiques a l'OS, on n'execute donc pas de syscalls directement mais on utilsie des **wrapper** (la plupart du temps expose par la libc) 

> Le kernel = 1 seul process qui tourne, comment faire pour reprendre la main pendant l'execution des programmes et gerer leur scheduling ?

## Fichiers

**i-node ou inode** : Contient toutes les informations d'un fichier
- *Emplacement* des data
- Date de *creation*, date de *modification*
- *Taille*
- *Permissions*, uid, gid
- Le *type* de fichier
    - regular
    - directory
    - symbolic links
    - devices : char device & block device
    - socket
    - named pipe (FIFO)

> Informations recuperables avec **stat/fstat**

**Numero d'inode** : Adresse qui permet de retrouver le fichier sur le disque

> On se balade dans un directory avec opendir, readddir, closedir

## Comment on execute un programme ?

**Programme** : fichier qui contient du code

**Process** : Un programme chose qui s'execute (la plupart du temps) -> *programme en cours d'execution*

> Sous Linux, on ne sait pas *creer* un nouveau process

**syscall fork()** : duplique le process courant
**syscall wait(), waitpid()** : Attend que le process duplique se termine
**syscall execve()** : Creer un nouvel espace memoire dans le process courant

```c 
pit_t pid = fork();
if (pid < 0)
    err(1, "unable to fork.");

if (pid)
{
    int rc = waitpid(pid/*...*/);
    // error checking/retry/etc
    return;
}

char *argv[] = 
{
    "rm",
    "toto.pyc",
    NULL
};

execvp(argv[0], argv);
err(1, "error"); // if execve is successful, this should not be read
```