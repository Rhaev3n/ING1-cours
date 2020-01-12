[PROBA] Probabilites discretes (3)
===

## Probabilites conditionnelles

$(\Omega, P)$ espace probabilise fini, ou P est la probabilite uniforme
Supposons que l'evenement A soit realise $(P(A) \neq 0)$

La ==**probabilite conditionnelle**== de B sachant A est definie par

$\begin{align}P(B/A) = \frac{P(A \cap B)}{P(A)}\end{align}$

:::info
**Notation** : $P(B/A) = P_A(B)$
:::

$\forall A \in \mathcal{P}(\Omega)$ l'application $P_A: \mathcal{P}(\Omega) \to [0, 1]$
$\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  B \to P_A(B)$

est une probabilite sur $\Omega$ appelee **probabilite conditionnelle**

:::info
**Remarque** : $P_A(\overline B) = 1 - P_A(B)$
:::

### Formule des probabilites composees

Soit $n \in \mathbb{N}\ \ (n \geq 2)$
Pour toute famille d'evenements $(A_1, A_2, ..., A_n)$ de $(\Omega, P)$ tel que $P(A_1 \cap A_2, ..., \cap A_{n-1}) \neq 0$

Alors on a $(A_1 \cap A_2 ... \cap A_{n}) = P(A_1)P(A_2/A_1)P(A_3/A_1\cap A_2)...P(A_n/A_1 \cap A_2 ... \cap A_{n-1})$

$P(A_1 \cap A_2 \cap ... \cap A_n) = P(A_1)\prod_{k=2}^{n}P(A_k/A_1\cap A_2 \cap ... \cap A_{k-1})$

En effet,

$\begin{align}P(A_1)P({A_2}_{/A_1})P({A_1}_{/A_1 \cap A_2})...P({A_n}_{/A_1 \cap ... \cap A_{n-1}}) &= P(A_1)\frac{P(A_1 \cap A_2)}{P(A_1)} \times \frac{P(A_1 \cap A_2 \cap A_3)}{P(A_1 \cap A_2)}....\frac{P(A_1 \cap A_2 ... A_n)}{P(A_1 \cap A_2 ... A_{n-1})} \\ &= P(A_1 \cap A_2 \cap ... \cap A_n)\end{align}$

### Systeme complet

==**Definition**==

$\Omega$ univers fini
On appelle **systeme complet** d'evenements $A_i\ (1 \leq i \leq n)\ (n \in \mathbb{N}^*))$ toute famille $A_i\ (A_i \cap A_j \neq \varnothing\ \ \forall i \neq j\ et\ \bigcup^n_{i=1}A_i = \Omega)$

$(A_i)_{1 \leq i \leq n}$ est une **partition** de l'univers

:::info
**Remarque**
$\begin{align}\sum_{i=1}^{n} P(A_i) = 1\ car\ \bigcup_{i=1}^{n}A_i = \Omega &\implies P(\bigcup_{i=1}^{n} A_i) = P(\Omega = 1) \\ &\implies \sum_{i=1}^{n} A(A_i) = 1\end{align}$


**Formule de probabilites totales**
$P(B) = \sum_{i=1}^{n} P(B \cap A_i)\ \ \forall B \in \mathcal{\Omega}$

$B \cap A_1, B \cap A_2, ..., B \cap A_n$ sont 2 a 2 incompatibles car

$B \cap A_i \cap B \cap A_j = B \cap A_i \cap A_j \ B \cap \varnothing = \varnothing$

$P(\bigcup_{i=1}^{n}B \cap A_i) = \sum_{i=1}^{n} P(B \cap A_i)$ 

car
$\bigcup_{i=1}^{n}(B \cap A_i) = B \cap (\bigcup_{i=1}^{n} A_i) = B \cap \Omega = B \implies P(B) = \sum_{i=1}^{n}P(B \cap A_i) = \sum_{i=1}^{n}P(B/A_i)P(A_i)$
:::

### Formule de Bayes

1. $\begin{align}P(A/B) = \frac{P(B/A)P(A)}{P(B)}\ \ \ (P(B) \neq 0, P(A) \neq 0)\end{align}$

En effet $P(A/B) = \frac{A \cap B}{P(B)} = \frac{P(B/A)P(A)}{P(B)}$ et $P(B/A) = \frac{B \cap A}{P(A)}$

2. $(A_1, A_2, ..., A_n)$ un systeme complet
$\begin{align}\forall i \in [[1, n]],\ \ \ P(A_i/B) = \frac{P(B/A_i)P(A_i)}{P(B)} = \frac{P(B/A_i)P(A_i)}{\sum_{j=1}^{n} P(B/A_j)P(A_j)}\end{align}$

car $P(B) = \sum_{j=1}^{n} P(B/A_j)P(A_j)$

---
**==Definition (evenements independants)==**

A et B sont 2 **evenements independants** ssi

$P_A(B) = P(B) \iff P(A \cap B) = P(A)P(B)$


## Variables aleatoires discretes

**==Definition (variable aleatoire)==**

$\Omega$ univers fini
Toute application X definie sur $\Omega$ a valeurs dans un ensemble E est appele **variable aleatoire** sur $\Omega$

Si $E = \mathbb{R}$ alors X est appelle V.A (variable aleatoire) reelle

$\Omega$ fini, $X(\Omega) = \{x_1, x_2, ..., x_n\}$ l'ensemble des valeurs de X

### Applications

++Exemple 1++ : 

Considerons le lancer de 2 des equilibres

$\Omega = [[1, 6]]^2 = \{(i, j) / i\in [[1, 6]], j \in [[1, 6]]\}$

$Card(\Omega) = 6^2 = 36$
$\forall \omega = (i, j) \in \Omega P(\omega) = \frac{1}{36}$

Soit X l'application $X \to E = \{2, ..., n\}$
$\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ (i, j) \to i + j$

$P(X=5) = P(\{(2, 3), (3, 2), (1, 4), (4, 1)\})$
$P(X=5) = \frac{4}{36} = \frac{1}{9}$

++Generalisation++
$\forall x \in E$
$P(X=x) = P(\{ X^{-1}(x) \}) = \{ \omega \in \Omega | X(\omega) = x\}$

++Exemple 2++ : 

$A \in \mathcal{P}(\Omega)$
Soit $X \to \mathbb{R}$
$\ \ \ \ \ \ \ \ \omega \to \begin{cases}1\ si\ \omega \in A \\ 0\ si\ \omega \in \overline A\end{cases}$

On dit que $X$ est une **variable aleatoire indicatrice** de A 

$X = \mathbb{1}|_A$

:::info
**Remarque**
L'ensemble des V.A discretes munies de (+) et (.) (multiplications par des scalaires) est un espace vectoriel

On le note $\mathcal{F} (\Omega, \mathbb{R})$
:::

**++Definition++**

On appelle **fonction de repartition** de la variable aleatoire $X$

$F: \Omega \to [0, 1]$
$\ \ \ \ \ \ \ x\to F(x)$

$F(x) = P(X < x)\ \ \forall x \in \mathbb{R}$

:::info 
**Remarque**
F est croissante 
$F(-\infty) = P(\varnothing) = 0$
$F(+\infty) = P(\Omega) = 1$
:::

## Moment d'une variable aleatoire 

### Esperance mathematique

Soit X une variable aleatoire discrete
On appelle ==**esperance**== de $X$

:::danger
$E(X) = \sum x_i\ \ P(X=x_i)$
:::

:::info
**Remarque**
L'operateur E est lineaire
- $E(\alpha X) = \alpha E(X)\ \ \forall \alpha \in \mathbb{R}$
- $E(X + Y) = E(X) + E(Y)$
- $E(a) = a\ \ \forall a \in \mathbb{R}$
:::

**==Definition==**

Soit $\varphi$  une fonction quelconque et $X$ une variable aleatoire
 
$E(\varphi(X)) = \sum_{i}^{} \varphi(x_i)P(X=x_i)$

---
### Variance de X

**==Definition (Variance)==**

Soit X une variable aleatoire discrete
On appelle **variance** de $X$

:::danger
$\sigma^2 = V(X) = E((X - E(X))^2)$
:::

$\sigma = \sqrt{V(X)} \implies$ **ecart type** de $X$
C'est une mesure de la dispersion de X autour de la valeur centrale E(X)

:::info
**Remarque**
V n'est pas lineaire
- $V(\alpha X) = \alpha^2V(X)$
- $V(X + Y) = V(X) + V(Y)\ si\ X+Y$ sont independantes
:::

### Formule de Konig Huggheus

$V(X) = E(X^2) - E^2(X)$

**==Definition (Moment d'ordre k)==**

On appelle **moment d'ordre k** $(k \in \mathbb{N}^*)$ de X
$\mathcal{F}_k = E(X^k)$

## Lois de probabilites d'usage courant

> Lois classiques

### ==**Loi uniforme**==

$X(\Omega) = \{1, 2, ..., n\}$
$P(X=1) = \frac{1}{n}\ \ \forall k \in X(\Omega)$

++Esperance++

$E(X) = \sum_{k=1}^{n} kP(X=k) = (1/n)\sum_{k=1}^{n} k = \frac{n(n+1)}{2n} = \frac{n+1}{2}$


++Variance++

$V(X) = E(X^2 - E^2(X))$

$E(X^2) = \sum_{k=1}^{n}k^2P(X=k) = (1/n) \sum_{k=1}^{n}k^2 = (1/n)\frac{n(n+1)(2n+1)}{6} = \frac{(n+1)(2n+1)}{6}$

$\phi(X) = X^2$

$V(X) = \frac{(n+1)(2n+1)}{6} = \frac{n+1}{4} = \frac{2(2n^2 + 3n + 1) - 3(n^2 + 2n+1)}{12}$

$V(X) = \frac{n^2 - 1}{12}$

---
### **==Loi de Bernoulli $B(p)$==**

$X = 1$ si un evenement A se realise avec la probabilite p
$X = 0$ sinon (avec la probabilite $1-p$)

++Esperance++

$E(X) = \sum_{k=0}^{1} kP(X=k) =p$

$E(X^2) = \sum_{k=0}^{1} k^2P(X=k) =p$

++Variance++

$V(X) = p - p^2 = p(1-p)$

$V(X) = pq$ ou $q = 1-p$

---
### **==Loi binomiale $B(n, p)$==**

On repete n fois l'experience de Bernoulli de maniere independante dans des conditions identiques

Soit X le nombre de realisations de l'evenement A

$X = \sum_{i=0}^{n} X_i$, $X_i$ suit la loi de Bernoulli $B(p)$
$X_i$ independante

++Esperance++

$E(X) = \sum_{i=1}^{n} E(X_i) = \sum_{i=1}^{n}p$

$E(X) = np$

++Variance++

$V(X) = \sum_{i=1}^{n} V(X_i)$ car $X_i$ independante

$V(X) = \sum_{i=1}^{n} pq = npq$

$P(X=k) = \binom{n}{k} p^k(1-p)^{n-k} \forall k \in [[0, n]]$