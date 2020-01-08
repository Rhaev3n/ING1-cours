[ALGO] Complexite des algorithmes (11)
===

$V = \{1, 2, 5, 10, 20, 50\}$ valeurs de pieces
$m=10$ montant a rendre

11 facons : 
- $10 * 1c$
- $5 * 1c$
- $2 * 5c$
- $1 * 10c$
- $4 * 2c + 2 * 1c$
- $3 * 2c + 4 * 1c$
- $3 * 2c + 6 * 1c$
- $2 * 2c + 6 * 1c$
- $1 * 2c + 8 * 1c$
- $2 * 2c + 1 * 5c + 1 * 1c$
- $1 * 5c + 3 * 1c + 1 * 2c$

$cc(n, m)$ = le nombre de facons de rendre $m$ avec les $n$ permieres pieces

On note $p_1, p_2, ..., p_n$ les valeurs de $n$ pieces

$cc(0, m) = \begin{cases}1\ ssi\ m=0\\ 0\ ssi\ m > 0\end{cases}$
$cc(n, 0) = 1$
$cc(n, m) = \begin{cases}cc(n, m - pn) + cc(n-1, m)\ si\ m \geq pn \\ cc(n-1, m)\ si\ m < pn\end{cases}$
> $cc(n, m - pn)$ = on prend les pieces
> $cc(n-1, m)$ = on ignore les pieces

|||0|1|2|3|4|5|6|7|8|9|10|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:
||**0**|1|0|0|0|0|0|0|0|0|0|0|
|5c|**1**|1|0|0|0|0|1|0|0|0|0|1|
|2c|**2**|1|0|1|0|1|1|1|1|1|1|2|
|10c|**3**|1|0|1|0|1|1|1|1|1|1|3|
|1c|**4**|1|1|2|2|3|4|5|6|7|8|11|

```c=
unsigned cc(const unsigned *values, unsigned count, unsigned amount)
{
    unsigned *res = calloc(amount + 1, sizeof *res);
    res[0] = 1;
    for (unsigned i = 0; i < count; i++)
    {
        unsigned val = values[i];
        for (unsigned j = val; j < amount; j++)
        res[j] += res[j - val];
    }
    unsigned r = res[amount];
    free(res);
    return r;
}
```

## Algos

- Tris comparatifs
    - Selection Sort
    - Insertion Sort
    - Merge Sort
    - Heap Sort
    - Quick Sort
    - Intro Sort
- Tris non comparatifs
    - Counting Sort
    - Radix Sort LSC (iter)
    - Radix Sort MSD (rec)
- Selection - Quick Select
- Prog dynamique
    - Distance de Levensthein
    - Cherche Mult Mat
    - Sacs a dos
- En TD
    - Strassen
    - Huffman
    - FastPow

## Outils pour la complexite

- Savoir compter les iterations de boucles imbriquees
    - (1 boucle = 1$\Sigma$)
- Recurrence du type $T(n) = T(n/a) + f(n)$
    - Theoreme general
    - Dessiner l'arbre + comptes
    - Faire des substitutions
    - Preuves par recurrence (deviner avant de prouver)
- Recurrences du type $T(n) = T(n - b) + f(n)$
    - Dessiner l'arbre + comptes
    - Faire des substitutions
    - Preuves par recurrence (deviner avant de prouver)
- Recurrences du type $T(n) = aT(n-1) + bT(n-2)$
    - Supposer $T(n) = x^n$
    - $x^2 - ax - b = 0$
