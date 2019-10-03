Series entieres (1)
===

// lien moodle
Evaluations formatives (QCM etc) : 10% de la note du cours

## Objectifs

- Etudier des valeurs/quantites discretes (ex: coefficients binomiaux $\binom{n}{k}$ pour  $k \in \mathbb{N}, k \leq n$) en les stockant dans un objet permettant de les manipuler plus facilement
> $$P(X) = \sum_{k \geq 0}^{k = n} \binom{n}{k}X^k = (1 + X)^n$$

> $\sum_{k = 0}^{n} \binom{n}{k} = 2^n$
> $P(X) = \sum_{k = 0}^{n} \binom{n}{k}X^k = (1 + X)^n$
> $P(1) = (1 + 1)^n = 2^n$

- Comprendre l'interet des series entieres
- Les manipuler dans un contexte probabiliste (Savoir manipuler des dataset)
- Connaitre l'utilite d'un DES en calcul numerique
- Determiner le lieu ou les raisonnements avec une serie numerique ont un sens

## Encoder des familles de grandeurs discretes

#### Fonction generatrice d'une loi binomiale

*Experience aleatoire* qui consiste a jeter une piece *n* fois. La proba d'obtenir pile etant $p\in{]0, 1[}$. On note X le nombre de fois qu'on obtient pile. Proba que X soit egale a $k\in{[0, n]}$ s'ecrit :

$$P(X = k) = \binom{n}{k}p^k(1 - p)^{n - k}$$
 
> k parmi n : le nombre k de fois qu'on a pile parmis n jets de piece
 
> X est la variable aleatoire (nombre de pile) -> X((P, F)) = 1
> Donc P(X=1) : combien de fois X renvoie k
 
Les donnees P(X=k) caracterisent completement la variable aleatoire X. Une maniere de **stocker** l'information relative a l'ensemble des valeurs de la loi de X est de construire le polynome : 

$$E(e^x) = \sum^{n}_{k=0} P(X = k)x^k = ((1 - p) + px)^n$$
 
C'est ce qu'on appelle la ==**fonction generatrice de X**==
 
> $(x + y)^n = \sum^{n}_{k=0} \binom{n}{k}x^ky^{n-k}$px
> $E(e^x) = \sum^{n}_{k=0} \binom{n}{k}(px)^k(1 - p)^{n - k} = ((1 - p) + p(x))^n$
 
Comprendre une variable aleatoire passe en particulier par le fait de comprendre son **esperance** et sa **variance**, respectivement donnees par : 
$$E(X) = \sum_{k >= 0} k\binom{n}{k} p^k(1-p)^{n - k}$$
$$V(X) = \sum_{k >= 0} k^2\binom{n}{k} p^k(1-p)^{n - k} - E(X)^2$$

> Esperance: somme pour chaque etudiant de sa note que je multiplie par la probabilite que j'obtienne cette note
------
:::warning
Calculer E(X)
:::

:::danger
**Rappel (calcul k parmi n)** : $$\binom{n}{k} = \frac{n!}{k!(n - k)!}$$
:::

> $\sum^{n}_{k=0} \binom{n}{k}x^ky^{n-k}$
$G(x) = \sum^{n}_{k=0} \binom{n}{k}p^k(1 - p)^{n - k}x^k = ((1 - p) + px)^n$


> ++On derive G (on veut drop les puissances)++
$G'(x) = \sum^n_{k=0}k\binom{n}{k}p^k(1 - p)^{n - k}x^{k - 1}$
$G'(1) = \sum^n_{k=0}k\binom{n}{k}p^k(1 - p)^{n - k}$

>$G(x) = ((1 - p) + px)^n$
>$G'(x) = n((1 - p) + px)^{n - 1} * p$
>$G'(x) = np((1 - p) + px)^{n - 1}$ 
> $G'(1) = np((1 - p) + p * 1)^{n - 1} = np * (1)^{n - 1} = np$

## Fonction generatrice d'une loi geometrique

On s'interesse a l'experience aleatoire consistant a jeter une piece autant de fois qu'on le souhaite, la probabilite d'obtenir pile est $p \in{]0,1[}$. On note Y la variable aleatoire correspondant a la premiere fois ou l'on obitent pile. La loi de Y s'exprime pour tout $k \in{\mathbb{N}^*}$ par : 

$$P(Y = k) = (1 - p)^{k - 1}p$$

Si on souhaite exrire la *fonction generatrice de Y*, on retrouve les symboles (pour l'instant depourvus de sens) : 
$$E(e^Y) = \sum_{k \geq 1} P(Y = k)x^k = \sum_{k \geq 1} (1 - p)^{k - 1}px^k$$

Cette ecriture en *polynome infini* est qualifiee de ==**serie entiere**==

-----
:::warning
Justifier informellement la relation suivante
$E(e^x) = \frac{px}{1 - (1 - p)x}$
:::

$G(x) = \sum_{k \geq 1} (1 - p)^{k - 1} px^k$


$\begin{align}
\sum_{k = 1}^N (1 - p)^{k - 1} px^k & = \sum_{k = 1}^N ((1 - p)x)^{k - 1} px \\
& = px \sum_{k = 1}^N ((1 - p)x)^{k - 1} \\
& = px (\frac{1 - ((1 - p)x)^{N}}{1 - (1 - p)x})
\end{align}$

:::danger
**Rappel (suite geometrique)**
$$\sum^{N}_{k=0} y^k = \frac{1 - y^{N+1}}{1 - y}$$
:::

> Ici, 
$((1 - p)x)^{N} \to \frac{px}{1 - (1 - p)x}$

> Si 
$\begin{align}
|x| > \frac{1}{1 - p} \rightarrow G(x) & = \sum_{k \geq 1} p(1 - p)^{k - 1}x^k \\ 
& = \frac{px}{1 - (1 - p)x}
\end{align}$

> Alors
$\begin{align}
G'(x) = \frac{p}{(1 - (1 - p)x)^2}
\end{align}$

> $\begin{align}
(\frac{px}{1 - (1 - p)x})' & = \frac{p(1 - (1 - p)x) - (-(1 - p))px}{(1 - (1 - p)x)^2} \\
& = \frac{p - (1 - p)px + (+(1 - p)px)}{(1 - (1 - p)x)^2}
\end{align}$

$G'(x) = \frac{p}{(1 - (1 - p)x)^2} \Rightarrow G'(1) = \frac{1}{p}$
    
> En faisant une serie entiere, on prend une suite de # (ex: $p(1 - p)^{k - 1}$) qu'on transforme en polynome infini, donc en serie entiere (ici $\sum_{k \geq 1} p(1 - p)^{k - 1}x^k$) $\to$ on calcule des sommes des termes de ces suites

    En deduire expression pour l'esperance de Y, ecrite 

$E(e^Y) = \sum_{k \geq 1} k(1 - p)^{k - 1}p$

## La notion de serie entiere

==**Definition (Serie entiere)**==
on se donne une suite de nombres reels $(a_n)_{n \geq 0}$. On appelle **serie entiere** la suite des *sommes partielles* associee a une suite de fonctions de la forme $(a_nx^n)_{n \geq 0}$, elle est notee $\sum_{n \geq 0} a_nx^n$ . Sur le lieu des valeurs de $x$ ou $\sum_{n \geq 0}a_nx^n$ converge on note : 

$$\sum^{+\infty}_{n = 0} a_nx^n$$

La fonction qui a $x$ associe la limite de la serie numerique $\sum_{n \geq 0}a_nx^n$

> **Exemple** fondamental des series entieres : la serie geometrique
$$\sum_{n \geq 0} x^n$$
> Si $|x| < 1, \to \frac{1}{1 - x}$

:::warning
La suite $\sum_{k \geq 1} (-1)^n$ converge ou diverge ?
:::

$\sum x^n$ : 
- Converge ssi $x \in ]-1; 1[$
- Diverge ssi $x \in ]-\infty; -1[$ ou $x \in ]1; +\infty[$
- Cas des points du bord (1 et -1) ??
- Ici, le rayon de la serie entiere est 1 (]-1;0] ou [0;1[)

:::warning
Trouver des series respectivement de rayons de convergence 0, 1, 2 et $+\infty$
:::

:::warning
Trouver des series convergentes : 
- Sur les bords du disque de convergence
- En un seul point de convergence
- En aucun point du bord
:::