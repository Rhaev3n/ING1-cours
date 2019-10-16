Series entieres (3)
===

## Additionner des series entieres

==**Proposition**==
Soient $\sum_{n=0}^{+\infty} a_nx^n$ et $\sum_{n=0}^{+\infty} b_nx^n$ deux series entieres de rayons des convergence $R_a$ et $R_b$. On note leur somme $\sum_{n \geq 0}c_nx^n$.
$$\forall n \geq 0\ \ \ c_n = a_n + b_n$$

Le rayon de convergence $R_c \geq min(R_a, R_b)$ et pour tout $x \in ]-R_c, R_c[$ (en particulier $\forall |x| < min\{R_a, R_b\}$)

$$(\sum_{n \geq 0}^{+\infty}a_nx^n) + (\sum_{n \geq 0}^{+\infty}b_nx^n) = \sum_{n \geq 0}^{+\infty}c_nx^n$$

---
**Exemple 1 (CVA)**
$\begin{align}\sum_{n=0}^{N}(a_x + b_n)x^n \leq \sum_{n \geq 0}a_nx^n + \sum_{n \geq 0}b_nx^n\end{align}$
$\begin{align}\Rightarrow |\sum_{n=0}^{N}(a_x + b_n)x^n| \leq \sum_{n=0}^{N}|a_x + b_n||x|^n \leq \sum_{n \geq 0}|a_n||x|^n + \sum_{n \geq 0}|a_n||x|^n\end{align}$

Et on a $\sum_{n \geq 0}|a_n||x|^n > +\infty$ et $\sum_{n \geq 0}|b_n||x|^n < +\infty$
Donc les sommes partielles de sont majores, d'ou la CVA.

**Exemple 2 (serie nulle)**
Soient $\sum_{n \geq 0}^{}x^n$ et $- \sum_{n \geq 0}^{}x^n$ de rayon de CV 1. La somme de ces 2 series est la serie nulle, de rayon de convergence $+\infty$.

## Multiplier des series entieres

==**Proposition**==
Soient $\sum_{n \geq 0}a_nx^n$ et $\sum_{n \geq 0}b_nx^n$ 2 series entieres respectivement de rayons de convergence $R_a$ et $R_b$. On note la serie entiere produit des deux premieres.
$$\forall n \geq 0,\ \ c_n = \sum_{k=0}^n a_kb_{n-k}$$

Le rayon de convergence $R_c \geq min(R_a, R_b)$ et pour tout $x \in ]-R_c, R_c[$ (en particulier $\forall |x| < min\{R_a, R_b\}$)

$$(\sum_{n \geq 0}^{+\infty}a_nx^n) \times (\sum_{n \geq 0}^{+\infty}b_nx^n) = \sum_{n \geq 0}^{+\infty}c_nx^n$$

:::info
On connait l'ecriture de la fonction exponentielle comme limite de serie entiere. Montrer que pour tout $a, b \in R$
$$exp(a+b) = exp(a)exp(b)$$
:::

## Primitives de series entieres

Soit une serie entiere de rayon de CV R > 0. f limite de s sur ]-R, R[
:::info
Est-ce que f admet une primitive sur ]-R, R[
:::

:::danger
**Remarque**
Savoir si f a une primitive et en donner une expression revient a etudier la question de l'integrabilite et des integrales de f
:::

----------
==**Rappel (Integrales et primitives)**==

- Une **integrale** est une aire algebrique, l'aire comprise entre le graphe d'une fonction et l'axe des abscisses. Elle est comptee positivement quand on est au-dessus de l'axe, et negativement en-dessous.
- Une **primitive** d'une fonction f (continue) est une fonction $F$ telle que $F' = f$.

==**Theoreme fondamental de l'analyse**==
Une primitive de f est la fonction $x \to \int_{0}^{x}f(t)dt$
En particulier $F(b) - F(a) = \int_{0}^{b}f(t)dt - \int_{0}^{a}f(t)dt = \int_{a}^{b}f(t)dt$


## Integrales de series entieres

:::info
Y a-t-il un lien entre la suite des integrales des sommes partielles
$$\int_{a}^{b}\sum_{n=0}^{N}a_nx^n = \sum_{n=0}^{N}[\frac{a_n}{n + 1}x^{n+1}]_{a}^{b}$$
et $\int^b_af(t)dt$ (pour peu que cela existe)

Ou f est la limite de la serie entiere $\sum_{n \geq 0}a_nx^n$
:::


==**Proposition**==
Soit une serie entiere $\sum_{n \geq 0}a_nx^n$ de rayon de CV R. f la limite de $\sum_{n \geq 0}a_nx^n$, definie sur ]-R,R[. La fonction f est integrable sur [a, b] $\in ]-R,R[$ et 
$$\int^b_af(t)dt = \int_a^b(\sum^{+\infty}_{n=0} a_nx^n)dt = \sum^{+\infty}_{n=0} \int^b_a a_nx^n dt = \sum^{+\infty}_{n=0}[\frac{a_n}{n+1}t^{n+1}]_a^b$$

==**Corollaire**==
La fonction f admet une primitive sur ]-R,R[ decrite par la serie entiere
$$\int^x f(t)dt = \sum_{n=0}^{+\infty}\frac{a_n}{n+1}x^{n+1}$$

> $\int^x$ : primitive dont la variable est x

:::info
Calculer la limite de la serie numerique
$$\sum_{n=1}^{+\infty}\frac{2^{-n}}{n}$$
:::

> $\begin{align}\sum_{n \geq 0}\frac{2^{-n}}{n} = \sum_{ \geq 0} \frac{1}{2^nn} = \sum_{n \geq 0} \frac{1}{n} (\frac{1}{2})^n = \sum_{n \geq 0} \frac{1}{n+1} (\frac{1}{2})^n\end{align}$
> On note $A(x)$ la limite de la serie entiere $\sum_{n \geq 0} x^n$, si $\overset{\sim}A$ est la primitive de A valant 0 en 0, on a $A(1/2)$ est egal a la valeur de la serie numerique qu'on cherche a calculer.

> Ou $\sum_{n \geq 0} \frac{1}{n+1} (\frac{1}{2})^n$ prend la forme de l'evaluation d'une primitive en un point

$\overset{\sim}A(n) = \sum_{n \geq 0} \frac{x^{n+1}}{n+1}$

$\begin{align}\overset{\sim}A(1/2) &= \sum_{n \geq 0} \frac{1}{n+1} (\frac{1}{2})^{n+1} \\ &= -ln(1 - 1/2) = -ln(1/2) = ln(2)\end{align}$

car
$\sum_{n \geq 0}^{+\infty} x^n = \frac{1}{1 - x}$ sur $]-1, 1[$
$\sum_{n \geq 0}^{+\infty} \frac{x^{n+1}}{n+1} = -ln(1-x)$

## Deriver une serie entiere

==**Proposition**==
Soit une serie entiere $\sum_{n \geq 0}a_nx^n$ de rayon de CV R. f la limite de $\sum_{n \geq 0}a_nx^n$, definie sur $]-R,R[$. La fonction f est derivable sur [a, b] $\in ]-R,R[$ et 
$$f'(x) = \sum^{+
\infty}_{n = 0} na_nx^{n-1}$$
La serie entiere $\sum_{}na_nx^{n-1}$ est de rayon de convergence R.

==**Corollaire**==
La serie entiere $\sum_{n \geq 0}a_nx^n$ est infiniment derivable sur son disque de convergence.

---
## Applications

Quel est le DSE des fonctions suivantes : 
1. $\begin{align}\frac{-x}{(1-x)^2}\end{align}$
2. $\begin{align}\frac{1}{1 + 2n}\end{align}$
3. $\begin{align}ln(1+x)\end{align}$

---
1. $\begin{align}\frac{-x}{(1-x)^2}\end{align}$
- $\frac{1}{1 - x} = \sum^{+\infty}_{n=0} x^n$
- $\frac{1}{1 - ax} = \sum^{+\infty}_{n=0} a_nx^n$
- $\frac{1}{1+x} = \frac{1}{1- (-x)} = \sum^{+\infty}_{n=0}(-1)^nx^n$
- $\frac{1}{(1+x)^2} = \sum^{+\infty}_{n=0} nx^{n-1}$
- $ln(1+x)= \sum^{+\infty}_{n=0}\frac{(-1)^n}{n+1}x^{n+1}$

Donc $\frac{-x}{(1-x)^2} = -x\sum^{+\infty}_{n=0}nx^{n-1} = \sum^{+\infty}_{n=0}-nx^{n}$

---
2. $\frac{1}{1 + 2n} = \sum^{+\infty}_{n=0} (-1)^n2^nx^n$

---
3. $ln(1+x)= \sum^{+\infty}_{n=0}\frac{(-1)^n}{n+1}x^{n+1}$

# Decrire des fonctions usuelles comme series entieres

## Les fonctions developpables en series entieres

==**Definition**==
Une fonction f est **devellopable en serie entiere au point $x_0 \in R$** s'il existe R > 0 tel que opur tout $x \in ]x_0 - R, x_0 + R[$
$$f(x) = \sum_{n=0}^{+\infty} a_n(x - x_0)^n$$

**Remarque**
Quitte a effectuer un changement de variable $x \to x + x_0$

**Proposition**
Une fonction devellopable en serie entiere en un point $x_0$ est infiniment derivable sur son disque de convergence centre en $x_0$

**Proposition**
Si une fonction admet un DSE en $x_0$, les coefficients de ce DSE sont exactement ceux de la serie de Taylor a tout ordre de f en $s_0$.

:::danger
**Rappel (Coefficient de la serie de Taylor en $x_0$)**
Si f est developpable en series entieres en $x_0$, on a
$$f(x) = \sum_{}^{}\frac{f^{(n)}(x_0)}{n!}(x - x_0)^n$$

Ou $\frac{f^{(n)}(x_0)}{n!}$ est le coef de la serie de Taylor de f en $x_0$
En particulier en 0, $\sum_{n=0} \frac{f^{(n)}(0)}{n!}x^n$
:::

## Le DSE des series entieres en zero

- $e^x = \sum_{n=0}^{+\infty}\frac{x^n}{n!}$
- $(1-x)^{-1}$
- $(1-x)^2$
- $sin(x) = \sum_{p \geq 0} \frac{(-1)^pt^{2p+1}}{(2p+1)!}$
- $cos(x) = \sum_{p \geq 0} \frac{(-1)^pt^{2p}}{(2p)!}$

**Demonstration pour sin(x) et cos(x)**
> En realite, les series entieres ont le droit d'avoir une variable complexe.

$$e^{it} = cos(t) + isin(t)$$
$e^{it} = \sum_{n=0}^{+\infty}\frac{(it)^n}{n!}$
> cos(t) = Re(e^{it})
> sin(t) = Im(e^{it})

Pour trouver les DSE de cos(t) et sin(t), il faut identifier les parties reelles et imaginaires de $\sum_{n=0}^{+\infty}\frac{(it)^n}{n!}$

$\begin{align}\sum_{n=0}^{+\infty}\frac{(it)^n}{n!} &= \sum_{p \geq 0} \frac{(it)^{2p}}{(2p)!} + \sum_{p \geq 0} \frac{(it)^{2p+1}}{(2p + 1)!} \\
&= \sum_{p \geq 0} \frac{(i^2)^pt^{2p}}{(2p)!} + \sum_{p \geq 0} \frac{(i^{2p+1})t^{2p+1}}{(2p+1)!} \\
&= \sum_{p \geq 0} \frac{(-1)^pt^{2p}}{(2p)!} + i\sum_{p \geq 0} \frac{(-1)^pt^{2p+1}}{(2p+1)!} \\
&= cos(t) + isin(t)\end{align}$

-------
:::info
Trouver une expression pour le DSE en 0 de $(1 - x)^a$ pour a > 0
:::

$exp(a + b) = exp(a)exp(b)$
$exp(a) = \sum_{n \geq 0} \frac{a^n}{n!}$ et $exp(b) = \sum_{n \geq 0} \frac{b^n}{n!}$
$exp(a)exp(b) = (\sum_{n \geq 0} \frac{a^n}{n!})(\sum_{n \geq 0} \frac{b^n}{n!}) = \sum_{n \geq 0}(\sum_{k=0}^{n} \frac{a^kb^{n-k}}{k!(n-k)!})$
Or 
$\frac{1}{n!}\sum_{n \geq 0}(\sum_{k=0}^{n} \frac{a^kb^{n-k}}{k!(n-k)!}) = \frac{1}{n!}\sum_{k=0}^{n} \frac{n!}{k!(n-k)!} a_kb^{n-k} = \frac{1}{n!}\sum_{k=0}^{n}\binom{n}{k}a^kb^{n-k} = \frac{(a+b)^n}{n!}$

> Ou $\frac{1}{n!}\sum_{k=0}^{n}\binom{n}{k}a^kb^{n-k} = \frac{(a+b)^n}{n!}$ est la formule de Newton

++En reinjectant++ : 
$exp(a)exp(b) = \sum_{n \geq 0} \frac{(a+b)^n}{n!} = exp(a+b)$