[MOB1] Approches Objet de la Programmation (1)
===

[// slides 00_introduction](https://www.lrde.epita.fr/~didier/lectures/aop/aop_00_introduction.pdf)

# Contexte

### Programmation imperative

**Instruction** : ordre destine a produire un effet de bord (modification de notre environnement)
> L'ordre d'execution est important

### Programmation procedurale

> C'est une extension logique de la programmation impertive

Factorisation d'une sequence d'instruction souvent repetee en **procedure** que l'on peut appeler autant de fois que l'on veut

### Origine

Ces paradigmes viennent du modele de **Von Neumann** (hardware des ordinateurs)
Fusion du calculateur de Pascal et des programmes sur cartes perforees de Charles Babbage
- Manipulation de registres
- Echanges avec la memoire

> Pas d'avancee technologique majeure sur le materiel depuis 1941

### Deux familles de langages

1. **Langage bas-niveau** (bottom-up) : on rajoute des concepts par dessus des concepts deja exisatnts (instructions assembleurs, etc) >> 80% des langages
2. **Langage haut-niveau** (top-down) : on part d'une idee de nouveau concept complexe et qui ne ressemble a rien d'existant

> L'approche imperative, procedurale, orientee objet est bas niveau

# Paradigmes de programmation

### Notion de paradigme

**Paragigme**
- Maniere de s'exprimer
- Affecte l'expressivite du langage
- Affecte la maniere de penser

**Turing-Completude** : nos langages de prog ont tous la meme puissance d'expression

### Specificites d'autres paradigmes

##### Fonctionnel
map (+4) [1, 2, 3, 4, 5] -- [5, 6, 7, 8, 9]