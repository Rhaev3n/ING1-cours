[ALGO] Complexite des algorithmes (9)
===

# Programmation dynamique

## Distance de Levenshtein

> Ou distance d'edition (String Edit Distance)

$d(m_1, m_2) =$ nombre min d'operations pour transformer $m_1$ en $m_2$

++Operations++ : 
- Inserer une lettre
- supprimer une lettre
- semplacer une lettre par une autre

++Exemple++ : 
$d(emacs, make)$ = 3
```
supprime e
remplace c->k
remplace s->e
```

$\forall u \in \Sigma^*, d(u, \varepsilon) = |u|$
$\forall v \in \Sigma^*, d(\varepsilon, v) = |v|$

$\forall u \in \Sigma^*, \forall v \in \Sigma^*, \forall a \in \Sigma, \forall b \in \Sigma$

$d(ua, vb) = \begin{cases}d(u, v)\ si\ a = b \\ min(1 + d(u, v), \to remplacer\ a\ par\ b 
\\1 + d(u, vb), \to supprimer\ a\\
1 + d(ua, v) \to inserer\ b)\ si\ a \neq b\end{cases}$


### Solution naive 

```
SED(u, un, v, vn):
if un = 0
    return vn
if vn = 0
    return un
    
if u[un - 1] = v[vn - 1]
    return SED(u, un - 1, v, vn - 1)
else
    d1 <- SED(u, un - 1, v, vn - 1)
    d2 <- SED(u, un - 1, v, vn)
    d3 <- SED(u, un, v, vn-1)
    return 1 + min(d1, d2, d3)
```

> ou d1 = remplacer a par b
> d2 = supprimer a 
> d3 = inserer b
> 
n = un + vn
$T(0) = T(1) = \Theta(1)$
$T(n) \leq T(n - 2) + 2T(n - 1) + \Theta(1)$

$2T(n - 1) + \Theta(1) \leq T(n) \leq 3T(n-1) + \Theta(1)$
$\Theta(2^n) \leq T(n) \leq \Theta(3^n)$

$T(0) = 1$
$T(n) = 2T(n-1) + T(n-2)$

Supposons $T(n) = a^n$
$a^n = 2a^{n-1} + a^{n-2}$
$a^2 - 2a - 1 = 0$
$a = \frac{2 +- \sqrt8}{2} = 1 + \sqrt2$

++Intuition++ : $T(n) = \Theta((1 + \sqrt2)^n)$

Dans notre arbre d'appels, on a $\Theta((1 + \sqrt2)^n)$ sommets

### Memoization

```
SED1(u, un, v, vn):
    un <- |u|
    vn <- |v|
    for i <- 0 to un:
        for j <- 0 to vn:
            cache[i][j] <- -1
    return SED2(u, un, v, vn)
```

```
SED2(u, un, v, vn):
    if cache[un][vn] < 0:
        cache[un][vn] <- SED3(u, un, v, vn)
    return cache[un][vn]
```

```
SED3(u, un, v, vn):
if un = 0
    return vn
if vn = 0
    return un
    
if u[un - 1] = v[vn - 1]
    return SED(u, un - 1, v, vn - 1)
else
    d1 <- SED2(u, un - 1, v, vn - 1)
    d2 <- SED2(u, un - 1, v, vn)
    d3 <- SED2(u, un, v, vn-1)
    return 1 + min(d1, d2, d3)
```

SED1 appelle 1 fois
SED2 appelee au plus 3(un + 1)(vn + 1) + 1 fois
SED3 appelle au plus (un + 1)(vn + 1) fois (la taille du cache)

SED1 $\Theta(1) + \Theta(|u| \times |v|)$
SED2 $\Theta(|u|.|v|)$
SED3 $\Theta(|u| \times |v|)$

Donc $T(n) = \Theta(|u| \times |v|)$
A comparer a $O((1 + sqrt2)^{|u| + |v|})$ sans le cache

### Solution optimale 

```
SED(u, v):
    un <- |u|; vn <- |v|
    for j <- 0 to vn:
        C[0][j] <- j
    for i <- 1 to un
        C[i][0] <- i
        for j <- 1 to vn:
            if u[i - 1] = v[i - 1]
                C[i][j] <- C[i - 1][j - 1]
            else
                C[i][j] <- 1 + min(C[i - 1][j - 1], C[i - 1][j], C[i][j - 1])
    return C[un][vn]
```

Ici $T(n) = \Theta(|u|.|v|)$

## Multiplication de matrices

A1[10 x 100]
A2[100 x 5]
A3[5 x 55]

(A1 x A2) x A3 demande 10x100x5 + 10x5x50 = **7500** multiplications
A1 x (A2 x A3) demande 100x5x50 + 10x100x50 = **75000** multiplications

$\Rightarrow$ ++Le probleme de multiplication de matrices++

Etant donne n matrices A1, A2, ..., An de tailles respectives p0xp1, p1xp2, p2xp3, ..., pn-1xpn
Quel parenthesage du produit A1 x A2 x ... x An minimise le nombre de multiplications scalaires ?

### Implementation naive

1. On enumere tous les parenthesages
2. On evolue chaque parenthesage -> nb de mult
3. On garde le meilleur

Notons P(n) le nombre de parenthesages pour n matrices

P(1) = 1
P(2) = 1
P(3) = 2
P(4) = 5
P(5) = 14

On fait figurer le dernier parenthesage qui sera effectue :

A1 (A2 A3 A4 A5) = 1 x 5
(A1 A2)(A3 A4 A5) = 1 x 2
(A1 A2 A3)(A4 A5) = 2 x 1
(A1 A2 A3 A4) A5 = 5 x 1

P(6) = 42

A1 (A2 A3 A4 A5 A6) = 1 x 14
(A1 A2)(A3 A4 A5 A6) = 1 x 5
(A1 A2 A3)(A4 A5 A6) = 2 x 2
(A1 A2 A3 A4)(A5 A6) = 5 x 1
A1 (A2 A3 A4 A5 A6) =  14 x 1

$P(n) = \sum_{i = 0}^{n - 1}P(i)P(n - i)$