[PROBC] Probabilites Continues (4)
===

## Loi de Laplace-Gauss (Loi Normale)

Sa densite est $\begin{align}f(x) = \frac{1}{\sigma \sqrt{2\pi}} exp(-\frac{1}{2}(\frac{x-m}{\sigma})^2)\ \ \ \forall x \in \mathbb{R}\end{align}$

$m= E(X)$
$\sigma = \sqrt{V(X)}$ (ecart-type)

> **Notation**  
> On note $X \to N(m, \sigma)$ ou $X \to L.G(m, \sigma)$

Soit $U = \frac{X-m}{\sigma} \to N(0, 1)$  
$E(U) = 0$ ($U$ est centree)  
$\sigma = \sqrt{V(X)} = 1$ ($U$ est reduite)

$U$ est dite variable normale centree et reduite  
Sa densite est $\begin{align}f(u) = \frac{1}{\sqrt{2\pi}}e^{-\frac{u^2}{2}}\end{align}$

-------------------
==**Proposition**==

:::danger
$V(U) = 1$  
:::

++Demonstration++  

$V(U) = E(U^2) - E^2(U) = E(U^2)$  

$\begin{align}E(U^2) = \int_0^{+\infty} \frac{1}{\sqrt{2\pi}} u^2 e^{-\frac{u^2}{2}} du = \frac{2}{\sqrt{2\pi}} \int_0^{+\infty} u^2 e^{-\frac{u^2}{2}}\end{align}$

> Posons $t = \frac{u^2}{2} \implies dt = udu \implies du = \frac{dt}{\sqrt{2t}}$

$\begin{align}E(U^2) = \frac{2}{\sqrt{2\pi}} \int_0^{+\infty} 2t e^{-t} \frac{dt}{\sqrt{2t}}\end{align}$

$\begin{align}E(U^2) = \frac{2}{\sqrt{\pi}} \int_0^{+\infty} t^{1/2} e^{-t} {dt} = \frac{2}{\sqrt{\pi}} \Gamma(3/2) = \frac{2}{\sqrt{\pi}} (1/2) \Gamma(1/2) = 1\end{align}$

$V(U) = 1$

++Calcul de $\Gamma(1/2)$++  

$\Gamma(1/2) = \int_0^{+\infty} x^{-1/2} e^{-x}dx$

> $x = \frac{u^2}{2}$ et $dx = udu$

$\begin{align}\Gamma(1/2) = \int_0^{+\infty} \sqrt{2} u^{-1} e^{-\frac{u^2}{2}} udu = \sqrt{2} \int_0^{+\infty} e^{-\frac{u^2}{2}}du\end{align}$

Or $\begin{align}\int_{-\infty}^{+\infty} \frac{e^{-\frac{u^2}{2}}du}{\sqrt{2\pi}} = 1 \implies 2\int_0^{+\infty} \frac{e^{-\frac{u^2}{2}}du}{\sqrt{2\pi}} = 1 \implies \int_0^{+\infty} e^{-\frac{u^2}{2}} du = \frac{\sqrt{2\pi}}{2}\end{align}$

$\begin{align} \Gamma(1/2) = \sqrt{2} \times \frac{\sqrt{2\pi}}{2} = \sqrt{\pi} \end{align}$

-----------
### Calculs des moments d'une loi Normale centree-reduite

$U \to N(0, 1)$  

:::danger
On appelle **moment d'ordre $k$ de $U$**:  

$F_k = E(U^k) = \int_{\mathbb{R}} u^k f(u) du$
:::

Si $\begin{align}k = 2p+1\ \ \ F_{2p+1} = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{+\infty} e^{2p+1} e^{-\frac{u^2}{2}} du = 0\end{align}$

Si $\begin{align}k = 2p\ \ \ \ \ \ \ \ \ \ F_{2p} = \frac{2}{\sqrt{2\pi}} \int_0^{+\infty} u^{2p} e^{-\frac{u^2}{2}} du\end{align}$

$\begin{cases} t = \frac{u^2}{2} \\ dt = udu \iff du = \frac{dt}{\sqrt{2t}} \end{cases}$

$\begin{align}F_{2p} = \frac{2}{\sqrt{2\pi}} \frac{1}{\sqrt{2}} \int_0^{+\infty} (2t)^{p} e^{-t} \frac{dt}{\sqrt{t}} = \frac{2^p}{\sqrt{\pi}} \int_0^{+\infty} t^{p - 1/2} e^{-t} dt\end{align}$

$\begin{align}F_{2p} &= \frac{2^p}{\sqrt{\pi}} \Gamma(p + 1/2) = \frac{2^p}{\sqrt{\pi}} \frac{1.3.5...(2p-1)}{2^p}\Gamma(1/2) = 1.3.5...(2p-1)\end{align}$

$\begin{align}F_{2p} &= \frac{(2p)!}{2.4.6...2p} = \frac{(2p)!}{2^p(p!)}\end{align}$

-----------------------------------------
### Somme de deux variables independantes

Soient $X$ et $Y$ deux variables aleatoires independantes et $Z = X + Y$

==**Theoreme**==  

$X, Y$ deux varaiables aleatoires independantes admettant pour densite $f$ et $g$.  
Une densite de $Z$ est donnee par le **produit de convolution** : 

$\begin{align}h(z) = \int_{-\infty}^{+\infty} f(u)g(z - u) du = \int_{-\infty}^{+\infty} g(y)f(z-y) dy\end{align}$
> Avec $h(z)$ la densite de $Z$

++Exemple++ : 

$X \to \gamma_r, Y \to \gamma_s$  
X et Y independantes  

1. Determiner la loi de $Z = X + Y$

$\begin{align}f(x) = \frac{1}{\Gamma(r)}e^{-x} x^{r-1}\end{align}$ et $\begin{align}g(y) = \frac{1}{\Gamma(s)}e^{-y} y^{s-1}\end{align}$

$\begin{align}h(z) = \int_{\mathbb{R}} f(x) g(z - x)dx = \int_{0}^{z} \frac{1}{\Gamma(r)} e^{-x} x^{r-1} \frac{1}{\Gamma(s)} e^{-(z-x)}(z-x)^{s-1} dx \end{align}$

> $g(z-x) = 0$ si $x > z$
 
$\begin{align}h(z) = \frac{e^{-z}}{\Gamma(r)\Gamma(s)} \int_0^z u^{r-1} (z-x)^{s-1} dx\end{align}$

Posons $x = tz \implies dx = zdt$

$\begin{align} h(z) = \frac{e^{-z}}{\Gamma(r)\Gamma(s)} \int_0^1 (tz)^{r-1}(z - tz)zdt = \frac{e^{-z}z^{r+s-1}}{\Gamma(r)\Gamma(s)} \int_0^1 t^{r-1}(1 - t)^{s-1}dt \end{align}$

Soit $\begin{align}C = \frac{1}{\Gamma(r)\Gamma(s)} \int_0^1 t^{r-1}(1-t)^{s-1}dt\end{align}$

$\begin{align}\int_0^{+\infty} h(z) dz = 1 = C\int_0^{+\infty} e^{-z}z^{r+s-1} dz \implies C = \frac{1}{\int_0^{+\infty} e^{-z} z^{r+s-1} dz} = \frac{1}{\Gamma(r+s)} \end{align}$

$\begin{align}  h(z) = \frac{e^{-z} z^{r+s-1}}{\Gamma(r+s)} \end{align}$ densite de la loi $\gamma_{r+s}$  

Donc $Z \to \gamma_{r+s}$

> Les parametres d'aditionnent pour la loi Gamma

---------------
### Convergence en probabilite et convergence en loi

#### Inegalite de MARKOV

==**Theoreme**==

Si $X$ est une variable aleatoire a densite admettant un moment d'ordre 2, alors $\begin{align}\forall \varepsilon > 0,\ \ P(|X| \geq \varepsilon) < \frac{E(X^2)}{\varepsilon^2}\end{align}$

++Demonstration++ 

$E(X^2) = \int^{+\infty}_{-\infty}$

-------------------------------------
#### Inegalite de Bienaymé Tchebyschev

$\begin{align}\forall \varepsilon > 0\ \ P(|X - E(X)| \geq \varepsilon) \leq \frac{V(X)}{\varepsilon^2}\end{align}$

En effet, on applique MARKOV a la variable aleatoire $X -E(X)$

$\begin{align}P(|X - E(X)| \geq \varepsilon) \leq \frac{E((X - E(X))^2)}{\varepsilon^2} = \frac{V(X)}{\varepsilon^2}\end{align}$

--------------------------------------------
==**Definition (Convergence d'une suite)**==

Soit $X_n$ une suite de variables aleatoires et $X$ une variable aleatoire. On dit que $X_n$ converge en probabilite vers $X$ ssi : 

$\forall \varepsilon > 0,\ \ \underset{n \mapsto +\infty}{lim} P(|X_n - X| > \varepsilon) = 0$  
> Notation $X_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} X$

:::info
**Remarque**  
$\{ X_n / |X_n - X| \geq \varepsilon \}$ l'ensemble des points de divergence de la suite $X_n$
:::

:::info
**Remarque**  
Si $E(X_n) \underset{n \mapsto +\infty}{\to} a$ et $V(X_n) \underset{n \mapsto +\infty}{\to} a$ alors $X_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} a$
:::

$\forall \varepsilon > 0\ P(|X_n - E(X_n)| \geq \varepsilon) \leq \frac{V(X_n)}{\varepsilon^2} \to 0$  
Si $n \to +\infty\ \ \ \ \ P(|X_n - a| \geq \varepsilon) \underset{n \to +\infty}{\to 0}$ Donc $X_n \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} a$

### Loi faible des grands nombres

==**Theoreme**==

$X_n$ une suite de variables aleatoires independantes admettant une esperance $m$ et une variance $\sigma^2$

$\begin{align}\overline{X_n} = \frac{1}{n} \sum_{i=1}^{n} X_i\end{align}$ alors $\overline{X_n} \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} m = E(X)$
> $\overline{X_n}$ : moyenne empirique

++Demonstration++  

$E(\overline{X_n}) = \frac{1}{n} \sum^n_{i=1}E(X_i) = \frac{nm}{n} = m$  
$V(\overline{X_n}) = \frac{1}{n^2} \sum^n_{i=1} V(X_i)$ car les $X_i$ sont independants  

$V(\overline{X_n}) = \frac{1}{n^2} \sum^{n}_{i=1} V(X_i) = \frac{n\sigma^2}{n^2} = \frac{\sigma^2}{n} \to 0$  

En util utilisant l'inegalite de Tchebyschev 

$\begin{align}\forall \varepsilon > 0\ \ P(|\overline{X_n} - m| \geq \varepsilon) \leq \frac{V(\overline{X_n})}{\varepsilon^2} \implies P(|\overline{X_n} - m| \geq \varepsilon)P(|\overline{X_n} - m| \geq \varepsilon) \leq \frac{\sigma^2}{n\varepsilon^2} \to 0\end{align}$

Donc $\begin{align}\overline{X_n} \underset{n \mapsto +\infty}{\overset{P}{\longrightarrow}} m = E(X_n)\end{align}$