[PROBC] Probabilites Continues (3)
===

# Applications (suite)

5. *Calculer $I = \int_0^{+\infty} te^{\alpha t}dt\ \ \forall a \in \mathbb{R}^*$. En deduire $E^0(Y)$*

$I = \int_0^{+\infty} te^{\alpha t}dt,\ \ \alpha < 0$
> Avec $v = t$ et $u' = e^{\alpha t}$  
> Donc $v' = 1$ et $u = (1/\alpha)e^{\alpha t}$ 

$\begin{align}I = [(t/\alpha)e^{\alpha t}]_0^{+\infty} - \int^{+\infty}_{0} (1/\alpha)e^{\alpha t}\end{align}$

> Or $(t/\alpha)e^{\alpha t} \underset{t \to +\infty}{\to} 0$

$\begin{align}I = -(1/\alpha)[\frac{e^{\alpha t}}{\alpha}]_0^{+\infty} = \frac{1}{\alpha^2}\end{align}$

++La densite de $Y$++ : 

$f_Y(t) = \begin{cases}0\ \ t \leq 0 \\ (3/2)e^{-t/2}(1-e^{-t/2})^2\ \ t > 0\end{cases}$

:::info
**Rappel (Esperance)**  

$E(Y)=\int_{\mathbb{R}}f_y(t)dt$
:::

$\begin{align}E(Y) &= (3/2)\int_0^{+\infty}te^{-t/2}(1-e^{-t/2})^2dt \\ &= (3/2)\int_0^{+\infty}te^{-t/2}(1-2e^{-t/2} + e^{-t})dt \\ &= (3/2)(\int_0^{+\infty}te^{-t/2}dt - 2\int_0^{+\infty} te^{-t}dt + \int_0^{+\infty}te^{-3t/2}dt) \\ &= (3/2)(\frac{1}{(1/4)} - 2\frac{1}{(-1)^2} + \frac{1}{(9/4)}) \\ &= (3/2)(2 + \frac{4}{9}) = \frac{11}{3}h\end{align}$

$E(Y) = 3h\ 40min$

---------------
++Exercice 3++ : 

La duree de fonctionnement, exprimee en jours, d'un certain composant electronique est une variable aleatoire $X$ dont la densite est $f(X) = \begin{cases}0 \ \ \ x < 0 \\ \beta x^2 e^{-\alpha x}\ \ \ x \geq 0\end{cases}$

1. *Calculer $\beta$ en fonction de $\alpha$*

$f$ est une densite ssi  
$\begin{align}\int_{\mathbb{R}}f(x)dx = 1 \implies \beta\int_0^{+\infty} x^2e^{-\alpha x}dx = 1\end{align}$  

Soit $\begin{align}I = \int_0^{+\infty}x^2 e^{-\alpha x}dx\end{align}$
> Ou $v = x^2$ et $u' = e^{-\alpha x}$  

$\begin{align}I= [-(1/\alpha)x^2e^{-\alpha x}]_0^{+\infty} + (2/\alpha)\int_0^{+\infty}xe^{-\alpha x}dx\end{align}$

> Et $x^2e^{-\alpha x} \underset{x \to +\infty}{\to} 0$

$\begin{align}I = (2/\alpha)\int_0^{+\infty}xe^{-\alpha x}dx\end{align}$

> Avec $v = x$ et $u' = e^{-\alpha x}$

$\begin{align}I &= (2/\alpha) ([-\frac{x}{\alpha} e^{-\alpha x}]_0^{+\infty} + (1/\alpha) \int_0^{+\infty} e^{-\alpha x}dx) \\ &= \frac{2}{\alpha^2}[-\frac{1}{\alpha}e^{-\alpha x}]_0^{+\infty} \\ &= \frac{2}{\alpha^3}\end{align}$

$\begin{align}I\beta = 1 \implies \beta = \frac{\alpha^3}{2}\end{align}$

-----------
2. *Sachant qu'un tel composant fonctionne en moyenne pendant 200 jours. Calculer $\alpha$.*

$E(X) = 200j$
$\begin{align}E(X) = \beta\int_0^{+\infty}x^3 e^{-\alpha x}dx\end{align}$
> Avec $v = x^3$ et $u' = e^{-\alpha x}$

$\begin{align}I= \beta([-(1/\alpha)x^3e^{-\alpha x}]_0^{+\infty} + (3/\alpha)\int_0^{+\infty}x^2e^{-\alpha x}dx)\end{align}$
> Ou $x^3e^{-\alpha x} \underset{x \to +\infty}{\to} 0$

$\begin{align}E(X) = \frac{3\beta}{\alpha}I\end{align}$

Or $\beta I = 1$
Donc $\alpha = \frac{3}{200}$

-----------
3. *Determiner une densite de $Y$ ou $Y = \sqrt{X}$*

La fonction de repartition de $Y: F_Y(x) = P(Y < x)$

$F_Y(x) = P(\sqrt{X} < x) = \begin{cases}0\ \ \ x < 0 \\ P(X < x^2) = F_X(x^2)\ \ \ x \geq 0\end{cases}$

$F'_Y(x) = \begin{cases} 0\ \ \ x < 0 \\ 2xf(x^2)\ \ \ x \geq 0\end{cases}$

Une densite de $Y$ :  
$f_Y(x) = \begin{cases}0\ \ \ x < 0 \\ 2xf(x^2) &= 2x\beta x^4 e^{-\alpha x^2} =  \alpha^3 x^5 e^{-\alpha x^2}\end{cases}$

Donc $f_Y(x) = \begin{cases}0\ \ \ x < 0 \\ \alpha^3 x^5 e^{-\alpha x^2}\end{cases}$

------
# Lois usuelles continues

## Loi uniforme sur un intervalle

Une variable aleatoire $X$ suit la loi uniforme sur $[a,b]$ lorsque $X$ admet pour densite :  

$f(x) = \begin{cases}\frac{1}{b-a}\ si\ x \in [a,b] \\ 0\ sinon\end{cases}$

> ++Notation++ : $X \to U[a,b]$ : $X$ suit la loi uniforme


**Esperance**  
$\begin{align}E(X) = \int_{\mathbb{R}}xf(x)dx = \int^b_a x \frac{1}{b-a}dx\end{align}$  
$\begin{align}E(X) = \frac{b+a}{2}\end{align}$

**Variance**  
$V(X) = E(X^2)-E^2(X)$  
$\begin{align}E(X^2) = \int_{\mathbb{R}}x^2f(x)dx = \int^b_a x^2 \frac{1}{b-a}dx = (1/3)(\frac{b^3-a^3}{b-a})\end{align}$  
$\begin{align}V(X) = \frac{(b-a)^2}{12}\end{align}$

## Loi exponentielle de parametre $\lambda\ (\lambda > 0)$

Une variable aleatoire $X$ suit la loi exponentielle si sa densite est

$f(x) = \begin{cases}0\ \ \ \ x < 0 \\ \lambda e^{-\lambda x}\ \ \ x \geq 0 \end{cases}$

++Notation++ : $X \to Exp(\lambda)$ : $X$ suit la loi exponentielle de parametre $\lambda$

-------------
**Esperance**  
$\begin{align}E(X) = \int_0^{+\infty} x \lambda e^{-\lambda x}dx\end{align}$
> avec $v = x$ et $u' = \lambda e^{\lambda x}$

$\begin{align}E(X) = [-x e^{-\lambda x}]_0^{+\infty} + \int_0^{+\infty} e^{-\lambda x}dx\end{align}$

> Or $-x e^{-\lambda x} \underset{x \to +\infty}{\to} 0$

$\begin{align}E(X) = \int_0^{+\infty} e^{-\lambda x}dx = [-1/\lambda e^{\lambda x}]_0^{+\infty}\end{align}$

$E(X) = \frac{1}{\lambda}$

------------
**Variance**  
$V(X) = E(X^2)-E^2(X)$  
$\begin{align}E(X^2) = \int_0^{+\infty} x^2 \lambda e^{-\lambda x}dx\end{align}$
> Avec $x^2 = v$ et $\lambda e^{-\lambda x} = u'$

$\begin{align}E(X^2) &= [-x^2 e^{-\lambda x}]_0^{+\infty} + 2 \int_0^{+\infty} xe^{-\lambda x}dx\\ &= 2\int^{+\infty}_{0}x e^{-\lambda x}dx  \\ &= \frac{2}{\lambda}E(X) = \frac{2}{\lambda^2}\end{align}$

Donc $\begin{align}V(X) = \frac{1}{\lambda^2}\end{align}$

:::info
**Remarque** :  

$\forall (s, t) \in \mathbb{R}^2_+$  
$\begin{align}P(X \geq s+t / X > s) &= P(X > t) \\ &= \frac{P((X \geq s + t) \cup (X > s))}{P(X > s)} = \frac{P(X \geq s + t)}{P(X > s)}\end{align}$
:::

On dit que la loi exponentielle n'a pas de memoire

## Loi Gamma de parametre $r\ (r > 0)$

==**Definition**==

On dit qu'une variable aleatoire $X$ positive suit une loi Gamma notee $\gamma_r$ de parametre $r$ si sa densite est $\begin{align}f(x) = \frac{1}{\Gamma(r)}e^{-x} x^{r - 1}\end{align}$

Ou $\begin{align}\Gamma(r) = \int_0^{+\infty} e^{-t} t^{x-1}dt\end{align}$ Fonction Gamma

==**Proprietes de $\Gamma(x)$**==

1. $\Gamma(x+1 = x\Gamma(x)) \ \ \ \forall x > 0$
2. $\Gamma(1) = 1$
3. $\Gamma(n + 1) = n!$
4. $\Gamma(k + (1/2)) = \frac{1.3.5...(2k - 1)}{2^k} \Gamma(1/2)$
5. $\Gamma(1/2) = \sqrt{\pi}$

#### Esperance

$\begin{align}E(X) = \int_{\mathbb{R}} xf(x)dx = \frac{1}{\Gamma(r)} \int_0^{+\infty} e^{-x} x^r dx\end{align}$

$\begin{align}\Gamma(x) = \int_0^{+\infty} e^{-t} t^{x-1} dt\end{align}$

$\begin{align}E(X) = \frac{\Gamma(r+1)}{\Gamma(r)} = \frac{r \Gamma(r)}{\Gamma(r)} = r\end{align}$

:::danger
**Esperance de la Loi Gamma**  
$E(X) = r$
:::

#### Variance

$V(X) = E(X^2) - E(X)^2$

$\begin{align}E(X^2) = \int_{\mathbb{R}} x^2f(x)dx = \frac{1}{\Gamma(r)} \int_0^{+\infty} e^{-x} x^{r+1} dx\end{align}$

$\begin{align}E(X^2) = \frac{\Gamma(r+1)}{\Gamma(r)} = \frac{(r+1)\Gamma(r+1)}{\Gamma(r)} = (r+1)r\end{align}$

$V(X) = E(X^2) - E(X)^2 = r^2 + r - r^2$  
$V(X) = r$

:::danger
**Variance de la Loi Gamma**  
$V(X) = r$
:::
