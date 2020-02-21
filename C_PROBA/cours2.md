[PROBC] Probabilites Continues (2)
===

## Applications 

++Exercice 1++ : 

Soit $f(x) = (1/2)e^{-|x|}\ \ \ \forall x \in \mathbb{R}$
1. *Montrer que $f(x)$ est une densite de probabilite.*

:::info
**Condition pour prouver qu'une fonction est une densite** 

$f$ est une densite ssi
- $f(x) \geq 0$
- $\int_{\mathbb{R}}f(x)dx = 1$
:::

- $f(x) = (1/2)e^{-|x|} > 0 \forall x \in \mathbb{R}$

- $\int^{+\infty}_{-\infty} f(x)dx = \int_{-\infty}^{+\infty} (1/2)e^{-|x|}dx$
> $f(x)$ est paire, $f(-x) = f(x)$, on peut n'integrer que sur la moitie de l'intervalle

$\begin{align}\int^{+\infty}_{-\infty} f(x)dx &= (2/2) \int^{+\infty}_0 e^{-x} dx \\ &= \int^{+\infty}_0 e^{-x} dx \\ &= [-e^{-x}]^{+\infty}_{0} = 1\end{align}$

2. *Soit $X$ la variable aleatoire de densite $f(x)$. Determiner la fonction de repartition de $X$.*

:::danger
**Fonction de repartition de $X$** : 

$F(X) = P(X < x) = \int^{x}_{-\infty} f(t)dt\ \ \forall x \in \mathbb{R}$
:::

- 1er cas : $x \leq 0$

$\begin{align}F(X) = \int^{x}_{-\infty}(1/2)e^t dt = (1/2) [e^t]^{x}_{-\infty} = (1/2) e^x\end{align}$  
$F(X) = (1/2)e^x$

- 2eme cas : $x > 0$

$\begin{align}F(X) = \int^{x}_{-\infty}f(t) dt &= \int^{0}_{-\infty}f(t) dt + \int^{x}_{0}f(t) dt \\ &= (1/2) + \int^{x}_{0}(1/2)e^{-t}dt \\ &= (1/2) + (1/2)[-e^{-t}]_0^x \\ &= (1/2) - (1/2)e^{-x} + (1/2)\end{align}$  
$F(X) = 1 - (1/2)e^{-x}$

$F(X) = \begin{cases} (1/2)e^x\ \ x \leq 0 \\ 1 - (1/2)e^{-x}\ \ x > 0\end{cases}$

$F(X)$ est continue sur $]-\infty, 0[ \cup ]0, +\infty[$

++Sur 0++ : $\underset{x \to 0^+}{lim} F(x) = 1/2 = \underset{x \to 0^-}{lim} = F(0)$  
$\implies F$ est continue sur $\mathbb{R}$

3. *Calculer $E(X)$ et $V(X)$.*

:::info
$E(X) = \int_{\mathbb{R}}xf(x)dx$
:::

:::info
$V(X) = E(X^2) - E^2(X)$  
Avec $E(X^2) = \int_{\mathbb{R}}x^2f(x)dx$
:::

:::danger
**Definition (esperance d'une loi composee)**

$E(\varphi(X)) = \int_{\mathbb{R}} \varphi(x)f(x)dx$
:::

$\begin{align}E(X) = (1/2)\int^{+\infty}_{-\infty} x e^{-x}dx\end{align}$

> Or $x e^{-x}$ impaire

$\implies E(X) = 0$

$E(X^2) = \int_{-\infty}^{+\infty} x^2 f(x)dx = (1/2)\int^{+\infty}_{-\infty} x^2 e^{-|x|}dx$

> Ou $x^2 e^{-|x|}$ paire

$E(X^2) = (1/2).2 \int^{+\infty}_0 x^2e^{-x}dx = \int^{+\infty}_{0} x^2e^{-x}dx$


:::info
**[Rappel] Integration par parties** 

$\int^{b}_{a} vu'dx = [uv]^b_a - \int^b_a v'u dx$
:::

> On pose $v = x^2$ et $u' = e^{-x}$  
> Donc $u = -e^{-x}$ et $v' = 2x$

$E(X^2) = [-x^{2}e^{-x}]_0^{+\infty} - \int_0^{+\infty} 2x(-e^{-x})dx$

> Et $[-x^{2}e^{-x}]_0^{+\infty} \underset{x \mapsto +\infty}\to 0$

$E(X^2) = 2\int^{+\infty}_{0} x e^{-x}dx$

> Avec $v = x$ et $u' = e^{-x}$

$E(X^2) = 2([-xe^{-x}]^{+\infty}_0 - \int^{+\infty}_0 (-e^{-x})dx)$

> Et $[-xe^{-x}]^{+\infty}_0 \underset{x \mapsto +\infty}\to 0$

$E(X^2) = 2(\int^{+\infty}_0 (e^{-x})dx) = 2[-e^{-x}]^{+\infty}_0 = 2$

Donc $V(X) = E(X^2) - E^2(X) = 2$
> Car $E^2(X) = 0$

--------------
++Exercice 2++ : 

Le fonctionnement d'une machine est perturbe par des pannes. On considere 3 variables aleatoires $X_i (i = 1, 2, 3)$

$X_1$ : Le temps, exprime en heures, ecoule entre la mise en route de la machine et la 1ere panne

$X_2$ (resp $X_3$) : Le temps en heures ecoule entre la remise en route de la machine apres la 1ere panne (resp la 2eme) panne et la suivante

Apres la 3eme panne, la machine est suspendue. $X_i$ sont independantes et suivant la meme loi de densite $f(t) = \begin{cases} 0\ \ \ t < 0 \\ (1/2)e^{-t/2}\ \ \ t \geq 0 \end{cases}$

1. *Quelle est la duree moyenne de fonctionnement entre 2 pannes consecutives ?*

La duree moyenne de fonctionnement entre 2 pannes consecutives : 

$E(X_i) = \int_{\mathbb{R}} tf(t)dt = (1/2)f_0^{+\infty} te^{-t/2}dt$

> Ou $v = t$ et $u' = e^{-t/2}$

$E(X_i) = (1/2)[-2te^{-t/2}]_0^{+\infty} - (1/2)\int_0^{+\infty} (-2e^{-t/2}dt)$

> Ou $(1/2)[-2te^{-t/2}]_0^{+\infty} \to 0$

$E(X_i) = \int_0^{+\infty}e^{-t/2}dt = [-2e^{-t/2}]_0^{+\infty} = 2$

Donc $E(X_1) = 2h$

2. *On appelle $E$ "Chacune des 3 periodes de fonctionnement dure plus de 2h". Calculer $P(E)$*

$E = \bigcap_{i=1}^3 (X_i \geq 2)$  
$P(E) = \prod_{i=1}^3 P(X_i \geq 2)$
> Or independance des $X_i$

$\begin{align}P(X_i \geq 2) &= \int^{+\infty}_{2} f(t)dt = \int_2^{+\infty}(1/2)e^{-t/2}dt \\ &= -[e^{-t/2}]_2^{+\infty} = e^{-1}\end{align}$

$P(E) = (e^{-1})^3 = e^{-3}$

3. *$Y$ variable aleatoire : la plus grande des 3 durees de fonctionnement. Calculer $P(Y \leq t)\ \ \forall t \in \mathbb{R}$*

$Y = \underset{1 \leq i \leq 3}{Max(X_i)}$

$P(Y \leq t) = P(\underset{i}{Max} X_i \leq t)\ \ \ \forall t \in \mathbb{R}$  
$P(Y \leq t) = P(X_i \leq t \ \forall i) = P(\bigcup^3_{i=1}(X_i \leq t))$  
$P(Y \leq t) = \prod^3_{i=1}P(X_i \leq t)$ car $X_i$ independants  
$P(Y \leq t) = F_{X_i}(t)$ fonction de repartition de $X_i$

- ++1er cas++ : $t < 0$

$F_{X_i}(t) = \int_{-\infty}^t f(t)dt = 0$

- ++2eme cas++ : $x \geq 0$

$F_{X_i}(t) = (1/2)\int_0^t e^{-u/2}du = (1/2)[-2e^{-u/2}]^t_0$  
$F_{X_i}(t) = 1 - e^{-t/2}$

$F_{X_i}(t) = \begin{cases} 0\ \ \ t < 0 \\ 1 - e^{-t/2}\ \ t \geq 0 \end{cases}$

$F_{X_i}$ est continue sur $\mathbb{R}$

$F_Y(T) = p(Y \leq t) = \begin{cases}0,\ \ t < 0 \\ (1 - e^{-t/2})^3\ \ t \leq 0\end{cases}$

4. *Determiner une densite de $Y$.*

On derive $F_Y(t)$

$f_Y(t) = F'_Y(t) = \begin{cases}0,\ \ t < 0 \\ (3/2)e^{-t/2}(1 - e^{-t/2})^2\ \ t \geq 0\end{cases}$


5. *Calculer $I = \int_0^{+\infty} te^{at}dt\ \ \forall a \in \mathbb{R}^*$. En deduire $E^0(Y)$*

1ere etape : Calculer l'integrale $\forall a < 0$
