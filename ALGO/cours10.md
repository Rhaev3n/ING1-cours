[ALGO] Complexite des algorithmes (10)
===

## Rappel dernier cours

Soit $P(n)$ le nombre de parenthesages de $A_1, A_2 ... A_n$

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
> Nombre de Catalan

$A_i \times A_{i+1} \times ... \times A_j$
> $A_i = P_{i - 1} \times p_i, A_{i+1} = P_i \times P_{i+1}, A_j = p_{j-1} \times p_{j}$
$m(i, i) = 0$
$m(i, i+1) = p_{i-1} \times p_{i} \times p_{i + 1}$
$m(i, j) = min \{ m(i, k) + m(k + 1, j) + p_{i-1}p_kp_j\ | i \leq k < j\}$

$(A_iA_{i+1}...A_j).(A_k)$

||1|2|3|4|5|
|:--:|:--:|:--:|:--:|:--:|:--:|
|1|0|1200|540|640|**840**|
|2||0|240|390|640|
|3|||0|80|260|
|4||||0|100|
|5|||||0|

$m(1,2) = 10 * 15 * 8 = 1200$
$m(2, 3) = 15 * 8 * 2 = 240$
$m(3, 4) = 8 * 2 * 5 = 80$
$m(4, 5) = 2 * 5 * 10 = 100$

$m(1, 3):$ 
- $A_1(A_2A_3) k=1, 0 + 240 + 10 * 15 * 2 = 540$
- $(A_1A_2)A_3 k = 2, 1200 + 0 + 10 * 8 * 2$

$m(2, 4):$
- $A_2(A_3A_4) k = 2, 0 + 80 + 15 * 8 * 5$
- $(A_2A_3)A_4 k = 3, 240 + 0 + 8 * 2 * 10 = 390$

$m(3, 5)$:
- $A_3(A_4A_5) k = 3, 0 + 100 + 8 * 2 * 10 = 260$
- $(A_3A_4)A_5 k = 4, 80 + 0 + 8* 5 * 10$

$m(1, 4)$:
- $A_1(A_2A_3A_4) k = 1, 0 + 390 + 10 * 15 * 15$
- $(A_1A_2)(A_3A_4)$ k = 2, 1200 + 80 + 10 * 8 * 5$
- $(A_1A_2A_3)A_4 k = 3, 540 + 0 + 10 * 2 * 5 = 640$

$m(2, 5)$:
- $k = 2, 0 + 260 + 15 * 8 * 10$
- $k = 3, 240 + 100 + 15 * 2 * 10$
- $k=4, 390 + 0 + 15 * 5 * 10$

$m(1, 5)$:
- $k=1, 0 + 640 + 10 * 15 * 10$
- $k=2, 1200 + 240 + 10 * 8 * 10$
- $k=3, 540 + 100 + 10 * 2 * 10 = 840$
- $k=4, 640 + 0 + 10 * 5 * 10$

## Proprietes des problemes ou la programmation dynamique doit marcher

- Le probleme a une **sous-structure optimale**
	- La solution optimale du probleme est composee de sous-solutions optimale pour des sous-problemes

> Probleme = $A_1A_2A_3A_4A_5$
> Solution optimale = $(A_1(A_2A_3))(A_4A_5)$
> Sous-probleme : $A_1A_2A_3$
> Solution optimale : $(A_1(A_2A_3))$
> etc
> 
Il y a un chevauchement de sous-problemes possibles (justifie le cache)

## Algorithme poissons

:::info
Soient n poissons de poids $p_1, p_2, ... p_n$ et d'apports caloriques $c_1, c_2, ... c_n$.

Comment maximiser le nombre de calories qu'on peut mettre dans un sac de $K$kg ?
:::

Notons $m(n, k)$ le nombre de cal max qu'on peut mettre dans un sac de $k$ kg en choisissant parmi les n premiers poissons

$m(n, 0) = 0$
$m(0, k) = 0$
si $n > 0, k > 0, m(n, k) = \begin{cases}max(c_n + m(n-1, k-p_n), m(n-1, k))\ si\ p_n \leq k \\m(n-1, k)\ si\ p_n > k\end{cases}$ 
> 
> $m(n-1, k-p_n)$ = on prend le poisson n
> $m(n-1, k)$ = on ignore le poisson n


++Exemple++
$p_1 = 2, c_1 = 6$
$p_2 = 4, c_2 = 10$
$p_3 = 6, p_3 = 12$

|n/k|0|2|4|6|8|10|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|0|0|0|0|0|0|0|
|1|0|6|6|6|6|6|
|2|0|6|10|16|16|16|
|3|0|6|10|16|18|22|