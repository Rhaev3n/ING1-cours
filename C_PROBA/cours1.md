[PROBC] Probabilites Continues (1)
===

## Variables aleatoires reelles

### ==Definition (Variable aleatoire reelle)==

Une variable aleatoire reelle est une application mesurable de $(\Omega, \mathcal{C}, \mathcal{P})$ dans $\mathbb{R}$, muni de sa tribu Borelienne

:::info
La **tribu Borelienne** sur un espace topologique X est la plus petite tribu sur X contenant tous les ensembles ouverts.
:::

> $\Omega$ : univers  
> $\mathcal{C}$ : tribu (l'ensemble de tous les evenements)  
> $\mathcal{P}$ : probabilite

$\mathbb{B}$ : La $\sigma$-algebre engendree par les intervalles de $\mathbb{R}$

$\forall B \in \mathbb{B}$ ($B$: borelien),  
$X: (\Omega, \mathcal{C}, \mathcal{P}) \mapsto (\mathbb{R}, \mathbb{B})$

$\mathcal{P}_X(B) = \mathcal{P}(\{ \omega \in \Omega / X(\omega) \in B \})$

---------
### Tribu

Axiomes de $\mathcal{C}$
1. $\forall A \in \mathcal{C},\ \overline A \in \mathcal{C}$

3. Soit $(A_i)_{i \in I}$ famille denombrable d'evenements, $\bigcup_{i \in I} A_i \in \mathcal{C}\ (A_i \in \mathcal{C})$ 
4. $\varnothing \in \mathcal{C}, \Omega \in \mathcal{C}$

> La $\sigma$-algebre, c'est la plus petite tribu engendree par les intervalles de $\mathbb{R}$  
> $\implies$ Intersection de toutes les tribus de $\mathbb{R}$


$\mathcal{P}_X(B) = \mathcal{P}(\{ \omega \in \Omega / X(\omega) \in B \}) = \mathcal{P}(\{ X^{-1}(B) \})$
> Avec $X^{-1}$ image reciproque

---------------------------
### Fonction de repartition

==**Definition**==

La fonction de repartition de $X$ est l'application 
$F : \mathbb{R} \mapsto [0,1]$

$F(x) = \mathcal{P}(X < x)$

> $F$ est une fonction croissante et $F(-\infty) = 0$, $F(+\infty) = 1$

---------------------
### Variable continue

On dit qu'une variable aleatoire $X$ est **a densite** lorsque sa fonction de repartition $F$ est continue sur $\mathbb{R}$ et de classe $\mathscr{C}^1$ sur $\mathbb{R}$ prive d'un ensemble fini de points.

Toute fonction $f$ a valeurs positives qui ne differe de la derivee de $F'$ qu'en un nombre fini de points est appelee **densite de X**.

:::info
$F'(x) = f(x)$ sur $\mathbb{R}$
prive de certains points
:::

==**Theoreme**==

Soit $X$ une variable aleatoire reelle a densite de fonction de repartition $F$

Alors $\forall x \in \mathbb{R},\ F(X) = \int^{x}_{-\infty} f(t)dt$

++Demonstration++

Soient $a_1, a_2, ..., a_n$ les points en lesquels $F'$ n'est pas definie, avec $a_1 < a_2 < ... < a_n$

:::info
++On note++  
$a_0 = -\infty$  
$a_{n+1} = +\infty$

F est une primitive de $f$ sur chaque intervalle de la forme $]a_k, a_{k+1}[\ \ (k \in [[0,p]])$ et donc sur $]a_p, x[$
:::
- **1er cas**

$F$ est une primitive de $f$ sur $]-\infty, x]$ et $\underset{t \to -\infty}{lim} F(t) = 0$

$\int^x_{-\infty} f(t)dt = [F(t)]^x_{-\infty} = F(x)$

- **2eme cas**

$a_p \leq x < a_{p+1}\ \ p \in [[1,n]]$

$\forall k \in [[1, p-1]],\ \ \ \begin{align}\int^{a_{k+1}}_{a_k} f(t)dt &= \underset{t \to a_{k+1}^-}{lim} F(t) - \underset{t \to a_k^+}{lim}F(t) \\ &= F(a_{k+1}) - F(a_k)\end{align}$

> car F est continue

$\begin{align}\int^{a_1}_{a_0} f(t)dt = \int_{-\infty}^{a_1} f(t)dt &= [F(t)]_{-\infty}^{a_1} \\ &= \underset{t \to a_1^-}{lim}F(t) - F(-\infty) \\ &= F(a_1)\end{align}$

$\begin{align}\int^{x}_{a_p} f(t)dt = F(x) - F(a_p)\end{align}$

$\begin{align}\int^{x}_{-\infty} f(t)dt &= \sum^{p-1}_{k=0} \int^{a_{k+1}}_{a_k} f(t)dt + \int^{x}_{a_p}f(t)dt \\ &= F(a_1) + \sum_{k=1}^{p-1} (F(a_{k+1}) - F(a_k)) + F(x) - F(a_p) \end{align}$

$\int^{x}_{-\infty} f(t)dt = F(x)$

- **Consequence**

$f(x)$ est continue sur $\mathbb{R}$ sauf eventuellement en un nombre fini de points

1. $F'(x) = f(x) \geq 0$ car $F$ est croissante
2. $\int^{+\infty}_{-\infty} f(t)dt = \underset{x \to +\infty}{lim} F(x) = 1$

----------------
### Applications

++Exemple 1++ : 

$f(x) = \begin{cases} cos(x)\ si\ x \in [0, \pi / 2] \\ 0\ sinon\end{cases}$

1. Verifier que $f(x)$ est une densite
2. Soit $X$ une variable aleatoire de densite $f$. Determiner la fonction de repartition $F(X)$

---
1. Verifier que $f(x)$ est une densite

i. 
$f(x) = cos(x) \geq 0\ \ \  \forall x \in [0, \pi / 2]$

ii.
$\int^{}_{\mathbb{R}} f(x)dx = \int^{\pi / 2}_{0} cos(x)dx = [sin(x)]^{\pi / 2}_{0} = sin(\pi / 2) = 1$

---
2. Soit $X$ une variable aleatoire de densite $f$. Determiner la fonction de repartition $F(X)$

$F(x) = \int^{x}_{-\infty} f(t)dt$

- 1er cas : $x \in ]-\infty, 0]$

$F(x) = \int^x_{-\infty}f(t)dt = 0$

- 2eme cas : $x \in ]0, \pi / 2]$

$F(x) = \int^{0}_{-\infty} f(t)dt + \int^{x}_{0} f(t)dt = \int^{x}_{0} cos(t)dt = sin(x)$

- 3eme cas : $x > \pi / 2$

$F(x) = \int^{x}_{-\infty} f(t)dt = \int^{0}_{-\infty} + \int^{\pi / 2}_{0}f(t)dt + \int^{x}_{\pi / 2} f(t)dt$  
$F(x) = \int^{\pi / 2}_{0} cos(t)dt = 1$

-------------
++Exemple 2++ : 

X est une variable aleatoire de densite $f$, $F$ est sa fonction de repartition

$Y = \varphi(X) = aX + b\ \ \ a \neq 0$

Determiner la loi de $Y$
Soit $G(x)$ la fonction de densite de $Y$

$G(x) = \mathcal{P}(Y < x)$

$G(x) = \mathcal{P}(aX + b < x)$

- 1er cas : a > 0

$G(x) = \mathcal{P}(X < \frac{x - b}{a}) = F(\frac{x-b}{a})$

- 2eme cas : a < 0

$G(x) = \mathcal{P}(X > \frac{x-b}{a}) = 1 - \mathcal{P}(X \leq \frac{x-b}{a}) = 1 - F(\frac{x-b}{a})$

:::info
**Remarque** : 
Pour les variables continues : 

$\mathcal{P}(X=a) = 0$
$\int^{b}_{a} f(t)dt = F(b) - F(a)$

Si $a = b,\ P(x=a) = 0$
$F(x) = P(x < a) = P(x \leq a)$
:::
La densite de $Y$ est $g(x) = G'(X)$
$g(x) = G'(x) = \begin{cases} \frac{1}{a}f (\frac{x-b}{a}) a > 0 \\ -\frac{1}{a} f(\frac{x-b}{a}) a < 0\end{cases}$

$\begin{align}g(x) = \frac{1}{|a|} f(\frac{x-b}{a})\end{align}$

## Moments d'une variable aleatoire continue

### Esperance mathematique

==**Definition**==

Soit X une variable aleatoire continue de densite $f(x)$
:::danger
On appelle **esperance** de $X$

$\begin{align}E(X) = \int_{\mathbb{R}} xf(x)\end{align}$

Si l'integrale converge
:::

:::info
**Remarque**

E est lineaire

$E(\alpha X + \beta Y) = \alpha E(X) + \beta E(Y)$  
$\forall(\alpha, \beta) \in \mathbb{R}^2$
:::

==**Definition**==

$\begin{align}E(\varphi(X)) = \int_{\mathbb{R}} \varphi(x) f(x) dx\end{align}$

> $\varphi$ quelconque  
> Avec $f(x)$ = densite de $X$

++Exemple (Loi de Cauchy)++ : 

Sa densite $f(x) = \frac{1}{\pi (1 + x^2)} \ \ \ \forall x \in \mathbb{R}$

$\begin{align}E(X) = \int^{+\infty}_{-\infty} \frac{x}{\pi (1 + x^2)} dx\end{align}$

++Au voisinage de $+\infty$++ :   
$\begin{align}\frac{x}{1 + x^2} \sim \frac{1}{x}\end{align}$

Or $\int^{+\infty}_{1} \frac{1}{x} dx$ DV car Riemann avec $\alpha = 1$

-----------------
### Variance de X

==**Definition**==

:::danger
On appelle **variance** de $X$
$V(X) = E((X - E(X)^2))$
:::

$\sigma = \sqrt{V(X)} \implies$ **ecart-type**

$V(X) = \int^{}_{\mathbb{R}} (x - E(X))^2 f(x) dx$  
Si l'integrale converge