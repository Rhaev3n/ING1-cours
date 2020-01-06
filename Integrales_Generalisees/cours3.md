Integrales Generalisees (3)
===

## Exercices (suite)

3. $\begin{align}\int_0^{+\infty}t^{\alpha}e^{-t}dt\end{align}$ avec $\alpha > 0$

:::danger
**Rappel (puissances)**

Soit $x \in \mathbb{R}^*_+$
- Si $n \in N, x^n = x \times x \times x \times ... \times x$ (n fois) ($x \in \mathbb{R}$ marche)
- Si $n \in \mathbb{Z}^*_-, x^n = 1/x \times 1/x \times ... \times 1/x$ (n fois) ($x \in \mathbb{R}^*$ marche)
- Avec $p, q \in N,\ p \times q = 1$,  $\ x^{p/q} = (x^{1/q})^p; x^{1/q}$ est :
    - l'unique reel y tel que $y^q = x$ et $y \geq 0$ quand q est pair ($x \in \mathbb{R}_+$)
    - l'unique reel y tel que $y^q = x$ quand q est impair ($x \in \mathbb{R}$)

Donc : 
- Si $\alpha \in R / R, x^{\alpha} = e^{\alpha ln(x)}$ (x ne peut qu'etre dans $R_+^*$)

Sur $R_+^*$ toutes les definitions precedentes pour $n \in N$ se confondent : 
- $x^n = e^{nln(x)}$
- $x^{p/q} = e^{p/q\ ln(x)}$
:::

Ici on a $t \to e^{-t}t^{\alpha}$ est une fonction continue sur $R_+^*$. L'integrale est au moins prorpe en $+\infty$

++En 0++ : 
$t^{\alpha}e^{-t} = e^{\alpha\ ln(t)}e^{-t} \underset{t \to 0}\to 0$
> Ou $e^{\alpha\ ln(t)} \underset{t \to 0}\to 0$ et $e^{-t} \underset{t \to 0}\to 1$

Notre integrale est donc impropre en $+\infty$

On cherche a justifier le fait que $t^{\alpha}e^{-t}$ est comparabl e a $\frac{1}{t^2}$ qui est une fonction dont $\int_{1}^{+\infty}\frac{dt}{t^2}$ est CV

On veut justifier que $t^{\alpha}e^{-t} = \mathcal{O}_{+\infty}(\frac{1}{t^2})$
$\frac{t^{\alpha}e^{-t}}{1/t^2} = t^2t^{\alpha}e^{-t} = t^{2 + \alpha}e^{-t} \underset{t \to +\infty}\to 0$

Comme $t^{\alpha}e^{-t} = o_{+\infty}(1/t^2)$. 

C'est en particulier $\mathcal{O}_{+\infty}(1/t^2)$. Les fonctions  en jeu etant positives, $\begin{align}\int_{0}^{+\infty} t^{\alpha}e^{-t}dt = \int_{0}^{1}t^{\alpha}e^{-t}dt + \int_{1}^{+\infty}t^{\alpha}e^{-t}dt\end{align}$
> $\int_{0}^{+\infty} t^{\alpha}e^{-t}dt$ CV
> Ou $\int_{0}^{1}t^{\alpha}e^{-t}dt$ bien definie et $\int_{1}^{+\infty}t^{\alpha}e^{-t}dt$ CV d'apres phrase du dessus

---

4. $\begin{align}\int^{\pi}_{0}ln(sin(t))dt\end{align}$

La fonction $\Gamma$ d'Euler est une fonction donnee par une integrale generalisee. On a


---

5. $\begin{align}\int_0^1cos^2(\frac{1}{t})dt\end{align}$

$0 \leq cos^2(\frac{1}{t}) \leq 1$ sur ]0, 1]

$\begin{align}\int_{0}^{1}1dt\end{align}$ est CV donc $\begin{align}\int_{0}^{1} cos^2(\frac{1}{t})dt\end{align}$ l'est aussi

Par changement de variable, $\int_{0}^{1}cos^2(\frac{1}{t})dt = \int_{1}^{+\infty}\frac{cos^2(u)}{u^2}du$
> Ou $\frac{cos^2(u)}{u^2} = \mathcal{O}_{+\infty}(\frac{1}{u^2})$

---

6. $\begin{align}\int_{0}^{+\infty}(1 - cos(\frac{1}{t}))dt\end{align}$

++En 0++ : 
$cos(x) = 1 - \frac{x^2}{2} + \mathcal{O}_0(x^2)$

Du coup en $+\infty$, $cos(x) = 1 - \frac{1}{2t^2} + \mathcal{O}_{+\infty}(\frac{1}{t^2})$
Ou encore $1 - cos(\frac{1}{t}) = \frac{1}{2t^2} + \mathcal{O}_{+\infty}(\frac{1}{t^2})$

:::danger
**Rappel**
$\begin{align} 1 - cos(\frac{1}{t}) &= \frac{1}{2t^2} + \frac{\varepsilon(t)}{t^2}\ (Avec\ \varepsilon(t) \underset{t \to +\infty} \to 0)\\ &= \frac{1}{2t^2} (1 + 2\varepsilon(t) \underset{t \to +\infty}\to 1)\end{align}$
:::

Comme les fonctions en jeu sont positives, 
$\begin{align}\int_{2}^{+\infty}(1 - cos(\frac{1}{t}))dt\end{align}$ est de meme nature que 
$\begin{align}\int^{+\infty}_{2} \frac{dt}{2t^2} = \frac{1}{2} \int_{2}^{+\infty} \frac{dt}{t^2}\end{align}$ qui est une integrale de Riemann CV.

---

7. $\begin{align}\int^{\pi / 2}_{0}\frac{sin(t)}{t}dt\end{align}$

---

8. $\begin{align}\int_0^{1}\frac{cos(t)}{t^2}dt\end{align}$

On a une integrale impropre en 0.

$\frac{cos(t)}{t^2} = \frac{1 - \frac{t^2}{2} + \mathcal{O}_0(t^2)}{t^2} = \frac{1}{t^2} - \frac{1}{2} + \mathcal{O}_0(1)$

On a donc $\frac{cot(t)}{t^2} \sim_0 -\frac{1}{2} + \frac{1}{t^2}$

$\int_{0}^{1} \frac{cos(t)}{t^2}dt$ est de meme nature que $\int_{0}^{1}(-\frac{1}{2} + \frac{1}{t^2})dt$ 

> $\int_{0}^{1}(-\frac{1}{2} + \frac{1}{t^2})dt$ est une integrale DV car $\int_0^1 - \frac{1}{2}dt + \int_0^1 \frac{dt}{t^2}$ et $\int_0^1 \frac{dt}{t^2}$ DV

--------
$\begin{align}\Gamma(\alpha) = \int_{0}^{+\infty}e^{-t}t^{\alpha - 1}dt\end{align}$

++Question++ : 
Pour quelle valeur de $\alpha\ \ \Gamma(\alpha)$ est definie ?

- On note $f(x) = = \frac{1}{\Gamma(p)}e^{-x}x^{p - 1}$, $1|_{R^*_+}(x)$ ou $p \in \mathbb{N}^*$
- f est la densite d'une variable aleatoire qui suit la loi $\gamma$

> $1|_{R^*_+}(x) = \begin{cases}1\ si\ x\ \in \mathbb{R}^*_+ \\ 0\ sinon\end{cases}$ 

$\mathbb{P}(X \in [a,b]) = \int_{a}^{b} f(x)dx$

Calculer E(X)


++En $+\infty$++ :   
On compare $t^{\alpha - 1}e^{-t}$ a $\frac{1}{t^2}$. On a $t^2t^{\alpha-1}e^{-t} \underset{t \to +\infty} \to 0$

Donc $t^{\alpha -1}e^{-t} = \mathcal{O}_{+\infty}(\frac{1}{t^2})^{t^2}$

$\int_{1}^{+\infty} t^{\alpha-1}e^{-t}dt$ est de meme nature que $\int_1^{+\infty} \frac{dt}{t^2}$ ie CV

++En 0++ :   
$t^{\alpha-1}e^{-t} \sim_0 t^{\alpha-1}$

$\int_{0}^{1} t^{\alpha - 1}e^{-t}dt$ est de meme nature que $\int_{0}^{1} \frac{dt}{t^{1 - \alpha}}$  
$\int_{0}^{1} \frac{dt}{t^{1 - \alpha}}$ CV $\iff 1 - \alpha < 1 \iff 0 < \alpha$
