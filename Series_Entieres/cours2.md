Series Entieres (2)
===

## Rappel

### Serie entiere
Une serie entiere est une serie de fonctions de la forme suivante
$$\sum^{}_{n \geq 0} a_nx^n,\ a_n \text{ est le coefficient de la serie}$$

On s'interesse aux fonctions que l'on decrit comme limites de ces series.

**Exemple** : Suite geometrique $\sum_{n \geq 0}^{}x^n$

Soit $N \in N$, $\sum_{n \geq 0}^{}x^n = \frac{1 - x^{N + 1}}{1 - x}$
Si $x \notin [-1, 1]; \frac{1 - x^{N + 1}}{1 - x}$ ne converge pas
Si $x \in ]-1, 1[; \frac{1 - x^{N + 1}}{1 - x} \underset{N \to +\infty}\to \frac{1}{1 - X}$
Si $x \in \{-1, 1\}; \frac{1 - x^{N + 1}}{1 - x}$ ne converge pas

-----------------------
### Lieu de congergence
En general, pour une serie entiere $\sum^{}_{n \geq 0} a_nx^n$, le **lieu de convergence** prend la forme suivante: 
![](https://i.imgur.com/YnFHCyv.png)

R est le **rayon de convergence**
- Sur un disque intervalle symetrique, $\sum^{}_{n \geq 0} a_nx^n$ converge
- A l'exterieur du segment ]-R, R[, $\sum^{}_{n \geq 0} a_nx^n$ diverge
- ]-R, R[ est le disque de convergence
- Sur les bords -R et R, ca depend

## Rayon de convergence
    Comment calculer le rayon de convergence d'une serie ?
A ce stade, on a rien d'autre que le test.

**Remarque** : 
1. Si $\sum^{}_{n \geq 0} a_nx^n$ CV pour r, alors elle CV necessairement sur $]-|r|, |r|[$
2. S'il existe $r$ tel que $\sum^{}_{n \geq 0} a_nr^n$ CV et $\sum^{}_{n \geq 0} a_n(-r)^n$ DV, alors r est le rayon de $\sum^{}_{n \geq 0} a_nx^n$

----------
:::warning
Trouver des series respectivement de rayons de convergence 0, 1, 2 et $+\infty$
:::

**Exemple de series entieres** : 
- $\begin{align}\sum^{}_{n \geq 0} x^n\end{align}$ est de rayon 1.
- $\begin{align}\sum^{}_{n \geq 0} (\frac{x}{2})^n\end{align}$ est de rayon 2.
> $\begin{align}\sum^{}_{n \geq 0} (\frac{x}{2})^n\end{align}$ CV ssi $|\frac{x}{2}| > 1 \iff |x| > 2$

- Si $a > 0$, $\begin{align}\sum^{}_{n \geq 0} (\frac{x}{a})^n\end{align}$ est de rayon a.
- $\begin{align}\sum^{}_{n \geq 1} \frac{x^n}{n!}\end{align}$ est de rayon 0.
- $\begin{align}\sum^{}_{n \geq 0} \frac{x^n}{n^n}\end{align}$ est de rayon $+\infty$.




:::warning
Trouver des series convergentes : 
- Sur les bords du disque de convergence
- En un seul point de convergence
- En aucun point du bord
:::

**Convergence aux bords** : 
- $\begin{align}\sum^{}_{n \geq 0} x^n\end{align}$ ne CV pas sur les bords de son disque de convergence.
- $\begin{align}\sum^{}_{n \geq 0} \frac{x^n}{n}\end{align}$ CV en -1 mais pas en 1.
- $\begin{align}\sum^{}_{n \geq 0} \frac{x^n}{n^2}\end{align}$ CV en -1 et en 1.
> Est-elle de rayon de CV 1 ? 

## Critere de d'Alembert
### Critere de d'Alembert pour les series numeriques

Soit  $\sum^{}_{n \geq 0} u_n$ une serie numerique avec $u_n \neq 0$
Pour n suffisamment grand : 
- Si $\frac{u_{n+1}}{u_n} \to l > 1 \Rightarrow \sum^{}_{n \geq 0} u_n$ CV
- Si $\frac{u_{n+1}}{u_n} \to l < 1 \Rightarrow \sum^{}_{n \geq 0} u_n$ DV

### Calculer le rayon de convergence avec le Critere de d'Alembert
On peut faire appel au critere de d'Alembert pour etudier la convergence d'une serie entiere. On s'interesse au rapport
$$\frac{a_{n+1}x^{n+1}}{a_nx^n} = \frac{a_{n + 1}}{a_n}x$$
On a $\begin{align}|\frac{a_{n + 1}}{a_n}|x \underset{n \to +\infty}\to l|x|\end{align}$
- Si $l|x| < 1 \Rightarrow \sum_{n \geq 0}^{} a_nx^n$ CV
- Si $l|x| > 1 \Rightarrow \sum_{n \geq 0}^{} a_nx^n$ DV

$l|x| > 1 \iff |x| > \frac{1}{l}$
$l|x| < 1 \iff |x| < \frac{1}{l}$

-> Moyen qui permet de calculer le rayon de convergence d'une serie entiere

:::danger
**Critere de d'Alembert**
Soit $\sum^{}_{n \geq 0} a_nx^n$ une serie entiere, On suppose que les $a_n$ sont non nuls a partir d'un certain rang et que le rapport $a_{n+1} / a_n$ CV vers $l \in \mathbb{R}_+$. Le rayon de convergence de $\sum^{}_{n \geq 0} a_nx^n$ est egal a $\frac{1}{l}$ si $l \neq 0$ et $+\infty$ sinon.
:::

**Exemple** (Critere de d'Alembert) : 
- $\begin{align}\sum^{}_{n \geq 0} x^n, \forall n \in N; a_n = 1 \Rightarrow \frac{a_{n+1}}{a_n} = 1 \underset{n \to +\infty}\to 1\end{align}$.
Son rayon de CV est 1/1 = 1
- $\begin{align}\sum^{}_{n \geq 0} (\frac{x}{2})^n, \forall n \in N a_n = \frac{1}{2}^n et \frac{a_{n+1}}{a_n} = \frac{1/2^{n+1}}{1/2^n} = 1/2 \underset{n \to +\infty}\to 1/2\end{align}$.
Son rayon de CV est $\frac{1}{(1/2)}$ = 2

- $\begin{align}\sum^{}_{n \geq 0} \frac{x^n}{n^2}, \frac{a_{n+1}}{a_n} = \frac{\frac{1}{(n+1)^2}}{\frac{1}{n^2}} = \frac{n^2}{(n+1)^2} = \frac{n^2}{n^2 + 2n + 1} \underset{+\infty}{\sim} \frac{n^2}{n^2} = 1\end{align}$
Donc $\frac{a_{n+1}}{a_n} \to 1$. Son rayon de CV est 1

- $\begin{align}\sum^{}_{n \geq 1} \frac{x^n}{n!}, |\frac{a_{n+1}}{a_n}| = \frac{\frac{1}{(n+1)!}}{\frac{1}{n!}} = \frac{n!}{(n + 1)!} = \frac{n!}{n!(n+1)} = \frac{1}{(n+1)} \underset{+\infty}{\to}  0\end{align}$
$\begin{align}|\frac{a_{n+1}x^{n+1}}{a_nx^n}| = |\frac{a_{n+1}}{a_n}x| \underset{n \to +\infty}\to 0\end{align}$



------
$\sum^{}_{n \geq 0} a_nx^n, a \neq 0$
Soit $O \in R$, on etudie la serie numerique $\sum^{}_{n \geq 0} a_nO^n$
Si $\begin{align}|\frac{a_{n+1}O^{n+1}}{a_nO^n}| = |\frac{a_{n+1}}{a_n}||O| \underset{n \to +\infty}\to M|O|\end{align}$
On suppose que $\frac{}{}$ tend vers M quand $n \to +\infty$ 

## Critere de Cauchy
:::danger
**Critere de Cauchy**
Soit $\sum^{}_{n \geq 0} a_nx^n$ une serie entiere, On suppose que $\sqrt[n]{|a_n|}$ CV vers $l \in \mathbb{R}_+$. Le rayon de convergence de $\sum^{}_{n \geq 0} a_nx^n$ est egal a $\frac{1}{l}$ si $l \neq 0$ et $+\infty$ sinon.
:::

> Utile quand il n'y a pas de rang a partir duquel les $a_n$ sont tous non nuls (ex: $\sum_{n \geq 0} x^{2n}$)

**Exemple** (Critere de Cauchy) : 

:::warning
Calculer avec le critere de Cauchy : 
$\sum_{n \geq 0} \frac{x^n}{n^n}$ 
$\sum_{n \geq 0} \frac{x^{2n}}{n + 1}$ 
:::

> Quel est le rayon de CV de $\sum_{n \geq 0} x^{2n}$

**Definition (Suites numeriques equivalentes)** : 
Deus suites numeriques $(u_n)$ et $(v_n)$
On suppose que les $v_n \neq 0$ a partie d'un certain rang
sont : 
- Equivalentes     $\ \ \ \frac{u_n}{v_n} \underset{n \to +\infty}\to 1$
- $u_n = O(v_n)\ \ \ \ \frac{u_n}{v_n}$ bornee a partir d'un certain rang
> C'est le cas si $\frac{u_n}{v_n}$ a une limite 
Equivalentes si elles se comportent de la meme maniere en $+\infty$

**Proposition** : 
Soient $\sum^{}_{n \geq 0} a_nx^n$ et $\sum^{}_{n \geq 0} b_nx^n$ deux series entieres reelles respectivement de rayon de convergence $R_a$ et $R_b$
- Si $a_n = O(b_n)$ alors $R_a \geq R_b$
- Si $a_n \sim b_n$ alors $R_a = R_b$

++Exemple++ : 
$\sum_{n \geq 0} x^2n; a_n = \begin{cases}0\ si\ impair\\1\ sinon\end{cases}$
$\sum_{n \geq 0} x^n; b_n = 1$

$\frac{a_n}{b_n} = \begin{cases}0\ si\ n\ impair\\ 1\ si\ n\ pair\end{cases}$
$\frac{a_n}{b_n}$ n'a pas de limite mais est bornee ($a_n = O(b_n)$)

------------
## Developper series entieres

Developpement en series entiere (DSE) : On ecrit une fonction comme somme / limite de series entieres

- DSE de $e^x$ : 
L'exponentielle est l'unique solution de l'equadiff $f' = f$ valant 1 en 0
Supposons que $f' = f$ ait une solution sous forme de series entieres, $\sum_{n \geq 0} a_nx^n$.
$$\sum_{n = 0}^{+\infty} na_nx^{n - 1} = \sum^{+\infty}_{n=0}a_nx^n$$

**Resultat** : Si 2 series entieres sont egales sur un intervalle ouvert, elles ont le meme coefficient 

D'apres le resultat precedent : 
$(n+1)a_{n+1} = a_n$
- $a_n$ est le coef de degre n a droite de l'egalite
- $(n+1)a_{n+1}$ est le coef de degre n a gauche $\Rightarrow a_{n+1} = \frac{a_n}{(n+1)}$ avec $a_0 = 1$

> On cherche a calculer $a_n$

Calculer $a_4$ : 
$a_4 = \frac{a_3}{4}$
$a_3 = \frac{a_2}{3}$
$a_2 = \frac{a_1}{2}$
$a_1 = \frac{a_0}{1}$
$a_0 = 1$

Donc $a_4 = (1/4) * (1/3) * (1/2) * 1 = \frac{1}{4!}$
Ainsi $a_n = \frac{1}{n!}$

---
Si $\sum^{+\infty}_{n \geq 0}a_nx^n$ est solution de $f' = f$ valant 1 en 0 alors c'est : 
$$\sum^{+\infty}_{n \geq 0}\frac{x^n}{n!}$$

C'est une serie entiere de rayon de convergence $+\infty$. Par unicite de la solution a $f' = f$ valant 1 en 0, on a : $e^x = \sum^{+\infty}_{n \geq 0}\frac{x^n}{n!}$