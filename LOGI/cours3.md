[LOGI] Logique du premier ordre (3)
===

## Point de vue algebrique

⟛ **Equivalence semantique** : 
$\phi \iff \psi$ Tautologie

**Equivalence Syntaxique** : 
$\phi \vdash \psi$ et $\psi \vdash \phi$

:::info
Notation : $\phi\ ⟛\ \psi$ $\vdash$
:::

++Exemples++ : 

$A\ ⟛\ A$

### Theoreme de Godot

Dans LK au niveau $F_0$ on a (equiv semantique) equivaut a (equivalence syntaxique)

|$\vdash$||
|:---:|:---:|
|V|F|
|F|V|
|?|?|

|A|$\lnot$A||A $\lor \lnot$ A|
|:---:|:---:|:-:|:---:|
|V|F||V|
|F|V||V|
|?|?||?|

==**Propriete**==

En ecrivant $\equiv$ au lieu de ⟛ on a $A \equiv A$

Pareil avec $\land$
> Propositions Algebriques : 
> $A \lor B \equiv B \lor A$
> $\lnot(A \lor B) \equiv \lnot A \land \lnot B$
> $(A \lor B) \lor C \equiv A \lor(B \lor C)$

**La logique c'est algebrique**

Relations binaires (paradigmes) :
1. Booleen : (a;b) $\to$ Vrai/Faux (selon situation)
2. Ensembles : $E \to R \subset \{(a, b), a \in E, b \in E$ 
3.  Graphes 
4.  Formules logiques $aRb \iff \phi[a;b]$ est verifiee

++Exemples++ : 

On definit R sur $\mathbb{Z}$ par : $R_1: aRb \iff (\exists k \in \mathbb{N}\ b=a+k)$
$\equiv_n: a_1 \equiv_n \iff \exists q \in \mathbb{Z}\ \ b-a=qn$

Relation ensembliste sur $\mathbb{R}$

$R = \{(x, y) \in \mathbb{R}^2 / (x - 2)^2 + (y - 2)^2 \leq 1$

|:heart:|Paul|Brian|Sophie|Lea|
|:---:|:---:|:---:|:---:|:---:|
|Paul|1|1|0|0|
|Brian|0|1|1|0|
|Sophie|1|0|1|0|
|Lea|1|1|1|0|

## Classifications de relations binaires

- **Reflexivite** : R est reflexive lorsque $\forall x; \mathcal{T},\ \ xRx$
	- Plus d'ordre 0 (c'est un cas d'ordre 1)

++Exemple++ : 
$\leq$ est reflexif ($\mathcal{R}$ reel)
$\equiv_n$ est reflexif ($\mathcal{T} int$)

- **Symetrie** : R verifie $\forall x: \mathcal{T} \forall y: \mathcal{T},\ \ xRy \implies yRx$

++Exemple++ : 
$\equiv_n$ symetrique
$\leq$ sur $\mathcal{T}$: reel n'est pas symetrique 
> (1 $\leq 2$, $\lnot 2 \leq 1$)(mais on a pas $2 \leq 1$)
> 
$\vdash$ n'est pas symatrique

- **Antisymetrie** : R verifie
$\forall x: \mathcal{T}\ \ \forall y:\mathcal{T},\ \ xRy \land yRx \implies x = y$

++Exemple++ : 

$\leq$ sur $\mathcal{T}$: reel
:heart: n'etait ni symetrique ni antisymetrique

:::danger
**Remarque**

Antireflexivite $\ \ \forall x: \mathcal{T}\ \ \lnot xRx$

**/!\\** Ce n'est pas non reflexif car $\exists x:\mathcal{T} \lnot xRx$
:::

- **Transitivite** : R verifie
$\forall a: \mathcal{T}\ \forall b: \mathcal{T}\ \forall c:\mathcal{T}\ \ aRb \land bRc \implies aRc$

++Exemple++ : 
$\leq, \subseteq, \equiv_n$

++Exemple++ : 
$\alpha \approx \beta$ non transitif sinon tous les reels verifieraient $\alpha \approx x$

**Vocabulaire**

- R relation binaire est dite **d'equivalence** lorsque R est reflective, transitive et symetrique
- R relation binaire est dite **d'ordre** lorsqu'elle est reflective, transitive et anti-symetrique

## Etude de nos relations logiques 

Etudions ⟛
- **Reflexivite** : $\phi ⟛ \phi$ signifie $||\phi ⟛ \phi||$ Tautologie $\to$ oui
- **Symetrie** : $||\phi \iff \psi||_{\nu} =$ vrai implique $||\psi \iff \phi||_{\nu}$ = vrai ($\forall \nu$)
- **Transitivite** : $\phi \iff \psi$ Tautologie et $\psi \iff \phi$ Tautologie par table de verite ou avec $\phi \iff \{Tautologie$
	- NB: PAS antisymetrique

++Exercice++ : 
On peut prouver que ⟛ a les memes propositions: Reflexivite [axi], Symetrie, Trensition

Relation d'equivalence !
R binaire (Reflexive, Transitive, Symetrique)

Ainsi: Equivanece syntaxique, equivalence semantique sont bien des equivalences

## Theoreme de completude de Gedal

Pour la logique d'ordre 0 (calcul propositionnel)
(equivalence semantique) equivaut (equivalence syntaxique)

$\phi ⟛ \psi$ ssi $\ \psi ⟛ \phi$ (ordre 0)

++Exemple++ (LK):
$\lnot (A \land B) ⟛ \lnot A \lor \lnot B$ (tableau de verite)
$\lnot(A \land B) \vdash \lnot A \lor \lnot B$ et $\lnot A \lor \lnot B \vdash \lnot(A \land B)$

:::info
/!\ $\top ⟛ \lnot A \land Acd Pr$
:::
## Relation ordre

R binaire
1) Reflexive (ordre large), Antireflexivite (ordre strict)
2) Transitivite
3) Antisymetrie (ordre large)