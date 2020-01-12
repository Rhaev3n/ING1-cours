[PROBA] Probabilites discretes (1)
===

# Experiences aleatoires et evenements

### ==Definition (Experience aleatoire)==

Une experience est qualifiee d'**aleatoire** si on ne peut prevoir par avance son resultat et si repetee dans des conditions identiques elle peut donner lieu a des resultats differents.

On représente le résulat d'une experience par un élément $\omega \in \Omega$.

- On appelle $\Omega$ l'**univers** (l'ensemble des resultats possibles)
- On appelle $\omega$ **un resultat** de cette experience

### Exemples

++Exemple 1++ : 

On jete un de cubique equilibre, les faces sont numerotees de 1 a 6
On lit les numeros apparus sur la face superieure 

$\Omega = \{1, 2, ... 6\} =  [[1,6]]$

++Exemple 2++ : 

On jete deux fois un de cubique et on note les numeros obtenus : 
$\Omega = [[1,6]]^2 = \{ (i,j) \begin{cases}i \in [[1,6]] \\ j \in [[1,6]]\end{cases}\}$

> $\Omega$ n'est pas deduit de l'experience de maniere unique

On s'interesse a la somme des points $i+j$, on peut definir $\Omega' = \{2, ..., 12 \}$

### ==Definition (Experience aleatoire)==

Lorsqu'on effectue une experience aleatoire, certains faits lies a cette experience peuvent se produire ou non. On les appelle **evenements**.

++Exemple 1++ : 

Soit $A_1$: "Le numero obtenu est pair"
$A_1$ est realise si $\omega \in \{2, 4, 6\}$
$A_1 = \{2, 4, 6\}$

$A_2$ : "Le numero obtenu est superieur a 4"

$A_2 = \{4, 5, 6\}$

$A_1$ et $A_2 \in \mathcal{P}(\Omega)$ (ensemble des parties de $\Omega$)

### ==Definition (Evenement impossible, contraires, incompatibles)==

- Un evenement **impossible** est represente par $\varnothing$

$\Omega$ est realise si $\omega \in \{1, 2, ..., 6\}$
$\Omega$ : evenement certain

- $\bar{A}$: Evenement **contraire** de A

Soient $A, B$ deux evenements
- $A$ et $B$ sont **incompatibles** ssi $A \cap B = \varnothing$

- A chaque evenement $A$ correspond son contraire $\overline{A} = C^{A}_{\Omega}$ (**complementaire** de $A$)

++Exemple 2++ : 

$\Omega = [[1,6]]^2$

Soit $B$ : "La somme des numeros obtenus est 6"
$B = \{(1,5), (2, 4), (3, 3), (4, 2), (5, 1)\}$

$B \in \mathcal{P}(\Omega) = [[1,6]]^2$
$\mathcal{P}(\Omega)$: ensemble de tous les evenements ($\omega$ fini)

## Espace probabilise fini

Soit $\Omega$ un ensemble fini
$\mathcal{P}(\Omega)$ ensemble des parties de $\Omega$

Le couple $(\Omega, \mathcal{P}(\Omega))$ est appele **espace probabilisable**

$\{\omega\}$ evenement elementaire, par definition $\omega \in \Omega$

### ==Definition (Probabilite)==

On appelle **probabilite** definie sur $(\Omega, \mathcal{P}(\Omega))$ toute application : 

$\mathbb{P}: \mathcal{P}(\Omega) \to [0,1]$
$\ \ \ \ \ \ \ \ \ \ \ \ A \to \mathbb{P}(A)$

Verifiant les axiomes :

- $\mathcal{P}(\Omega) = 1$
- $\forall (A, B) \in \mathcal{P}^2(\Omega) \ A \cap B = \varnothing$
- $P(A \cup B) = P(A) + P(B)$

$(\Omega, \mathcal{P}(\Omega), P)$ : **espace probabilise fini**
> $\Omega$ univers  
> $\mathcal{P}(\Omega)$ tribu  
> $P$ proba

------------------
### ==Proprietes elementaires==
1. $P(\overline{A}) = 1 - P(A)  , \ \ P(\varnothing) = 0$
2. $P(A - B) = P(A) - P(A \cap B)$
3. Si $A \subset B \implies P(A) \leq P(B)$
4. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$

> $A- B = \{ x \in A\ et\ x \notin B \}$

### Demonstrations 

1. 
$A = (A - B) \cup (A \cap B)$
$(A - B) \cap (A \cap B) = \varnothing$

2. 
$P(A) = P(A-B) + P(A \cap B)$
$P(A - B) = P(A) - P(A \cap B)$

3. 
$A \subset B\ \ A \cap B = A$
$B = (B-A) \cup (A \cap B)$
$P(B) = P(B-A) + P(A \cap B)$
$P(B) = P(B-A) + P(A) \geq P(A)$

4. 
$A \cap B = B \cap (A - B)\ \ \ (B \cap (A-B) = \varnothing)$
$P(A \cup B) = P(B) - P(A - B) = P(B) + P(A) - P(A \cap B)$

-----------------------
## Formule de Poincare

$(\Omega, \mathcal{P}(\Omega), P)$ espace probabilise fini
Pour toute famille d'evenements $(B_k)$

$\begin{align}P(\bigcup_{k=1}^nB_k) = \sum_{k=1}^n(-1)^{k+1} \sum_{1 \leq i_1 < i_2 < ... < i_k \leq n} P(\bigcap_{j=1}^kB_{ij})\end{align} \ \ \ (1 \leq k \leq n)$

**Remarque**

Si $(B_k)$ sont incompatibles 2 a 2, $B_i \cap B_j \neq 0,\ i \neq j$

$\begin{align}P(\bigcup_{k=1}^{n} B_k)=\sum_{k=1}^{n}P(B_k)\end{align}$

### ==Theoreme==

Soit $\Omega = \{ \omega_1, \omega_2, ..., \omega_n \}$
$P$ est une probabilite sur $\Omega$ telle que $P_i = P(\{\omega_i\}) \forall i \in [[1,n]]$

On a alors $\begin{cases}(1)\ P_i \geq 0\ \ \ \forall i \in [[1,n]] \\ (2)\ \sum_{i=1}^nP_i = 1\end{cases}$

**Reciproque**

Si $(P_i)_{1 \leq i \leq n}$ est une suite de reels verifiant (1) et (2) 
Alors il existe une unique probabilite $P$ sur $\Omega$ telle que :

$P(\{\omega_i\}) = P_i \ \ \forall i$ et $P(A) = \sum_{i, \omega_i \in A}^{}P_i\ \ \forall A \in \mathcal{P}(\Omega)$

---
#### Demonstration

Si $P$ est une probabilite sur $\Omega$

$P_i = P(\{\omega_i\}) \geq 0$ et $\sum_{i=1}^n P_i = \sum_{i=1}^nP(\{\omega_i\}) = 1$

Or $\Omega = \cap_{i=1}^n\{\omega_i\}$
$P(\Omega) = \sum_{i=1}^n P(\{\omega_i\}) = \sum_{i=1}^nP_i = 1$

> $P(\Omega) = 1$

#### Reciproque 

Supposons (1) et (2) verifiees

Soit $P$ l'application : 
$\begin{align}P(A) &= \sum_{i, \omega_i \in A}^{}P(\{\omega_i\}) \sum_{i, \omega_i \in A}P_i\end{align}$

$\forall A \in \mathcal{P}(\Omega)$: $A = \cup_{i, \omega_i \in A}\omega_i$

:::info
Montrons que P est une probabilite
:::

$0 \leq P(A) = \sum_{i, \omega_i \in A}P_i \leq \sum_{i=1}^nP_i = 1$
$1 \leq P(A) \leq 1$

$P(\Omega) = \sum_{i=1}^{n}P(\{\omega_i\}) = \sum_{i=1}^nP_i = 1$

Si $A$ et $B$ sont deux evenements incompatibles, $A \cap B = \varnothing$
$A \cup B = \cup_{i, \omega_i\ A \cup B} \{\omega_i\} = \cup_{i, \omega_i \in A}\{\omega_i\} \cup_{i, \omega_i \in B} \{\omega_i\}$

$P(A \cup B) = P(\cup_{i, \omega_i \in A \cup B}\{\omega_i\}) = \sum_{i, \omega_i \in A}P(\{\omega_i\}) + \sum_{i, \omega_i \in B} P(\{\omega_i\}) = P(A) + P(B)$

P est une probabilite


-----
### ==Definition (Equiprobabilite)==

On dit qu'il y a **equiprobabilite** lorsque les probabilites de tous les evenements elementaires sont egales. On dit que $P$ est une probabilite **uniforme** sur $(\Omega, \mathcal{P}(\Omega))$.

$\begin{align}\forall A \in \mathcal{P}(\Omega), P(A) = \frac{Card\ A}{Card\ \Omega} \end{align}$

> Autrement dit P(A) = mombre de cas favorables / nombre de cas possibles

#### Demonstration 

En effet, $\exists \lambda \in [0, 1]/ P_i = \lambda\ \ \forall i \in [[1,n]],\ \ p_i = P(\{\omega_i\})$

$\sum_{i=1}^np_i = 1 \implies n\lambda = 1 \implies \lambda = 1/n$

$\begin{align}\forall A \in \mathcal{P}(\Omega) P(A) = \sum_{i, \omega_i \in A}P_i = \sum_{i, \omega_i \in A}\lambda = \lambda \sum_{i, \omega_i \in A}1 = \lambda\ Card A = \frac{Card A}{Card \Omega}\end{align}$

---
### Application

++Exercice 1++ : 

On considere une urne contenant 5 boules blanches et 5 noires. Les boules blanches sont numerotees de 1 a 5  et les noires egalement.

Decrire l'univers associe a chacune des experiences suivantes : 
1. On tire une a une 3 boules de l'urne en y remettant la boule tiree a chaque fois
2. On tire une a une 3 boules de l'urne sans remise
3. On tire une a une toutes les boules de l'urne sans les y remettre apres chaque tirage jusqu'a ce qu'il n'y ait plus de boules

Soit $U = \begin{cases}B_1, B_2, ..., B_5\\N_1, N_2, ..., N_5\end{cases}$

1. $\Omega = U^3 = \{(a,b,c)\ \ a \in U, b \in U, c \in U\}$
$Card\ \Omega = 10^3$

2. $\Omega = \{(a, b, c) \in U^3\ \ a \neq b, b \neq c, a \neq c\}$
{3-listes a elements $\neq$}
$Card\ \Omega = A_{10}^3 = \frac{10!}{7!}$

3. $\Omega =$ {permutations de $[[1,10]] \to [[1,10]]$}
$Card\ \Omega = 10!$