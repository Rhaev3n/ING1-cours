[ALGO] Complexite des algorithmes (8)
===

## Preuve de complexite par recurrence

H1 est vraie 
si H1, H2, ..., Hn-1 sont vraies, alors Hn est vraie 
$\Rightarrow \forall n \geq 1$, Hn est vraie

### Prouver que T(n) = O(f(n))

1. Poser l'hypothese Hn : "$T(n) \leq cf(n)$ pour un $c > 0$ (qu'on peut choisir aussi grand qu'on veut)"

2. Montrer que $H_{n_0}$ est vraie (cas de base)

3. Supposer $H_{n_0}, H_{n_0+1}, ..., H_{n - 1}$ et montrer que $H_n$ est vraie

4. Conclure que $\forall n \geq n_0$ Hn vraie et $\forall n \geq n_0 T(n) \leq cf(n)$ donc T(n) = O(f(n))

### Applications 

++Exemple 1++ : 

$T(n) = 
\begin{cases} 
\Theta(1)\ si\ n = 1 \\ T(\lfloor n/2 \rfloor) + \Theta(1)\ si\ n > 1 
\end{cases}$

---------
Intuition : $T(n) = O(log\ n)$ ?

$H_n = "T(n) \leq c\ log_2n"$

$H_1 : "T(1) \leq \Theta(1) \leq c\ log_2 1 = 0$
$\Rightarrow\ H_1$ est fausse

$H_2 : "T(2) \leq T(1) + \Theta(1) \leq \Theta(1) = \Theta(1) \leq c\ log_22 = c"$
> Ou c existe par definition de $\Theta(1)$

$\Rightarrow\ H_2$ est vraie

$H_3 : "T(3) \leq T(1) + \Theta(1) = \Theta(1) \leq c\ log_23"$

----
**Cas general** : 
Pour $n \geq 4$, on suppose $H_1, H_2, H_3, ..., H_{n-1}$
$T(n) \leq T(\lfloor n/2\rfloor) + \Theta(1)$
$T(n) \leq c\ log_2(\lfloor n/2\rfloor) + \Theta(1) \leq c\ log_2(n/2) + \Theta(1)$
$T(n) \leq c\ log_2n - (c - \Theta(1)$
> Ou $(c - \Theta(1) \geq 0$ si c est choisi assez grand pour dominer $\Theta(1)$
$T(n) \leq c\ log_2n$

Donc $H_n$ est vraie.

On a montre $\forall n \geq n_0, T(n) \leq c\ log_2 n$
Donc $T(n) = O(log\ n)$

--------------
++Exercice 2++ : 

$T(n) = \begin{cases} 1 \\ 2T(\lfloor n/2\rfloor) + 2\end{cases}$

----------
Intuition : $T(n) = \Theta(n)$

On essaye de montrer $T(n) = O(n)$ par recurrence

$H_n : "T(n) \leq cn"$
$H_1 : T(1) = 1 \leq c \Rightarrow$ vraie
$H_2 : T(1) = 2T(1) + 1 = 3 \leq c \Rightarrow$ vraie

Pour $n \geq 3$, on suppose $H_1, H_2, ..., H_{n-1}$

$T(n) = 2T(\lfloor n/2\rfloor) + 1$
> On applique notre hypothese $H_{\lfloor n/2 \rfloor} \to$

$T(n) \leq 2c\lfloor n/2\rfloor + 1$
$T(n) \leq cn + 1$

> On veut supprimer le + 1
> Hypothese pas suffisamment precise ? On soustrait le terme qui nous derange dans l'hypothese de depart 

-----
$H_n : "T(n) \leq cn - 1"$
$H_1 : T(1) = 1 \leq c - 1 \Rightarrow$ vraie (pour c suffisamment grand)
$H_2 : T(1) = 2T(1) + 1 = 3 \leq c2 - 1 \Rightarrow$ vraie

$\forall n \geq 3$, on suppose $H_1, H_2, ..., H_{n-1}$

$T(n) \leq 2T(\lfloor n/2\rfloor) + 1$
> On applique notre hypothese $H_{\lfloor n/2 \rfloor} \to$

$T(n) \leq 2(c\lfloor n/2\rfloor - 1) + 1$
$T(n) \leq cn - 2 + 1$
$T(n) \leq cn - 1$

$\Rightarrow H_n$ vraie
Donc $T(n) = O(n)$

## Selection de la valeur de rang k

> k-ieme plus petite valeur

rang 0 = min
rang n - 1 = max
rang $\lfloor n/2\rfloor$ = mediane

++Exemple++ : 
On veut k = 4
|        2 3 4 7 9 2 5 7         |
|:------------------------------:|
|  **2** 3 4 **7** 9 2 5 **7**   |
| **2** 3 **4** 7 5 **2** \| 9 7 |
|              k =4              |
|   2 \| **3** 4 **7** 5 **2**   |
|              k =3              |
|    2 \| **4** **7** 5 **3**    |
|              k =2              |
|           3 \| 7 5 4           |
|             k = 1              |
|            4 \| 5 7            |
|             k = 0              |
|             5 \| 7             |

```
Selection(A, b, e, k)
// retourne la valeur de rang k dans A[b...e-1]
// 0 <= k < e - b
if (e - b) == 1
    return A[b]
else
    m <- Partition(A, b, e)
    l <- m - b
    if (k < l)
        return Selection(A, b, m, k)
    else
        return Selection(A, m, l, k - l)
```

| Ligne de code                    | Cout        |
| -------------------------------- | ----------- |
| if (e - b) == 1 return A[b]      | $\Theta(1)$ |
| m <- Partition(A, b, e)          | $\Theta(n)$ |
| l <- m - b                       | $\Theta(1)$ |
| return Selection(A, b, m, k)     | $T(l)$      |
| return Selection(A, m, l, k - l) | $T(n-l)$    |

**Meilleur cas** : 

$T(1) = \Theta(1)$
$T(n) = \Theta(n) + T(1)$
$T(n) = \Theta(n) + \Theta(1)$
Donc $T(n) = \Theta(n)$

**Autre cas (favorable)** :

$T(1) = \Theta(1)$
$T(n) = \Theta(n) + T(n/2)$
Donc $T(n) = \Theta(n)$

**Pire cas** : 

$T(1) = \Theta(1)$
$T(n) = \Theta(n) + T(n - 1)$
Donc $T(n) = \Theta(n^2)$

**Cas moyen** : 

$T(n) \leq \Theta(n) + \frac{1}{n-1} \sum_{l=1}^{n-1} max(T(l), T(n-l))$
> Moyenne sur tous les cas possibles 

$T(n) \leq \Theta(n) + \frac{2}{n-1} \sum_{l = \lfloor n/2 \rfloor}^{n-1} T(l)$

Intuition : $T(n) = O(n)$

$H_n : "T(n) \leq cn"$ 
$H_1 : T(1) = \Theta(1) \leq c$

$\forall n \geq 2$, supposons $H_1, H_2, ..., H_{n-1}$
$T(n) \leq \Theta(n) + \frac{2}{n-1} \sum_{l = \lfloor n/2\rfloor}^{n-1} T(l)$
> On applique notre hypothese $H_l \to$

$T(n) \leq \Theta(n) + \frac{2}{n-1} \sum^{n - 1}_{l = \lfloor n/2\rfloor}cl$

> $\sum^{n-1}_{l = \lfloor n/2\rfloor}l \leq (3 / 8)n^2$

$T(n) \leq \Theta(n) + \frac{2 \times 3 \times c \times n^2}{8 \times (n-1)} = \Theta(n) + \frac{3c}{4} \frac{(n - 1 + 1)n}{n - 1}$
$T(n) \leq \Theta(n) + \frac{3c}{4} + \frac{3c(n - 1 + 1}{4(n-1)} = \Theta(n) + \frac{3cn}{4} + \frac{3c}{4}+ \frac{3c}{4(n-1)}$
$T(n) \leq cn - (\frac{cn}{4} - \Theta(n) - \frac{3c}{4} - \frac{3c}{4(n-1)})$
> Ou $(\frac{cn}{4} - \Theta(n) - \frac{3c}{4} - \frac{3c}{4(n-1)}) \geq 0$ si c choisi assez grand

$T(n) \leq cn$
$T(n) = O(n)$

Par ailleurs, a cause de l'appel a Partition, $T(n) = \Omega(n)$ donc $T(n) = \Theta(n)$

:::info
On veut une meilleure complexite pour le pire cas >> **IntroSelect**
:::