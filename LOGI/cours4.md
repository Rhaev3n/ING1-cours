[LOGI] Logique du premier ordre (4)
===

## Langages du premier ordre (Relationnels)

### Nouveaux connecteurs logiques 

- **Quantificateurs** : $\forall$, $\exists$
- $\mathcal{V}$ est a present constitue de minuscules


**Partie specifique** : On note $\mathcal{L}$ la donnee de symboles dits specifiques 
- Symboles dits de constante $\mathcal{C}_1, \mathcal{C}_2, ..., \mathcal{C}_k$ (arite 0)
- Symboles de fonctions munis d'un nombre d'arguments $f_1, f_2, ..., f_k$ avec nb d'args respectifs $a_1, a_2, ..., a_k$ (qui sont des entiers naifs)
> Ou nb d'arguments = **Meta-variables** et fonctions = **symboles**
- Symboles de relations munis d'arites $R_1, R_2, ..., R_n$ avec arites respectives $r_1, r_2, ..., r_n$

++Vocabulaire++ : 

Si R est une relation d'arite $n+1$ verifiant $R(x_1 ... x_n\ y)$ est valide $\implies$ y est unique
$\Rightarrow$ On dira alors que R est **fonctionnelle**

++Notation++ : On ecrira alors $y = f_R(x_1 ... x_n)$ au lieu de $R (x_1...x_n\ y)$
> Toute fonction peut etre vue comme une relation (syntaxiquement)

### Construction inductive de $F_1(\mathscr{L})$
(Formules du premier ordre du langage $\mathscr{L}$)

- Termes de $\mathscr{L}$
    - **Atomes** : tout symbole de variable ou de constante
    - **Constructeur** : Si $r_1 ... r_{a_i}$ sont des termes alors $f\ f_1 ... f_{a_i}$ est un terme si $a_i$ est le nombre d'arguments de $f$
    - **Arret $\omega$**

++Exemples++ : 
$\mathscr{L}_{Ari} = \{0; 1; +; \times; \nearrow; \equiv$ \} (0, 0, f 2, f 2, f 1, rel 2)

Termes : (ok)
- 0 atomique
- n atomique
- + 10 (1 + 0)
- $times + 11 x$ ((1 + 1) x $x$)
> **NB**: polonais

### Algo de verif de construction de termes de $F_1(\mathscr{L})$

**Entree** : $f = \omega_1 ..... \omega_n$ ($\omega_i$ : symbole)
$\mathcal{v} : \omega \to \begin{cases}ar(\omega) - 1 \\ - \infty si \omega: (ni\ constante,\ ni\ var,\ ni\ fonction)\end{cases}$

**Process** : $S_n = \sum_{}^{} \mathcal{v}(\omega_i); k = 1 a n$

**Accept**: ssi $S_k = -1 \land k = n$

++Exemple++

||$\times + 11 x$|
|:---:|:---:|
|$\mathcal{v_i}$|1 1 -1 -1 -1|
|$\sum$|1 2 1 0 -1|

### Formules

**Atomes** : $\top \bot$ sont des formules pour chaque $R$ d'arite $r;\ si\ r_1 ... r_r$ sont des termes de $F_1(\mathscr{L})$ alors $R\ f_1 ... f_n$ est une formule atomique

**Construction** : [connections logiques de $F_0$] si $\phi, \psi$ formules de $F_1(\mathscr{L})$ alors $\phi \land \psi,\ \ \phi \lor \psi,\ \ \phi \implies \psi,\ \ \phi \iff \psi\ ou\ \lnot \phi$ sont encore des formules de $F_1(\mathscr{L})$
De plus ???

**Arret** $\omega$

++Exemple++ (Ari) : 
$T \implies \forall x\ \ 1+1 \equiv x$
$\exists y \nearrow y \equiv 0 \iff \forall x 1 + x \equiv y$
En polonais $\forall y\ \equiv \nearrow y\ 0\ \ \  \forall x \equiv + 1x\ y$

### Statuts des variables

**Ocurrence** : apparition d'un symbole donne
$1 + 1 \equiv x \land\ \ y + 0 \equiv x \times 1$

$nb\ occ\ x: 3$ et $nb\ occ\ x: 2$ admet ???
$nb\ occ\ x: 0$ n'admet pas 

**Ocurrences libres** : Hors champ de quantification
> [hors champ] $\forall x$ [champ de quanditication de "x"]

++En polonais++ : $\iff \forall  x y x 0\ \ \ \exists x \implies + 1 1 \equiv x\ \equiv x y$

**Symbole de var quantifie** : chaque occ dams le champ de quandification
**Symbole de var lie**

**Formule close** : tous les symboles de variables qui admettent une occurrence sont entierement quantifies ()

++Exemple++ : $\forall x\ \exists y \equiv 1 \times xy \to \forall x \exists y\ \ xxy \equiv 1$

Demonstration avec $F_1(\mathscr{L})$
Regles du calcul des sequants des LK1
Autres regles LK1 (pas LK0): gestion des quantifs

$\frac{C \vdash \phi(x)}{C \vdash \forall x \phi(x)}\forall-intro$

**Notation** : $\phi[x]$ signifie que x a occurences libres dans $\phi$
$\phi[f/x]$