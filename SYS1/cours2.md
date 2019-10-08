[SYS1] Systemes d'exploitation (2)
===

## Espace d'adressage
En demandant une adresse, l'espace alloue est constitue de zones de taille fixe (4k)

> Controlleur memoire + devices definit un espace d'adressage

- ==Espace d'adressage== physique de la machine : 

|4G||
|:--:|:--:|
||ROM|
|||
||Dev|
|||
||RAM|
||Video|
|640k|RAM|
|**0**||

> Memoire video : quand on y ecrit un device dispay le contenu sur un ecran

### Adressage avec segments
**Segment** : Quand on decrit une zone, on decrit une **base** (l'adresse) et une **limite** (taille, offset de la derniere adresse valide = taille - 1)
Dans le processeur, un registre permet de stocker le segment courant 

:::warning
Modele bien pourri
:::

||
|:--:|
|CODE|
|^|
|Data|

> On ecrit les data en avancant via le segment dans une zone lineaire, on va donc finir par ecrire sur une autre zone (Data va finir par ecrire sur la zone du code)

## Virtualisation de memoire

|Adressage virtuel|Adressage physique|
|:--:|:---:|
||P1|
|V1||
|V2||
||P2|

> Ou V1 pointe vers P1 et V2 pointe vers P2

Aussi appele **pagination** : 
- On decoupe notre espace d'adressage en zone (appelees pages) de globalement ==4Kb==
- **Adresse de la page** encodee sur ==20bits==

> Le processeur fait le dereferencement en passant par la table de traduction (On lui donne l'adresse virtuelle et elle l'associe a l'adresse physique)

**MMU** : Memory Managment Unit (puce qui s'occupe de faire la traduction)

---
En plus de stocker l'adresse des adresses physiques, la table de traduction doit aussi stocker des **permissions** 

|@V|@Phy|flag|
|:--:|:--:|:--:|
||||

> Comment encoder cette table ?

|||
|:--:|:--:|
||4M|
|@Px0|@Phy 20b \| flags|

Memoire doit etre contigue en memoire physique > chiant ca
-> On utilise une srtucture arborescente = un **BTree**
- Node : fait la taille d'une page
- Pointe soit sur l'adresse de la page suivante soit sur de la data

|4|
|:--:|
||
|p|
||
||

p pointe vers
|4|
|:--:|
||
||
||
|d|

![](https://i.imgur.com/G8Qbiov.png)
