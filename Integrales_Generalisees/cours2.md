Integrales Generalisees (2)
===

**Rappel**
Notre question de depart etait de donner du sens a l'integrale d'une fonction sur un intervalle infini ou pour une integrande mal defini au bord de l'intervall d;integration. Par exemple, pour definir $\int_{0}^{+\infty}e^{-x}dx$ lorsque l'intervalle en choisissant $A \in R$ :
$$\int_{0}^{A}e^{-x}dx = [-e^{-x}]_{0}^{A} = 1 - e^{-A}$$

Cette expression en A calcule l'aire algebrique comprise entre le graphe de $e^{-x}$ et l'axe des abscisses sur [0, A]. Elle admet une limite quand $A \to +\infty$, c'est cette limite qu'on definit comme $\int_{0}^{+\infty}e^{-x}dx$
On a ici :
$$\int^{+\infty}_{0}e^{-x}dx = 1$$
On dit que $\int^{+\infty}_{0}e^{-x}dx$ est CV de valeur 1.

## Lorsqu'on ne connait pas de primitives

==**Fait**==

On ne connait pas de primitive de fonction $x \to e^{-x^2}$ exprimable a l'aide des fonctions usuelles

La demarche adoptee jusqu'a present ne permet donc pas d'etudier $\int_R e^{-x^2}dx$. C'est un soucis, cette integrale est d'une utilisation constante en probabilites. On doit donc trouver d'autres moyens de decider de la convergence des integrales generalisees.

==**Convention**==

On se contente dans la suite d'enoncer le cas des integrales *improrpes a droite*. Les cas des integrales improrpes a gauche ou bilateraales est a votre charge.

Voici la proposition au centre de cette section :

==**Proposition**==

Soient f  et g deux fonctions **positives** sur un intervalle [a,b[ $(b \in R \cup \{+\infty\})$ ou elles sont definies et continues. On suppose que $\forall x \in [a,b[$,
$$g(x) \geq f(x) \geq 0$$

- Si $\int_a^bg(x)dx$ CV, alors $\int_a^bf(x)dx$ CV aussi
- Si $\int_a^bf(x)dx$ DV, alors $\int_a^bg(x)dx$ DV aussi
---

[graphiquement]
- Si [aire sous g] < $+\infty$ alors [aire sous f] < $+\infty$
- Si [aire sous f] = $+\infty$ alors [aire sous g] = $+\infty$

++Esquisse de preuve++ :
Les fonctions $x \to \int_a^xf(t)dt$ et $x \to \int_a^xg(t)dt$
Sont croissantes et continues. La croissance vient du fait que f, g $\geq$ 0.

On a donc 2 cas possibles pour chacune (dans le cas de f) :
1. $x \to \int_a^xf(t)dt$ est bornee
2. $x \to \int_a^xf(t)dt$ n'est pas bornee

Dans le cas (1), en revenant au cas des suites (critere sequentiel de continuite), on peut montrer que $\underset{x \to b}{lim}\int_a^xf(t)dt$ existe.
Dans le cas (2) a cause de la monotonie de f, f non bornee $\Rightarrow f \underset{b}\to +\infty$

++Exemple++ :
1. $\int_{1}^{+\infty}\frac{dx}{x^2}$
$\int_{1}^{A}\frac{dx}{x^2} = [-\frac{1}{x}]^A_1 = -\frac{1}{A} + 1 \underset{A \to +\infty}\to 1$
Donc $\int_{1}^{+\infty}\frac{dx}{x^2}$ converge et $\int_{1}^{+\infty}\frac{dx}{x^2} = 1$

$\forall \alpha \geq 2$ on a sur $[1,+\infty[$, $0 \leq \frac{1}{x^{\alpha}} \leq \frac{1}{x^2}$
Donc $\int_1^{+\infty} \frac{dx}{x^{\alpha}}$ est CV

---
2. $\exists k \in R_+$ tel que $\forall x \in [k, +\infty[$, $e^{-x^2} \leq \frac{1}{x^2}$

:::info
Justification :
$x^2e^{-x^2} \to 0$ en particulier a partir d'un certain $k \in R_+, \forall x \geq k, x^2e^{-x^2} \leq 1$
:::
Donc $\int_k^{+\infty} e^{-x^2}dx$ Cv car $\int_k^{+\infty}\frac{dx}{x^2}$ CV.

On peut en deduire de plus que $\int^{+\infty}_0e^{-x^2}$ CV car
Pour $A >> 0$
$\int_{0}^{A}e^{-x^2}dx = \int_{A}^{k}e^{-x^2}dx + \int_{k}^{A}e^{-x^2}dx$

> Ou $\int_{A}^{k}e^{-x^2}dx$ est une integrale bien definie et $\int_{k}^{A}e^{-x^2}dx$ une integrale deja etudeie

Que dire de $\int_{-\infty}^0 e^{-x^2}dx$ ?
- Si $A \in R_-, \int_{A}^0 e^{-x^2}dx$ ets egale a $\int_{0}^{-A} e^{-x^2}dx$, car $x \to e^{-x^2}$ est paire.

:::danger
**Remarque** :
1. Le fait d'etre positif est essentiel dans la proposition precedente
2. On peut relaxer cette hypothese tant que f et g dont de meme signes constant
:::

Le resultat precendent a 2 consequences suivantes :

==**Proposition**==

Soient f et g deux fonctions continues sur [a,b[ et de signes $\geq 0$. Sur ce meme intervalle :
1. Si $f \underset{b}\sim g$ alors $\int_{a}^{b}f(t)dt$ et $\int_{a}^{b}g(t)dt$ sont de meme natures.
2. Si $f = \mathcal{O}_a(g)$
    - Si $\int_{a}^{b}g(t)dt$ CV alors $\int_{a}^{b}f(t)dt$ CV
    - Si $\int_{a}^{b}f(t)dt$ DV alors $\int_{a}^{b}g(t)dt$ DV

:::danger
**Remarque :**
La proposition suivante repose sur le fait que :
1. $f = \mathcal{O}_a(g)$ signifie que $\exists k \in R_+$ tel que $f \leq kg$ (au voisinage de b)
2. $f \underset{b}\sim g$, $\exists k, K \in R_+$ tel que $kg \leq f \leq Kg$ (au voisinage de b)
:::

## Kit de survie

Soient f et g deux fonctions definies au voisinage d'un point a (sur un intervalle ouvert centre en a). On suppose que g n'est pas nulle sur un voisinage de a (a exclu).
:::info
Comparer f et g en a, c'est etudier le rapport f/g au voisinage de a.
:::

:::danger
1. $\sim_a$ : $\frac{f}{g} \underset{a}\to 1$
2. $f = \mathcal{o}_a(g)$ : $\frac{f}{g} \underset{a}\to 0$
3. $f = \mathcal{O}_a(g)$ : $\frac{f}{g}$ est majore en a
:::
:::danger
$f \sim_a g \Rightarrow \mathcal{O}_a(g)$
$f = \mathcal{o}_a(g) \Rightarrow f = \mathcal{O}_a(g)$
:::

==**Definition propre**==

Il existe une fonction $\varepsilon$ au voisinage de a telle que $f = \varepsilon g$
1. $f \sim_a g$ : $\underset{t \to a}{lim}\ \varepsilon(t) = 1$
2. $f = \mathcal{o}_a(g)$ : $\underset{t \to a}{lim}\ \varepsilon(t) = 0$
3. $f = \mathcal{O}_a(g)$ : $\varepsilon$ est majore au voisinage de a.

## Exercices

1. $\int_0^1\frac{dt}{t^{\alpha}}$ pour $\alpha \in R$
- (a) Si $\alpha \leq 0$ est continue et definie sur [0,1] (pas de soucis en 0)

On se limite donc au cas $\alpha > 0$
On cherche une primitive de $t^{-\alpha}$ :
- Si $\alpha = 1$,  $\int_{}^{x}t^{-\alpha}dt\ ln(t)$
- Si $\alpha \neq 1$: $\int^x t^{-\alpha}dt = \frac{1}{(1 - \alpha)t^{\alpha -1}}$

$\int_{0}^{1}\frac{dt}{t^{\alpha}}$ est une integrale impropre en 0.
- Si $\alpha = 1$ : $\int_{A}^{1} \frac{dt}{t} = [ln(t)]^{1}_{A} = -ln(A)$ qui n'a pas de limite reelle en 0.
- Si $\alpha \neq 1$, $\int_{A}^{1}\frac{dt}{t^{\alpha}} = [\frac{1}{(1-\alpha)^{\alpha - 1}}]^{1}_{A} = \frac{1}{1 - \alpha} - \frac{1}{(1 - \alpha)A^{\alpha - 1}}$
    - Si $\alpha > 1$ : $\frac{1}{A^{\alpha - 1}}$ n'a pas de limite
    - Si $\alpha \in ]0,1]$ : $\frac{1}{A^{\alpha - 1}} \underset{A \to 0}{\to} 0$
- (b) Si $\alpha  \geq 1$, on DV
- (c ) Si $\alpha \in ]0,1[$ on CV
---
:::info
**En conclusion**
$\begin{align}\int_{0}^{1}\frac{dt}{t^{\alpha}}\ CV \iff \alpha < 1\end{align}$
En effectuant le meme type d'etudes on a $\begin{align}\int_{1}^{+\infty}\frac{dt}{t^{\alpha}}\ CV\ ssi\ \ \alpha > 1\end{align}$
:::

:::info
**Aide**
Comment trouver des equivalents d'une fonction de f en a dont on a un DL a l'ordre n en a.

$\begin{align}f(a + x) &= f(a) + f'(a)x + \frac{f''(a)}{2}x^2 + \mathcal{o}_o(x^2) \\ &=(f(a) + f'(a)x + \frac{f''(a)}{2}x^2)X\end{align}$
:::

2. $\begin{align}\int_0^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt\end{align}$

On a eventuellement les deux points du bord qui posent probleme :

- ++En 0++ :
$\frac{t^4}{(t^5 + 1)\sqrt{t}} \underset{0}\sim \frac{t^4}{\sqrt{t}} = t^{7/2}$ $\to$ L'integrande est continue et definie en 0

- ++En $+\infty$++ :
$\frac{t^4}{(t^5 + 1)\sqrt{t}} = \frac{t^4}{t^5\sqrt{t}(1 + \frac{1}{t^5})} = \underset{+\infty}\sim \frac{t^4}{t^5\sqrt{t}} = \frac{1}{t\sqrt{t}} = \frac{1}{t^{3/2}}$

Comme $\frac{1}{t^{3/2}} \geq 0$ sur $[1,+\infty[$ de meme que $\frac{t^4}{(t^5 + 1)\sqrt{t}}$ et $\frac{1}{t^{3/2}} \underset{+\infty}{\sim} \frac{t^4}{(t^5 + 1)\sqrt{}t}$

$\int_0^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt$ est de meme nature que $\int_{1}^{+\infty}\frac{dt}{t^{3/2}}$. C'est une integrale de Riemann CV.

:::info
$\begin{align}\int_0^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt = \int_0^{1} \frac{t^4}{(t^5+1)\sqrt{t}}dt + \int_1^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt\end{align}$
Donc $\begin{align}\int_0^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt\end{align}$ CV (somme de 2 integrales convergentes)
:::

> Ou $\int_0^{1} \frac{t^4}{(t^5+1)\sqrt{t}}dt$ est definie et $\int_1^{+\infty} \frac{t^4}{(t^5+1)\sqrt{t}}dt$ CV d'apres ce qui precede.

---

3. $\begin{align}\int_0^{+\infty}t^{\alpha}e^{-t}dt\end{align}$ avec $\alpha \in R$

---

4. $\begin{align}\int^{\pi}_{0}ln(sin(t))dt\end{align}$

---

5. $\begin{align}\int_0^1cos^2(\frac{1}{t})dt\end{align}$

---

6. $\begin{align}\int_{0}^{+\infty}(1 - cos(\frac{1}{t}))dt\end{align}$

---

7. $\begin{align}\int^{\pi / 2}_{0}\frac{sin(t)}{t}dt\end{align}$

---

8. $\begin{align}\int_0^{\pi}\frac{cos(t)}{t^2}dt\end{align}$
