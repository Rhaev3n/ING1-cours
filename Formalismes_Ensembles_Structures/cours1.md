[FES] Formalismes, Ensembles et Structure (1)
===

> Vocabulaire relatif aux ensembles structures et aux relations

## I. Ensembles

### 1.1 Ensembles et elements

- La notion d'ensemble est une notion premiere que nous ne cherchons pas a definir
> Collection d'objets

- Disons seulement qu'un **ensemble** est un objet auquel peut appartenir ou ne pas appartenir un autre objet. On note : 
$$\begin{cases}
x \in E \\
x \notin E
\end{cases}$$

-------------
Quand on definit un ensemble il faut faire attention aux contradictions
> cf Paradoxe de Russel

Pour echapper a ces contradictions > il faut respecter des regles precises pour definir des ensembles
Certains ensembles definis de maniere **axiomatique** (par exemple $\mathbb{N}$)
D'autres peuvent etre **construits** a partir de ceux la avec des operations convenables (par exemple $\mathbb{Z}$)

### 1.2 Sous-ensembles


==**Definition (Sous-ensemble)**==
Soient E et F 2 ensembles. On dit que F est inclus dans E si tout element de F est element de E.
On note $F \in E$. On dit aussi que F est un **sous-ensemble** ou une **partie** de E. 

> Exemple : $\mathbb{N} \in \mathbb{Z}$

Deux ensembles sont **egaux** ssi ils ont exactement les memes elements (si chacun est inclus dans l'autre)
$$E = F \iff (E \in F\ et\ F \subset E)$$

Un **sous ensemble** de E peut etre defini comme ensemble des elements de E verifiant une certaine proposition

> Exemple $\mathbb{R}_+ = {x \in \mathbb{R}, x \geq 0}$
> Exercice : $E = {1, 2, 4, 6, 10}\ et\ F = {x \in E, x \leq 4}$

En particulier, si cette propositione st impossible on obtient l'ensemble vide qui doit etre considere comme un sous-ensemble de nimporte quel ensemble. On le note $\varnothing$


Un ensemble qui possede un unique element est appele singleton. Il ne faut pas confondre l'element x et le singleton ${x}$. On peut ecrite : $2 \in N\ ou\ {2} \subset \mathbb{N}$ mais pas l'inverse

### 1.3 Produit cartesien

Soit E et F deux ensembles. On peut construire un nouvel ensemble appele **produit cartesien** de E et F, note $E \times F$, dont les elements sont les couples formes d'un element de E et d'un element de F
$$(x, y) \in E \times F \iff (x \in E\ et\ y \in F)$$

Si $E = F$ on note $E \times E = E^2,\ E \times E \times E = E^3$ etc

> Exemple : $(1, \sqrt{2}) \in \mathbb{R}$ L'ensemble $\mathbb{R}^2$ peut etre identifie a un plan muni d'un repere cartesien

### 1.4 Quantificateurs

- Soit $P(x)$ une proposition dependant d'un element $x$ d'un certain ensemble E
La proposition $\forall x \in E, P(x)$ signifie que tout element $x$ de E verifie la proposition $P(x)$.
$$\forall x \in E, P(x) \iff {x \in E, P(x)} = E$$

- La proposition $\exists x \in E$, $P(x)$ signifie qu'il existe au moins un element $x$ de E qui verifie la proposition $P(x)$
$$\exists x \in E, P(x) \iff {x \in E, P(x)} \neq \varnothing$$

### 1.5 Negation d'une proposition

==**Definition (Negation d'une proposition)**==
Soit P une proposition qui est vraie (1) ou fausse (0).
On note $\overline P$ la **negation** de la proposition P, c-a-d la proposition qui est vraie si P est fausse, et faussi si P est vraie. Notons ue
$$\overline{P\ ou\ Q} \iff \overline P\ et\ \overline Q$$

$$\overline{P\ et\ Q} \iff \overline P\ ou\ \overline Q$$

:::info
"et" se note aussi $\land$
"ou" se note aussi $\lor$
:::

D'autre part, comme l'implication $P \Rightarrow Q$ possede la table de verite

|P |Q |$P \Rightarrow Q$|
|:-:|:--:|:-:|
|V |V |V|
|V| F| F|
|F| V| V|
|F| F| V|

la proposition $P \Rightarrow Q$ est logiquement equivalente a $\overline P$ ou $Q$ dans le cadre de la logique classique

- La **negation** de $P \Rightarrow Q$ s'ecrit $\overline{P \Rightarrow Q} \iff (P\ et\ \overline Q)$
- Notons d'ailleurs que $(P \Rightarrow Q) \iff (\overline Q \Rightarrow \overline P)$. C'est la **contraposee** de l'implication, parfois plus facile a demontrer que l'implication elle meme
- C'est le principe du **raisonnement par l'absurde** : suppose le contraire de ce que l'on veut demontrer, et on cherche une contradiction de l'une des hypotheses 

### 1.6 Negation d'une proposition avec des quantificateurs

- La proposition $\forall x \in E$ P(x) signifie que tous les elements de E verifient la propriete $P(x)$, sa **negation** est qu'il existe au moins un qui ne la verifie pas
$$\overline{\forall x \in E, P(x)} \iff  \exists x \in E, \overline{P(x)}$$

- La proposition $\exists x \in E$ P(x) signifie que tous les elements de E verifient la propriete $P(x)$, sa **negation** est qu'aucun d'entre eux ne la verifie : 
$$\overline{\exists x \in E, P(x)} \iff  \forall x \in E, \overline{P(x)}$$

> ex : $\exists m \in R \exists M \in R \forall x \in R f(x) \geq m\ et\ f(x) \leq M$
> $\forall m \in R \forall M \in R \exists x \in R f(x) \geq m\ ou\ f(x) \leq M$

## 2 Ensemble des parties d'un ensemble 

### 2.1 Ensemble $\mathcal{P}(E)$

- Tous les sous-emsembles E constituent un nouvel ensemble appele **ensemble des parties de E** et note $\mathcal{P}(E)$
$$A \in \mathcal{P}(E) \iff A \subset E$$

>Ex si $E = \{a, b, c\}$ alors
> $\mathcal{P}(E) = \{\varnothing, \{a\}, \{b\}, \{c\}, \{a, b\}, \{a, c\}, \{b, c\}, E\}$

**Remarque** : L'ensemble $\mathcal{P}(\varnothing)$ n'est pas vide puisqu'il contient l'element $\varnothing$. C'est un singleton $\mathcal{P}(\varnothing) = {\varnothing}$

### 2.2 Operations dans $\mathcal{P}(E)$

Soit E un ensemble et A et B deux parties de E. On peut definir de nouvelles parties de E par les operations suivantes : 
- ==**Complementaire**== : $C_EA$ est l'ensemble des elements de E qui n'appartiennent pas a A (eq ensembliste de la negation)
> ie $\forall x \in E, x \in C_EA \iff x \notin E$
> ex $C_{\mathbb{R}}{0} = \mathbb{R}^*$

- ==**Intersection**== : $A \cap B$ est l'ensemble des elements appartenant a la fois a A et a B (eq ensembliste de la conjonction)
> ie $\forall x \in E, x \in A \cap B \iff x \in A\ et\ x \in B$
> ex $\mathbb{R}_+ \cap \mathbb{R}_- = {0}$

- ==**Reunion**== : $A \cup B$ est l'ensemble des elements a A eou a B (eq ensembliste de la disjonction)
> ie $\forall x \in E, x \in A \cup B \iff x \in A\ ou\ x \in B$
> ex $\mathbb{R}_+ \cup \mathbb{R}_- = \mathbb{R}$

- ==**Difference**== : A \\ B ensemble des elements de E appartenant a A mais pas a B (eq negation de l'implication ou encore "prive de ")
> ie $A \setminus B = A \cap C_EB$
>ex $\mathbb{R}_+ \setminus \mathbb{R}_- = \mathbb{R}_+^*$

- ==**Difference symetrique**== $A \triangle B$ ensemble des elements de E qui appartiennebt soit a A soit a B mais pas aux deux a la fois  (eq de la disjonction exclusive)
> ie $A \triangle B = (A \cup B) \setminus (A \cap B)$
> ex $\mathbb{R}_+ \triangle \mathbb{R}_- = \mathbb{R}^*$
 
 ### 2.3 Proprietes
 
 ==**Proprietes**==
 
- $A \cap B = B \cap A$
- $A \cup B = B \cup A$
- $A \triangle B = B \triangle A$
- $A \cap (B \cap C) = (A \cap B) \cap C$
- $A \cup (B \cup C) = (A \cup B) \cup C$
- $A \triangle (B \triangle C) = (A \triangle B) \triangle C$
- $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$
- $A \cup (B \cap C) = (A U B) \cap (A \cup C)$
- $C_E(A \cap B) = C_EA \cup C_EB$
- $C_E(A \cup B) = C_EA \cap C_EB$
- $A \subset B \iff C_EB \subset C_EA$
- $A \cap B = \varnothing \iff A \subset C_EB \iff B \subset C_EA$ (les parties A et B sont dites disjointes)

-------------------------------
### 2.4 Exercices d'application

**++Enonce++** : 
Soit A B et C 3 aprties d'un meme ensemble E. Demontrer que
$$(A \cap B) \cup (C \cap C_EA) \subset (A \cap C_EC) \cup (C_EA \cap C_EB) \cup (B \cap C)$$

> $(A \cap B) \cup (C \cap C_EA)$ : Ce qui appartient a A et a B $\cup$ ce qui n'appartient pas a A mais appartient a C
> $(A \cap C_EC) \cup (C_EA \cap C_EB) \cup (B \cap C)$ : Ce qui appartient a A mais pas a C $\cup$ ce qui n'appartient ni a A ni a B $\cup$ ce qui appartient a A et a B

**++Solution++** : 
Soit $x$ un element de $(A \cap B) \cup (C \cap C_EA)$, x appartient au moins a l'un des deux ensembles $A \cap B$ ou $C \cap C_EA$

Si $x \in A \cap B$
- Soit $x \in C$, alors $x \in B \cap C$;
- Soit $x \notin C$, alors $x \in A \cap C_EC$;

Si $x \in (C \cap C_EA)$
- Soit $x \in B$, alors $x \in B \cap C$;
- Soit $x \notin C$, alors $x \in C_EA \cap C_EB$;

Dans tous les cas : 
$x \in (A \cap C_EC) \cup (C_EA \cap C_EB)$

## 3. Application d'un ensemble dans un autre

### 3.1 Definition

==**Definition (Applications)**==
Soient E et F 2 ensembles. On appelle **application de E dans F** la donnee des ensembles E, F et d'une partie $\Gamma$ de E x F telle que pour tout element $x$ de E il existe un element $y$ de F tel que $(x, y) \in \Gamma$
- E est appele **ensemble de depart** de l'application
- F est appele **ensemble d'arrive** de l'application
- $\Gamma$ est **graphe** de l'application
- $y$ est appele **image** de $x$ par l'application. Si on designe l'application par f on ecrit alors $y = f(x)$
- $x$ est un **antecedent** de y par l'application (mais pas forcement le seul)
- **Notation** : $\begin{cases}
E \overset{f}\to F\\
x \to f(x)
\end{cases}$

### 3.2 Composition des applications

Soit E, F et G trois ensembles, f une application de E dans F et g une application de F dan G
on appelle application composee de f et g l'application de E dans G qui a un element x de E fait correspondre l'image par g de l'image par f de x.
On note cette application $g \circ f$
$$\forall x \in E g \circ f(x) = g[f(x)]$$

>Exemples : $f \circ Id_E = f; Id_F \circ f = f$

==**Theoreme 1**==
Si E, F, G, H sont quatre ensembles et f, g, h trois applications appartenant respectivement a $\mathcal{F}(E, F), \mathcal{F}(F, G), \mathcal{F}(G, H)$
$$h \circ (g \circ f) = (h \circ g) \circ f$$

>**Demonstration**
> Les deux applications $h \circ (g \circ f)$ et $(h \circ g) \circ f$ ont le meme ensemble de depart : E et le meme ensemble d'arrivee H. Blablabla

:::info
L'ensemble des applications de E dans F est note $\mathcal{F}(E, F)$ ou encore $F^E$
:::

### 3.3 Famille d'elements d'un ensemble

==**Definition (Famille)**==
- On appelle **famille** d'elements d'un ensemble E indexee par un ensemble I, une application de I dans E notee : 
$$\begin{cases}I \to E \\i \to x_i\end{cases}$$
- Onc peut identifier le produit cartesien $E \times E$ avec l'ensemble des familles d'elements de E indexees par l'ensemble $\{1, 2\}$, et plus generalement le produit cartesien $E^n$ avec l'ensemble des familles d'elements de E indexees par $\{1, ..., n \}$

- On peut generaliser aux familles de parties d'un ensemble E les notions d'intersection et de reunion : 
$$\underset{i \in I}{\bigcap} A_i = \{x \in E, \forall i \in I, x\in A_i\}$$

## Injectivite et surjectivite

### 4.1 Equation

Soit f une application de E dans un ensemble F, On appelle equation une egalite de la forme $f(x) = y$ (avec ici x solution de l'equation) ou $y$ est un element fixe de F ; on appelle la **solution** de l'equation blabla

==**Definition (Application injective)**==

Soit f une application d'un ensemble E blabla
A l'aide de quantificateurs, l'injectivite de f s'ecit : 
$$\forall(x, x') \in E^2 f(x) = f(x') \Rightarrow x = x'$$

==**Theoreme 2**==
1. La composee de deux injectives est une injection
2. Si la composee $g \circ f$ est injective, f est injective

-------------------
==**Definition (Application surjective)**==

A l'aide de quantificateurs, la surjectivite de f s'ecit : 
$$\forall(y) \in F f\exists x \in E f(x) = y$$

==**Theoreme 2**==
1. La composee de deux surjectives est une surjection
2. Si la composee $g \circ f$ est injective, g est injective

### 4.4 Application bijective
- Une application f est bijective si elle est injective et surjectivem c-a-d si pour tout $y \in F$, l'eq blabla

## 5 Image directe ou reciproque d'une partie

### 5.1 Image d'une partie de l'ensemble de depart

==**Definition (image directe)**==
- Soit f une application de E dans F et A une partie de E
- On appelle **image de A par f** l'ensemble des images des elements de A
- Par abus de notation on le note f(A) mais ce n'est pas l'image d'un element de E

Pvar definition : 
$$\forall y \in F y \in f(A) \iff x \in A y = f(x)$$

==**Definition (image reciproque)**==
- On appelle **reciproque de B par f** l'ensemble des antecedents des elements de B, autrement dit l'ensemble des elements de E dont l'image appartient a B
- Se note $f^{-1}(B)$ mais $f^{-1}$ ne designe pas une application

Par definition : 
$$\forall x \in E x \in f^{-1}(B) \iff f(x) \in B$$

## 6. Relation d'ordre

### 6.1 Relation binaire

On appelle **relation binaire** definie sur un ensemble E la donnee de e et d'une partie quelconque $\Gamma$ de $E \times E$. On note $x\mathcal{R}y$ pour $(x, y) \in \Gamma$
> *Exemples* : Dans $\mathbb{Z} : |x| = |y|, x \neq y$ divise y, etc

Une relation binaire $\mathcal{R}$ definie sur E est une **relation d'ordre** si elle est : 
- **Reflective** ($\forall x \in E, x\mathcal{R}x$)
- **Antisymetrique** ($\forall(x, y) \in E^2 (x\mathcal{R}y \Rightarrow y\mathcal{R}x)$)
- **Transitive** ($\forall(x, y, z) \in E^3 (x\mathcal{R}y\ et\ y\mathcal{R}z) \Rightarrow x = y$)
