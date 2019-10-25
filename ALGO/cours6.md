[ALGO] Complexite des algorithmes (6)
===

### Ecrire T(n) en fonction de T(n-1)

$T(n) = cn + \sum_{i=1}^{n-1}T(i)$
$T(n-1) = c(n-1) + \sum_{i=1}^{n-2}T(i)$

$T(n) - T(n-1) = c + T(n-1)$
$T(n) = 2T(n-1) + c$
$\ \ \ \ \ \ \ \ = 2(2T(n-2) + c) + c$
$\ \ \ \ \ \ \ \ = 4T(n-2) + 2c + c$
$\ \ \ \ \ \ \ \ = 8T(n-3) + 4c + 2c + c$
$\ \ \ \ \ \ \ \ = 2^{n-1}T(1) + 2^{n-2}c + 2^{n-3}c + ... + 2c + c$

$\ \ \ \ \ \ \ \ = \Theta(2^{n-1}) + c\frac{2^{n-1}}{1}$
$\ \ \ \ \ \ \ \ =\Theta(2^{n-1}) = \Theta(2^n)$

## QuickSort en moyenne

$T(n) = \Theta(n) + T(l) + T(n-l)$
> Ou T(l) = rec a gauche et T(n-l) = rec a droite.

- Les valeurs possibles de l : toutes les valeurs de $[1, n-1]$

++En moyenne++

$T(n) = \Theta(n) + \frac{1}{n-1}sum_{l=1}^{n-1}(T(l) + T(n-l))$

$T(n) = \Theta(n) + \frac{2}{n-1}\sum_{l=1}^{n-1}T(l)$

$(n-1)T(n) = cn(n-1) + 2\sum_{l=1}^{n-1}T(l)$
$(n-2)T(n) = c(n-1)(n-2) + 2\sum_{l=1}^{n-1}T(l)$

$(n-1)T(n) - (n-2)T(n-1) = 2c(n - 1) + 2T(n-1)$
$(n-1)T(n) = nT(n-1) + 2c(n-1)$
On divise par (n(n-1)) : $\frac{T(n)}{n} = \frac{T(n-1)}{n-1} + \frac{2c}{n}$

ON pose $U(n) = \frac{T(n)}{n}$
$U(n) = U(n-1) + \frac{2c}{n}$
$= U(n-2) + \frac{2c}{n-1} + \frac{2c}{n}$
$= U(1) + \frac{2c}{2} + \frac{2c}{3} + ... + \frac{2c}{n}$
$= \Theta(1) + 2c\sum_{i=2}^{n}\frac{1}{i}$
$= \Theta(1) + 2c \times \Theta(log n)$

$U(n) = \Theta(log n)$

$T(n) = n \times U(n) = \Theta(n log n)$

### Comparaison

||QuickSort|MergeSort|
|:---:|:---:|:---:|
|Best|$\Theta(nlogn)$|$\Theta(n log n)$|
|Any|$\Theta(nlogn)$|$\Theta(n log n)$|
|Worst|$\Theta(n^2)$|$\Theta(n log n)$|

### Partition de QuickSort

```
QuickSort(A,b,e)
    if e - b > 1:
        m = Partition(A,b,e)
        QuickSort(A,b,m)
        QuickSort(A,m,e)

```

```
Partition(A,b,e):
    i <- b - 1; j <- e; p = A[b]
    for ever:
        do ++i until A[i] >= p
        do --j until A[j] <= p
        if i < j
            A[i] <-> A[j]
        else
            return i + (b == i)
```

:::info
Recherche du pivot ideal pour Partition
:::

Pivot ideal = Mediane du tableau

---
**Recursion terminale** : Le dernier appel recursif n'est suivi d'aucune autre operation avant le return.

```
int fac2(int n, int acc):
start:
    if (n <= 1)
        return acc;
    acc = n * acc;
    n = n - 1;
    goto start;
```

```
int fac2(int n, int acc)
    while (n <= 1) {
        acc *= n;
        n--;
    }
    return acc;
```

### Optimisations de QuickSort

```
QS(A, b, e):
    while (e - b > 1)
        n <- Partition(A, b, e)
        QS(b, m)
        b <- m
```

> Ne change pas la complexite mais on gagne en memoire dans le cas d'un tableau trie a l'endroit : On passe de $\Theta(n)$ recursions a $\Theta(1)$
> 

:::danger
**Optimisation 1** : 
Faire l'appel recursif sur le plus petit cote, et faire une boucle sur l'autre cote
:::

```
QS(A, b, e):
    while e - b > 1:
        m <- Partition(A, b, e)
        if m - b > e - m:    
            QuickSort(A, m, e)
            e <- m
        else
            QuickSort(A, b, m)
            b <- m
```

- Nombre max d'appels recursifs empiles : $log_2n$ au lieu de $n-1$

$\Rightarrow$ On consomme moins de pile !

```
QuickSort'(A, b, e):
    while e - b > 4:
        m <- Partition(A, b, e)
        if m - b > e - m:    
            QuickSort'(A, m, e)
            e <- m
        else
            QuickSort'(A, b, m)
            b <- m
    InsertionSort(A, b, e)
    
QuickSort(A, n):
    QuickSort'(A, 0, n)
    InsertionSort(A, n)
```

> Andrei Alexandrescu - CPPCOM 2019