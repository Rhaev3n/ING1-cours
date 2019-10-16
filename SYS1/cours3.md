[SYS1] Systemes d'exploitation (3)
===

## Mapping memoire

**void \*mmap(void \*addr, size_t sz, int prot, int flag, int fd, off_t offset);** : Faire des mapping memoire
- ++addr++ = NULL : Le kernel choisit lui-meme ou creet le mapping (le plus portable)
- ++size++ : Taille quelconque realignee au multiple de 4096 (Taille de page par defaut du systeme) suivant
- ++prot++ : RD | WR
- ++offset++ : Doit etre aligne. Ecrit le fichier fd a partir de l'offset dans la page 
- ++flag++ : MAP_PRIVATE (copie privee) | MAP_SHARED (changements propages sur le file system) | MAP_ANONYMOUS (non POSIX, alloue de la memoire et non un fichier)
- ++fd++ : -1 avec MAP_ANONYMOUS
- ++Valeur de retour++ : MAP_FAILED ((void*)-1)

> /dev/zero : En ecriture n'ecrit rien, en lecture lit les n bytes demandes, tous a 0

**munmap(addr, sz)**;
**mprotect(addr, sz, prot)**; : Change les permissions sur les mappings

**void \*mremap(void \*addr, size_t old_size, size_t new_size, int flag, ... /\*void \*new_addr\*/);** : Etendre ou reduire un mapping existant

> Garde la memoire physique, cree une nouvelle zone d'addresse virtuelle qui pointe sur l'ancien bloc de memoire physique

:::info
On veut pouvoir allouer de la memoire dans la page (*allocateur a grains fins*)
:::

## Algorithmes d'allocation

### First fit

- On alloue un bloc (avec des metadonnees associees : premier bloc alloue de la page, pointeur vers page suivante, taille de la page)
- Dans ce bloc, on alloue d'autres blocs (avec metadonnees associees : bloc libre?, taille du bloc, bloc suivant, bloc precedent), doublement chaines entre eux

:::info
Probleme : Recherche de place libre et suppression : complexite lineaire
:::
:::info
Probleme : Grosses metadonnees
:::
++Solution++ : On alloue plusieurs pages, contenant chacune des allocations de taille fixe identique (**Buckets**)


### Page begin
Retrouver le debut de la page quand on a un pointeur random sur un bloc random dans cette page : 
- Realigner le pointeur sur la taille de la page (on redesend au multiple de 4096 (PAGE_SIZE) inferieur)

> Cast en uintptr_t
> addr & 0xFFFFF000

### Metadonnees

On stocke les metadonnees a l'exterieur, qui pointe sur notre bloc de taille 4K, et sur la prochaine metadonnee
> Pas de temps constant sur la suppression

-> On utilise une hashmap