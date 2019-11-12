[SYS1] Systemes d'exploitations (5)
===

# Filesystem

**Disques** : 
- READ
- WRITE
- SYNC

**Bloc** : 
- size = $\begin{cases} 512\ (HDD\ historiquement) \\ 2K\ (CDrom) \\ 4K\ (HDD\ moderne)\end{cases}$
- address = $\begin{cases}CHS\ (cylinder\ head\ sector) \\ LBA\ (logical\ block\ address) \end{cases}$


**LBA** : le disque connait sa propre topologie
**CHS** (plus utilise) :
![](https://i.imgur.com/hTe6fwF.png)


Aller plus vite sur un disque : On met du cache devant (on gagne surtout en ecriture)

- *HDD* : Amenagement pour que la memoire soit contigue
- *SSD* : Lecture / Ecriture instantannees et ne dependent pas de la place sur le disque

**LRU (Least Recently Used)** : Algorithme de gestion de cache

## Structure de file system

**Inode** : data structure qui represente le file system

1 bloc = Metadonnees et contenu

**Struct Superblock**
- Index : BTree \<InodeNb>
- Root Inode

> Superblock sur le 16eme bloc (endroit fixe sur le disque) : il faut de la place sur le disque avant pour pouvoir boot

On utilise des magic number en debut de structure et un checksum permettent d'identifier le type de structure

![](https://i.imgur.com/Fqby3Rk.png)

## Exemple

**FAT32 (File Allocation Table)** : L'exemple du file system stupide

||
|:---:|
|SB (Super block)|
|FAT|

> FAT : gros tableau contenant plusieurs listes chainees
> FAT : une corruption corromp toutes les donnees 