[PROBA] Probabilites Discretes (last)
===

++Exercice++

On dispose de 2 urnes $U$ et $V$
U possede a boules blanches et b boules noires
V possede b boules blanches et a boules noires

$\implies$ Tirage avec remise

$U_n$ : "Le n-ieme tirage s'effectue dans U"
$V_n$ : "Le n-ieme tirage s'effectue dans V"
$B_n$ : "La n-ieme boule tiree est blanche"

Si a l'etape n, on a tire une boule blanche, prochain tirage dans U, sinon dans V

1. Calculer $P(B_{n+1}/B_n)$ et $P(B_{n+1}/\overline{B_n})$

$P(B_{n+1}/B_n) = P(B_{n+1}/U_{n+1}) = \frac{a}{a+b}$
$P(B_{n+1}/\overline{B_n}) = P(B_{n+1}/V_{n+1}) = \frac{b}{a+b}$

2. $P_n = P(B_n)$. Trouver la relation de recurrence entre $P_n$ et $P_{n+1}$

$B_{n+1} = (B_{n+1} \cap B_n) \cup (B_{n+1} \cap \overline{B_n})$
$\begin{align}P(B_{n+1}) &= P(B_{n+1} \cap B_n) + P(B_{n+1} \cap \overline{B_n}) \\ &= P(B_{n+1}/B_n)P(B_n) + P(B_{n+1}/\overline{B_n})P(\overline{B_n})\end{align}$

$\begin{align}P_{n+1} &= (\frac{a}{a+b})P_n + (\frac{b}{a+b})(1 - P_n) \\ &= \frac{a-b}{a+b}P_n + \frac{b}{a+b} = f(P_n)\end{align}$

>On cherche le point fixe $l = f(P_n)$

Supposons que $P_n$ est convergente avec $l$ sa limite
$l$ est un point fixe : $l = f(l) \implies l = \frac{a-b}{a+b}l + \frac{b}{a+b}$

$f(x) = \frac{a-b}{a+b}x + \frac{b}{a+b}$

$(a+b)l = (a-b)l + b$
$\iff 2bl = b$
$\iff l = 1/2$

3. Montrer que $P_n \underset{n \to +\infty}\to 1/2$

Montrons que la suite $P_n$ est convergente

Posons $Q_n = P_n - 1/2$
$Q_{n+1} = (\frac{a-b}{a+b})Q_n \implies$ suite geometrique de raison $\frac{a-b}{a+b}$

Or $\frac{a-b}{a+b} < 1 \implies q_n \underset{n \to +\infty}\to 0 \implies P_n \underset{n \to +\infty}\to 1/2$

## Fonctions Generatrices

==**Definition**== 

$X$ est une variable aleatoire definie sur un espace probabilise $(\Omega, \mathcal{C}, \mathcal{P})$ telle que $X(\Omega) \subset \mathbb{N}$

$X(\Omega) = \{valeurs\ de\ X\}$
On definit sa **fonction generatrice** $g_X(t) = \sum_{-\infty}^{+\infty}t^nP(X=n)$

:::info
**Remarque**

$g_X(t) = E(t^X)$ (lorsqu'elle existe)
$g_X(t) = \sum_{n=0}^{+\infty}t^nP(X=n)$ serie entiere

$\sum_{n=0}^{+\infty} a_nt^n\ \ \ a_n = P(x=n)$
:::

Soit $R_X$ le rayon de convergence
Donc la serie converge sur $]-R_X,R_X[$

$g_X(1) = \sum_{0}^{+\infty}P(X=n) = 1$
$g_X(1) = 1 \implies R_X \geq 1$ (rayon de CV)

++Exemple++

Soit $X$ qui suit la loi $\mathcal{P}(X)$ (Loi de Poisson)

1. Calculer $g_X(t)$

$\begin{align}g_X(t) &= \sum_{n=0}^{+\infty}t^nP(X=n) \\ &= \sum_{n=0}^{+\infty}t^ne^{-\lambda} \frac{\lambda^n}{n!} \\ &= e^{-\lambda} \sum_{}^{} \frac{(\lambda t)^n}{n!} \\ &= e^{-\lambda} e^{\lambda t} = e^{\lambda (t-1)}\end{align}$

---
La loi d'une variable aleatoire $X$ a valeurs dans $\mathbb{N}$ est entierement determinee par la donnee de sa fonction generatrice $g_X(t)$

:::danger
**Rappel**

$f(t) = \sum_{n=0}^{+\infty} a_nt^n\ \ \ \ \forall t \in ]-R,R[$

$a_n = \frac{f^{(n)}(0)}{n!}$

Donc $P(X=n) = \frac{g^{(n)}_X(0)}{n!}\ \ \forall n \in \mathbb{N}$
:::

:::info
**Remarque**

Si $X$ est $Y$ sont deux variables aleatoires independantes

Alors $g_{X+Y}(t) = g_X(t) \times g_Y(t)$
:::

**Propriete**

$g_X^{(k)}(1) = E(X(X - 1)) ... (X - k + 1)\ \ \ \forall k \in \mathbb{N}$

$g_X(t) = \sum_{n=0}^{+\infty} t^n P(X=n)$

$g'_X(t) = \sum_{n=1}^{+\infty}P(X=n) nt^{n-1}$

$g''_X(t) = \sum_{n=}^{+\infty} P(X=n)n(n-1)t^{n-2}$

$g'_X(1) = \sum_{n=1}^{+\infty} P(X=1)n$

$g''_X(1) = \sum_{n=2}^{+\infty}n(n-1) P(X(X-1)) = E(X(X-1))$

$g_X^{(k)}(t) = \sum_{}^{} P(X=n) n (n-1)(n-2)...(n-k+1)t^{nk}$

$g^{(k)}_X(1) = \sum_{n=k}^{+\infty} n(n-1)...(n-k+1)P(X=n) = E(X(X-1)...(X - k+ 1)$

++Exercice++

Determiner la fonction generatrice de $X$ qui suit $G(p)$ (Loi geometrique)

$P(X=n) = p(1 - p)^{n-1} = pq^{n-1}$ avec $q = 1 - p$

$g_X(t) = \sum_{n=1}^{+\infty} = t^n P(X=n) = \sum_{n=1}^{+\infty}t^npq^{n-1} = pt\sum^{+\infty}_{1} (tq)^{n-1}$

$g_X(t) = pt \frac{1}{1-qt}$
$g_X(t) = \frac{pt}{1 - qt}$ avec $q = 1 - p$

++Exemple++

$X$, $Y$ deux variables aleatoires 

$X$ suit $\mathcal{P}(\alpha)$ et Y suit $\mathcal{P(\alpha)}$ (Loi de Poisson)

Determiner la loi de $Z = X + Y$

$G_Z(t) = G_Y(t)g_Y(t)$ car X et Y sont independantes

$G_Z(t) = e^{\lambda(t-1)} e^{\alpha(t-1)}$

$G_Z(t) = e^{(\lambda + \alpha)(t - 1)}$

Z suit $\mathcal{P}(\lambda + \alpha)$

## Formulaire

$\sum_{}^{}k = \frac{n(n+1)}{2}, \sum_{k=1}^{n}k^2 = \frac{n(n+1)(2n+1)}{6}$

$\sum_{1}^{n}k^3 = \frac{n^2(n+1^2)}{4}$

### Formule de Pascal
$\binom{n}{k} = \frac{n}{n-k}$
$\binom{n}{k} + \binom{n}{k+1} = \binom{n+1}{k+1}$

### Formule de Vandermonde
$\sum_{k=0}^{a+b} \binom{a}{k} \binom{b}{n-k} = \binom{a+b}{n}$

> $a,b,c \in \mathbb{N}^3$

$\sum_{k=p}^{n} \binom{k}{p} = \binom{n+1}{p+1}$

++Exemple++

Dans une entreprise, on a mis au point le systeme de test suivant pour verifier la qualite du produit
On teste 10 produits ensemble

Si le test est positif, on accepte tous les produits
Si le test est negatif, on teste a nouveau chaque produit individuellement

On teste 50 produits par groupes 

1. Determiner $X(\Omega)$, X:nombre total de tests
2. Loi de X, E(X)

$X = 45$ si 4 lots defectueux
$X = 55$ si 5 lots defectueux

Soit $Y$ une variable aleatoire le nombre de lots defectueux

|X|5|15|25|35|45|55|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|Y|0|1|2|3|4|5|
|$P(Y=k)$|$P(Y=0)$|$P(Y=1)$|...
$Y$ suit $\mathcal{B}(n,p)$ avec $n=5, p=0,1$ (Loi binomiale)

$P(Y=k) = \binom{5}{k}(0,1)^k(0,9)^{5-k}\ \ \ \forall k \in [[0,5]]$

$E(Y) = np = 5 \times 0,1 = 0.5$

$X = 10Y + 5 \implies E(X) = 10E(Y) + 5$

$E(X) = 10 \times 0.5 + 5 = 10$ (En moyenne, l'entreprise fait 10 tests)