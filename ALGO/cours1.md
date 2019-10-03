[ALGO] Complexite des Algorithmes (1)
===

[// cours pdf](https://www.lrde.epita.fr/~adl/ens/algo/algo.pdf)

++QCM++
- Cours 2
- 1er cours apres l'atelier A_ALGO
- **A points negatifs**

++NOTE ATELIER ALGO++
- 25% QCM 1
- 25% TP Atelier Algo
- 50% QCM2

---------------------
==**Problematique**==

**Algorithme** : sequence d'instruction qui resoud un probleme

**Problemes** : 
- Trouver le minimum d'un tableau de $n$ valeurs
- Trouver un mot dans un dictionnaire de $n$ mots
- Parametres par une taille

**==Complexite temporelle== d'un algorithme** : 
$T_{algo}(n)$ = temps pour resoudre un probleme de taille $n$
> Faire des choix entre des algos, ou des predictions sur le comportement des algo avec un n donne


$$A(n) = \sum^{n}_{i = 0} i = ?$$
> On a $A(n) = 1 + 2 + ... + n - 1 + n$
> Donc $2A(n) = (n + 1)n$
> Donc $A(n) = \frac{n(n + 1)}{2}$

-------------
## Les sommes

**Formule de la somme** : 
$$\frac{(premier_{terme} + dernier_{terme}) * nb_{terme}}{2}$$

\begin{align}
\sum^{n}_{i = 0} (i + 1)^2 & \to \sum ^{n + 1}_{i = 1} i^2 = \sum^{n}_{i = 1} i^2 + (n + 1)^2\\
& \to \sum^{n}_{i = 0}(i^2 + 2i + 1) = \sum^{n}_{i = 0}i^2 + \sum^{n}_{i = 0}i + \sum^{n}_{i =0}1
\end{align}

$(n + 1)^2 = 2(\sum^{n}_{i=0}i) + (n + 1)$
$\frac{(n + 1)n}{2} = \sum^{n}_{i=0}i$


\begin{align}
\sum^{n}_{i-0}i^3 & \to (\sum^{n}_{i=0}i^3) + (n + 1)^3\\
& \to \sum^{n}_{i=0} (i^3 + 3i^2 + 3i + 1) = \sum^{n}_{i=0}i^3 + 3\sum^{n}_{i=0}i^2 + 3\sum^{n}_{i=0}i + (n + 1)
\end{align}

$(n+1)^3 = 3\sum^{n}_{i=0}i^2 + \frac{3n(n + 1)}{2} + \frac{2(n + 1)}{2}$
Avec $\frac{3n(n + 1)}{2} + \frac{2(n + 1)}{2} = \frac{(3n + 2)(n + 1)}{2}$

$\begin{align}
3\sum^{n}_{i=0}i^2 & = (n + 1)^3 - \frac{(3n+2)(n + 1)}{2} \\
& = \frac{2(n + 1)(n + 1)^2}{2} - \frac{(n + 1)(3n + 2)}{2}
\end{align}$

$\begin{align}
\sum^{n}_{i=0}i^2 & = \frac{(n + 1)}{6}(2(n+1^2) - (3n + 2)) \\
& = \frac{(n + 1)}{6}(2n^2 + 4n + 2 -3n - 2) \\
& = \frac{n(n + 1)}{6}(2n + 1)
\end{align}$

$\begin{align}
S(n) & = \sum^{n}_{i=0}x^i \\
& = \frac{1 - x^{n + 1}}{1 - x} \to_{x \to 1} n + 1
\end{align}$

> $S(n) = x^0 + x^1 + x^2 + ... + x^n$
> $xS(n) = x^1 + x^2 + ... + x^n + x^{n + 1}$
> $(1 - x)S(n) = x^0 - x^{x + 1}$

------------------
## Les logarithmes

$log_{10} (1234) = a,bc$ ou $a = 3$ car $log_{10}(1000) = log_{10}(10^3) = 3$
$log_{10} (1234) - 3 = 0,bc$
$log_{10} (\frac{1234}{1000}) = 0,bc$
$log_{10} (1,234) = 0,bc$
$log_{10} (1,234^{10}) = b,c$ ou $1,234^{10} = 8,1875$
$log_{10} (8,1875) = b,c$
$log_{10} (8,1875) = 0,c$ car $8,1875 < 10$
$log_{10} (8,1875^{10}) = c,$
$log_{10} (1353679866,79) = 9,$ (nb de chiffers devant la virgule - 1)
Donc $log_{10} (1234) = 3,09$

$log_2(1234) = a,bc$
$log_2(1234) = 10,bc$ car $log_2(1024) = 10$
$log_2(\frac{1234}{1024}^{10}) = b,c$
$log_2(6,4588) = 2,c$ car $log_2(4) = 2$ et $log_2(8) = 3$
$log_2(\frac{6,4588}{4}^{10}) = c,$
$log_2(120,48) = 6$

> $^{10}$ -> decale la virgule de l'autre cote de l'equation

--------------------
## Exemples concrets
```c 
void fun(int n)
{
    for (int i = 5; i <= n; ++i)
    {
        puts("A");
        for (int j = 10; j < 20; ++j)
            puts("B")
        for (int j = 1; j < i; ++j)
            puts("C");
        for (int j = 10; j < i; ++j)
            puts("D");
    }
}
```

:::warning
Calculer combien de fois chaque lettre est affichee ?
:::

    Avec 10 
- A(10) = 5
- B(10) = 50
- C(10) = 30
- D(10) = 0

------------

    Avec n quelconque
$\begin{align}
A(n) = \sum^{n - 1}_{i=5} 1 = \begin{cases}
n - 5\ ssi\ n > 5 \\
0\ sinon
\end{cases}
\end{align}$

$\begin{align}
B(n) = \sum^{n-1}_{i=5} \sum^{19}_{j=10} 1 = \sum^{n-1}_{i=5} 10 = 
\begin{cases}
10(n - 5)\ ssi\ n > 5\\
0\ sinon
\end{cases}
\end{align}$

$\begin{align}
C(n) & = \sum^{n-1}_{i=5} \sum^{i - 1}_{j=i} 1 = \sum^{n-1}_{i=5} (i - 1) \\
& = 
\begin{cases}
\frac{(4 + n -2)(n - 5)}{2} = \frac{(n - 5)(n + 2)}{2} si n > 5 \\
0\ sinon
\end{cases}
\end{align}$

$\begin{align}
D(n) & = \sum^{n-1}_{i=5} \sum^{i - 1}_{j=10} 1 = \sum^{n-1}_{i=11} (i - 10) \\
& = 
\begin{cases}
\frac{(1 + n - 11)(n - 11)}{2} = \frac{(n - 10)(n - 11)}{2}\ ssi\ n >= 12 \\
0\ sinon
\end{cases}
\end{align}$

-----

```c 
for (int i = 1; i < n; ++i)
    for (int j = 1; j < i; j += 2)
        puts("E");
```

:::warning
Comment calculer E(n) ici ?
:::

On a j = 1, 3, 5, 7, 9... < i
Changement de variable avec : 
$j = 2k + 1 < i \iff 2k < i - 1 \iff k < \frac{i - 1}{2}$ (partie entiere sup)

> $i < x$ -> On prend la partie entiere superieure de x
> $i \leq x$ -> On prend la partie entiere inferieure de x

```c 
for (int i = 1; i < n; ++i)
    for (int k = 0; k < (i - 1) / 2; ++k)
        puts("E");
```

$\begin{align}
E(x) &= \sum^{n-1}_{i=1} \sum_{k=0}^{\lceil\frac{i - 1}{2}\rceil - 1} 1 \\
& = \sum^{n-1}_{i=1} \lceil\frac{i-1}{2}\rceil \\
& = \sum^{n - 2}_{i=0} \lceil\frac{i}{2}\rceil = \sum^{n - 2}_{i = 1} \lceil\frac{i}{2}\rceil \\
& = 1 + 1 + 2 + 2 + 3 + 3 +... + \lceil\frac{n - 2}{2}\rceil
\end{align}$

>Si n est pair, tous les termes sont en double
$E(n) = 2 \sum^{\frac{n-2}{2}}_{i=1}i = (1 + \frac{n}{2} - 1)(\frac{n}{2} - 1) = \frac{n(n - 2)}{4}$

> Si n est impair 
$E(n) = E(n - 1) + \lceil\frac{n - 2}{2}\rceil = \frac{(n - 1)(n - 3)}{4} + \frac{n - 1}{2} = \frac{(n - 1)^2}{4}$
