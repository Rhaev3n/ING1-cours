[IMASI] Introduction aux mathematiques du signal (last)
===

## Series de Fourier

Soit $f(t)$ periodique de periode $T (T > 0)$. Un signal 1D periodique peut etre vu comme une somme de sinusoides

$\begin{align}f(t) = \sum_{n=-\infty}^{\infty}C_ng_n(t)\end{align}$

On considere les fonctions $g_n(t)$

$\begin{align}g_n(t) = e^{2 j\pi (\frac{nt}{T})}\end{align}$

**Remarques**

- Harmoniques 
$\begin{align}f(t) = \sum_{n=-\infty}^{\infty}C_ng_n(t)\end{align}$ avec $C_n$ harmoniques

$C_0$ : frequence continue
$C_1$ : frequence fondamentale
...
$C_n$ : $n^{ieme}$ harmonique
$f$ reel $\implies C_n = C_{-n} * (t(t) = f*(t))$

**==Relation de Parseval==**

Il y a conservation de la puissance de la representation temporelle a la representation frequentielle

### Frequences

++Pour le son++ : 
- Basses frequences
    - Lentes variations
    - Sons graves
- Hautes frequences
    - Variations rapides
    - Sons aigus


++Pour l'image++ : 
- Basses frequences
    - Lentes variations
    - Zones presque uniformes
- Hautes frequences
    - Variations rapides
    - Contours / coins

#### Spectre

- D'amplitude $|C_n|$
- De phase $Arg(C_n) = argtan(-bn/an)$
- De puissance $|C_n|^2$
- $f(t)$ reel $\implies$ spectre d'amplitude symetrique

++Visualisation du spectre++ : 
![](https://i.imgur.com/RggLESi.png)

> On invertit les cadrans $\implies$ les basses frequences se retrouvent au centre
> 
Soient $\begin{align}f(t) = \sum_{n=-\infty}^{\infty}C_ng_n(t)\end{align}$ et $\begin{align}g_n(t) = e^{2 j\pi (\frac{nt}{T})}\end{align}$

Que vaut $<g_n(t), g_m(t)> = \frac{1}{T}\int_T g_n(t)g^*_m(t)dt$ ?

Comment trouver les coefficients $C_n$ ? 

$<g_n(t), g_m(t)> = \frac{1}{T}\int_T g_n(t)g^*_m(t)dt$

$<g_n(t), g_m(t)> = \begin{cases}1\ si\ n=m \\ 0\ sinon\end{cases}$

$<f(t), g_m(t)> = \frac{1}{T}f(t)g^*_m(t)dt$

$\begin{align}<f(t), g_m(t)> &= C_0 \int g_0g_m^* + C_1 \int g_1 g_m^* + ... + C_i \int g_i g_m^* + ... + C_m \int g_m g_m^* + ... \\ &= C_m \int g_m g_m^* \\ &= C_m\end{align}$

**Passage a la transformee de Fourier**

$\begin{align}f(t) = \sum_{n=-\infty}^{\infty}C_ng_n(t)\end{align}$

On considere jusqu'a present des signaux periodiques

On peut generaliser en prenant $T \to +\infty$

On definit $TF\{x(t)\}$
$X(f) = \int_{-\infty}^{+\infty} x(t)e^{-2j \pi ft}dt$

On definit $TF^{-1}\{x(t)\}$
$x(f) = \int_{-\infty}^{+\infty} X(f)e^{+2j \pi ft}df$

> Toutes les infos contenues dans le signal sont contenues dans le spectre
> 
**Existence de la transformee de f(t)**
- $f(t)$ bornee
- Integrale de $f(t)dt$ existe
- Les discontinuites de $f(t)$ sont en nombre limite

### Transformees usuelles

- Porte
- Constante
- Peigne de Dirac

### Proprietes

- **Linearite**
$Kf(t) + g(t) \iff K F(t) + G(t)$ avec $K$ complexe

- **Similitude**
Une dilatation dans le domaine temporel correspond a une contraction dans le domaine frequentiel
> $f(at) \iff \frac{1}{|a|} F(f/a)$ avec $a$ reel

- **Derivee**
$dx(t) / dt \iff 2 i \pi f X(f)$
$dX(f) / df \iff -2 i \pi t x(t)$

Dans le cas : 
- Signal discret (echantillone) + support borne
    - TFD (Transformee de Fourier Discrete)

++Pour un signal borne et echantillone++

Soit le pic de Dirac $\delta(t)$
![](https://i.imgur.com/0ZPraIy.png)

Soit le pic de Dirac $\delta(t_0)$
- $\delta(t_0) = \delta(t - t_0)$
![](https://i.imgur.com/uCHpKzS.png)

$f(t) \delta (t_0) = f(t_0)$
![](https://i.imgur.com/SizIglg.png)


Peigne de Dirac $W(t)$ : 

$\sum_{n = -\infty}^{+\infty} \delta (t - nT)$
![](https://i.imgur.com/ZeZ2dGk.png)

$f(t) W(t_0) =$
![](https://i.imgur.com/IBl6bW2.png)


---
TFD

$X(f) = \inf_{-\infty}^{+\infty}x(t)e^{-2 j \pi ft}dt$

$X(f) = \sum_{}^{} x(t) e^{-2 j \pi ft}$

$X(l) = \sum_{k=0}^{N-1} x(kT_e)e^{-2j \pi lf_ekT_e}$

$X(l) = \sum_{k=0}^{N-1} x(k)e^{\frac{-2j \pi kl}{N}}$

$x(l) = \frac{1}{N}\sum_{l=0}^{N-1} X(l)e^{\frac{2j \pi kl}{N}}$

**notes** : 
$F_e$ : frequence d'echantillonage
- $X(0) \to -F_e / 2$
- $X(N-1) \to +F_e / 2$
- Pas en frequence : $F_e / N$

## Convolution

![](https://i.imgur.com/sAQrV07.png)


La reponse du filtre est $y(t) = x(t) * h(t) = \int_{-\infty}^{+\infty} x(u) h(t-u)du$

|Temps|Frequences|
|:--:|:--:|
|Convolution \*| Multiplication .|
|Multiplication .|Convolution \*|

- $f'*g = f *g' = (f * g)'$