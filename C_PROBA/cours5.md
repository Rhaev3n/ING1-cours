[PROBC] Probabilites Continues (5)
===


## Convergence en loi

==**Definition**==

$X_n$ une suite de variables aleatoires de fonction de repartition $F_{X_n}(x)$ et $X$ une variable aleatoire de fonction de repartition $F_X(x)$

On dut que $X_n$ converge en loi vers $X$ ssi $\forall x \in \mathbb{R}$ ($x$ point de continuite dans $F_X(x)$)  

$\underset{n \to +\infty}{lim}\ F_{X_n}(x) = F_X(x)$


++Notation++  

$\overline{X_n} \underset{n \mapsto +\infty}{\overset{\mathscr{L}}{\longrightarrow}} X$

==**Theoreme**==

($X_n$) une suite de variables aleatoires independantes et de meme loi d'esperance $m$ et d'ecart-type $\sigma$

Soit $S_n = \sum^n_{k=1} X_k$ alors on a   

$\begin{align}\frac{S_n - nm}{\sigma \sqrt{n}} \underset{n \mapsto +\infty}{\overset{\mathscr{L}}{\longrightarrow}} N(0,1)\end{align}$

:::info
**Remarque**  
$E(S_n) = \sum^n_{k=1} E(X_k) = \sum^n_{k=1}m = nm$  
$V(S_n) = \sum^n_{k=1} V(X_k) = \sum^n_{k=1} \sigma^2 = n\sigma^2$  
$\sigma(S_n) = \sigma \sqrt(n)$

Ce theoreme traduit $S_n = \sum^n_{k=1} X_k$ alors on a   


$\begin{align}\frac{S_n - E(S_n)}{\sigma(S_n))} \underset{n \mapsto +\infty}{\overset{\mathscr{L}}{\longrightarrow}} N(0,1)\end{align}$
:::

:::info
**Remarque**  
La congergence en probabilite $\implies$ la convergence en loi
:::

:::info
**Remarque**  
Si la suite $X_n$ converge en loi vers une constante $a$, alors on a la convergence en probabilite

Convergence en probabilite : Quand on regarde l'evenement $X_n - a \geq \varepsilon =$ points de divergence de la suite, donc on prouve que la probabilite de divergence de la suite = 0
:::

## Applications 

++Exercice 1++  

Soit $(X_n)$ une suite de variables aleatoires de densite $\begin{align}f_n(X) = \frac{ne^{-nX}}{(1+e^{-nX})^2}\end{align}$

- Montrer que $X_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} 0$

Il faut qu'on prouve que la proba $P(|\overline{X_n} - m| \geq \varepsilon) \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} 0$

> On passe par l'evenement contraire

On cherche $\forall \varepsilon > 0\ \ P(|X_n| \geq \varepsilon) = 1 - P(|X_n| < \varepsilon)$  
$P(|X_n| \geq \varepsilon) = 1 - P(-\varepsilon < X_n < \varepsilon) = 1 - \int_{-\varepsilon}^{\varepsilon} f_n(x)dx$

$\begin{align}P(|X_n| \geq \varepsilon) = 1 - \int^{\varepsilon}_{-\varepsilon} \frac{ne^{-nX}dx}{(1+e^{-nX})^2}\end{align}$

$\begin{align}P(|X_n| \geq \varepsilon) = 1 - [\frac{1}{1 + e^{-nx}}]^{\varepsilon}_{-\varepsilon} = 1 - \frac{1}{1 + e^{-n\varepsilon}} + \frac{1}{1 + e^{n\varepsilon}}\end{align}$

$\underset{n \to \infty}{lim} P(|X_n| \geq \varepsilon) = 1 - 1 = 0$

Donc $X_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} 0$

 
---
++Exercice 2++

Soit $X_n$ uine variable aleatoire suivant la loi exponentielle de densite :  
$f(x) = 0$ ssi $x \leq 0$  
$f(x) = e^{-x}$ si $x > 0$

$S_1, X_2, ... X_n$ une suite de variables aleatoires independantes de meme loi que $X$

Soit $U_n = Inf_{1 \leq i \leq n} X_i$

- Montrer que $U_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} 0$

++Etapes++  
- Fonction de repartition de la loi exponentielle  
- Fonction de repartition de la suite $U_n$  
- Puis sa limite en tout point de continuite (0 est le point de discontinuite de la fonction)

$X_1,... X_n \to Expo(\lambda = 1)$  
$U_n = Inf_{i \leq i \leq n} X_i$

Montrons que $U_n = Inf_{1 \leq i \leq n} X_i$

Foit $F(x)$ la fonction de repartitio de $X: \begin{cases}F(x) = 0\ \ x < 0 \\ F(x) = 1 - e^{-x}\ \ x \geq 0\end{cases}$

Soit $G_n(x)$ la fonction de repartition de $U_n$
$x < 0\ \ G_n(x) = 0$  
$x \geq 0\ \ G_n(x) = P(U_n \leq x)$  

$G_n(x) = 1 - P(U_n > x)$  
$G_n(x) = 1 - P(X_i > x,\ i \in \{1,...n\})$  
$G_n(x) = 1 - P(\bigcap^n_{i=1} X_i > x)$ et $X$ independante  
$G_n(x) = 1 - \prod^n_{i=1} P(X_i > x)$  
$G_n(x) = \prod^n_{i=1}(1 - P(X_i \leq x))$  
$G_n(x) = 1 - \prod^n_{i=1} (1 - F(x)) = 1 e^{-x}$

Donc $G_n(x) = 1 - e^{-x}$ si $x \geq 0$  
$G_n(x) = 0$ si $x < 0$

Si $x < 0\ \ \underset{n \to \infty}{lim}G_n(x) = 0$  
Si $x > 0\ \ \underset{n \to \infty}{lim} G_n(x) = 1$

Or $G_n(x) = \begin{cases}0\ \ x < 0\\ 1\ \ x > 0\end{cases}$ est la fonction de repartition de $X = 0$

Donc $U_n \underset{n \mapsto +\infty}{\overset{\mathscr{L}}{\longrightarrow}} 0$

---
++Exercice 3++  

Soit $\begin{cases} f_n(x) = (n + 1)(1 - x)^n\ si\ x \in [0,1] \\ f_n(x) = 0\ sinon \end{cases}$

1. Verifier que $f_n$ est une densite de probabilite

$Y$ une variable aleatoire suivant la loi exponentielle

$\begin{cases} f_n(x) = (n + 1)(1 - x)^n\ si\ x \in [0,1] \\ f_n(x) = 0\ sinon \end{cases}$

$f_n \geq 0$, montrons que $\int^{+\infty}_{-\infty} f_n(x)dx = 1$  

$\int^{+\infty}_{-\infty} f_n(x)dx = \int^{1}_{0} (n+1)(1-x)^ndx = [-(1-x)^{n+1}]^1_0 = 1$

Donc $f_n(x)$ est une densite

2. Soit $X_n$ une suite de variables aleatoires admettant $f_n$ pour densite. On pose $Y_n = nX_n$. Montrer que $Y_n \underset{n \mapsto +\infty}{\overset{\mathscr{L}}{\longrightarrow}} Y$

$\forall x \in \mathbb{R}\ \ \ (Y_n \leq x) = P(nX_n \leq x)$  
$P(Y_n \leq x) = P(X_n \leq \frac{x}{n})$  

Si $x < 0,\ P(Y_n \leq x) = 0$  
Si $X \in [0,n] \implies 0 \leq \frac{x}{n} \leq 1$  

Donc $P(Y_x \leq x) = \int^{x/n}_{0} (n+1)(1-t)^n dt$

$P(Y_n \leq x) = [-(1-t)^{n+1}]^{x/n}_0 = 1 - (1 - \frac{x}{n})^{n+1}$

Si $x > n,\ P(Y_n \leq x) = \int^{x/n}_{0}f_n(t)dt$

Or $\frac{x}{n} > 1 \implies \int^1_0 f_n(t) dt = 1$

Donc la fonction de repartition de $Y_n$ est 

$F_n(x) = \begin{cases}0\ si\  x< 0 \\ 1 - (1 - \frac{x}{n+1})^{n+1}\ si\ 0 \leq x \leq n \\ 1\ si\ x > n \end{cases}$

$\begin{align}(1 - \frac{x}{n})^{n+1} = e^{(n+1)ln(1-\frac{x}{n})}\end{align}$

On sait que $ln(1 - \frac{x}{n}) \sim -\frac{x}{n}$ au voisinage de 0 $\ \ \ \ (\frac{x}{n} \underset{n \to +\infty}{\to} 0$)

Donc $(1 - \frac{x}{n})^{n+1} \sim e^{-\frac{(n+1)}{n}x} \underset{}{\to} e^{-x}$

Donc $\underset{n \to +\infty}{\lim} (1 - (1 - \frac{x}{n+1})) = 1 - e^{-x}$

++Conclusion++

$\underset{}{lim} F_n(x) = \begin{cases} 0\ si\ x < 0 \\ 1 - e^{-x}\ si\ \geq 0 \end{cases}$

On reconnait la fonction de repartition de la loi exponentielle $(\lambda = 1)\ \ F_n = \begin{cases}0\ x < 0 \\ 1 - e^{-x}\ x \geq 0\end{cases}$

Donc $Y_n \overset{\mathscr{L}}{\to} Y$ suit la loi $Expo(\lambda = 1)$