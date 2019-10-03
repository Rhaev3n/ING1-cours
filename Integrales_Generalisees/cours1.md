Integrales generalisees (1)
===

## Objectifs
- Etre en mesure de saisir la difficulte liee au fait de travailler avec des integrales infinies.
- Savoir manipuler ces integrales generalisees dans le cadre des *probabilites*

### 1. Problematisation
> On s'interresse a la question de la decomposition d'un materiel radioactif. La question se pose en terme de probabilites : quelle est la probabilite qu'une particule se desintegre a un moment donne ?

Les modeles mathematiques qui permettent de donner une reponse a cette question vont donner une *probabilite nulle aux evenements instantanes* et une *probabilite positive sur les intervalles de temps*, non reduits a un singleton. Ces modeles font apparaitre des **integrales de fonctions positives** (qu'on appelle densites). Le premier modele qu'on retient pour modeliser le cas de la desintegration est utile de la **loi exponentielle**. 

## Loi exponentielle
Si l'on note X la variable aleatoire qui correspond au temps de desintegration d'une particule. On a 
$$\mathbb{P}(X \in ]a, b[) = \int^{b}_{a} \lambda e^{-\lambda t}dt$$
$a, b \in \mathbb{R}$ et $\lambda \in \mathbb{R}^*_+$ depend du materiau

![](https://i.imgur.com/Uni7dwa.png)

[// Loi exponentielle](https://jaicompris.com/lycee/math/probabilite/loi-exponentielle.php)

----------
:::warning
**Question**
Quelle est la probabilite que l'on ait une desintegration apres un temps $T \in \mathbb{R}_+$

Autrement dit, $\begin{align}\int^{+ \infty}_T \lambda e^{-\lambda t}dt\end{align}$ ?
:::

++Ce qu'on sait faire pour l'instant++ : 
- On sait integrer une fonction **continue** sur un **segment** (un intervalle ferme et borne). Dans ce cadre quand on a une primitive la valeur de l'integrale correspond a la difference des valeurs que prend la primitive sur les bornes.

> Integrale = Valeur d'une aire algebrique, comprise entre la courbe du graphe et la courbe des abscisses (entre ses bornes)

++On pose une deuxieme borne arbitraire finie A++ : 
$\begin{align}
\int^A_T \lambda e^{-\lambda t}dt &= [ -e^{- \lambda t} ]^A_T \\
& = ( -e^{-\lambda A} + e^{-\lambda T})
\end{align}$

On sait maintenant calculer l'aire sous la courbe entre T et A.
On cherche a estimer l'aire entre T et A en faisant tendre $A \to +\infty$
Des qu'on parle de limite, il faut garder en memoire le fait que celle-ci peut ne pas exister. 

Dans notre cas $( -e^{-\lambda A} + e^{-\lambda T})$ a une limite finie en $+ \infty$ donnee par $e^{-\lambda T}$
Donc $\begin{align}\int^{b}_{a} \lambda e^{-\lambda t}dt = e^{-\lambda T}\end{align}$

--------------
## Definitions

==**Definition (Integrale generalisee)**== : 
Soit f une fonction continue et definie sur $]a, b[$ avec $a, b \in ]\mathbb{R}\ U {-\infty, +\infty}$. Une **integrale generalisee** est de l'une des 3 formes suivantes ($\int^b_a f(t)dt$) :
1. **Definie** : f est en fait continue sur $[a, b]$
2. **Impropre a gauche (resp a droite)** : f n'est pas definie en a (resp en b)
3. **Bilaterale** : f n'est definie ni en a ni en b


**Exemples**
1. $\int^1_0 x dx$ est une integrale *definie* sur $[0,1]$
> 1(bis). $\int^1_0 xln(x)dx$ est bien *definie* sur $[0, 1]$ ($xln(x) \underset{x \to 0}\to 0$)
2. $\int^1_0 ln(x) dx$ est *impropre a gauche* (pas definie en 0)
3. $\int^{+\infty}_0 \frac{dx}{x}$ est *bilaterale*

------------------
==**Definition (integrale impropre a gauche convergente)**==

Soit $\int^b_a f(t)dt$ une **integrale impropre a gauche**. On dit que $\int^b_a f(t)dt$ **converge** si la fonction $A \to \int^b_A f(t)dt$ a une limite finie quand $A \to a$.
On note dans ce cas
$$\int^b_a f(t)dt = \underset{A\to a}{lim} \int^b_Af(t)dt$$

:::info
**Note** : La notation $\int^b_a f(t)dt$ sert pour noter l'objet integrale generalisee mais egalement la valeur de l'aire algebrique  comprise entre le graphe de la fonctione et l'axe des absisses, **quand celle-ci existe** (et pour cette raison il faut toujours se poser la question de la convergence d'une integrale avant d'en manipuler la somme)
:::

:::danger
**Remarque** : Le cas des integrales impropre a droite se traite de maniere similaire, la difference etant qu'on etudie la limite 
$$\underset{B \to b}{lim} \int^B_a f(t)dt$$
:::

-----------------------------------------------------
==**Definition (integrale bilaterale convergente)**==

Une **integrale bilaterale** $\int^b_a f(t)dt$ **converge** si pour un quelconque $c \in ]a, b[$, ++les deux++ integrales $\int^c_a f(t)dt$ et $\int^b_c f(t)dt$ convergent.

Dans ce cas, la **somme** est donnee par : 
$$\int^b_a f(t)dt = \int^c_a f(t)dt + \int^b_c f(t)dt$$

> Pourquoi cette definition ?
> 1. $\begin{align}\int^A_{-A}tdt = \frac{A^2}{2} - \frac{A^2}{2} = 0 \underset{A \to +\infty}\to 0\end{align}$
> 2. $\begin{align}\int^A_{-A-1}tdt = \frac{A^2}{2} - \frac{(-A-1)^2}{2} = -A + \frac{1}{2} \underset{A \to +\infty}\to {+\infty}\end{align}$

-----------
## Exemples

1. $\begin{align}\int^{+\infty}_1e^{-2t}dt &= -\frac{1}{2}[e^{-2t}]^{+\infty}_{1} \\ &= \frac{e^{-2}}{2}\end{align}$
> On a une integrale impropre a droite. Soit $B \in \mathbb{R}_+$, on s'interesse a $\int^{B}_{1}e^{-2t}dt$
> On pose un $B \to +\infty$

$\begin{align}\int^{B}_1e^{-2t}dt &= -\frac{1}{2}[e^{-2t}]^{B}_{1} \\ &= - \frac{e^{-2B}}{2} + \frac{e^{-2}}{2}\end{align}$

$\int^{B}_1e^{-2t}dt$ a une limite quand $B \to +\infty$
$\underset{B \to +\infty}{lim}int^{B}_1e^{-2t}dt = \frac{e^{-2}}{2}$

:::warning
$\int^{+\infty}_1e^{-2t}dt$ est donc convergente et on a $\int^{+\infty}_1e^{-2t}dt = \frac{e^{-2}}{2}$
:::

:::danger
**Rappel integration par parties**
$$\int^{b}_{a}u'(t)v(t)dt = [uv]^b_a = \int^b_a u(t)v'(t)dt$$
:::

2. $\begin{align}\int^{1}_{0} ln(t)dt &= [tln(t)]^{1}_{0} - \int^b_a dt \\ &= 0 - [t]^1_0 \\ &= -1\end{align}$
> $\begin{align}\int^{1}_{A} ln(t)dt &= [tln(t) - t]^{1}_{A} \\
&= -1 - Aln(A) + A\ ou\ (-Aln(A) + A) \underset{B \to 0}{\to} 0\end{align}$

:::warning
$\int^{1}_{0} ln(t)dt$ admet une limite quand $A \to 0$
On a donc $\int^{1}_{0} ln(t)dt = -1$
:::

3. $\begin{align}\int^{1}_{0} \frac{dt}{t}\end{align}$
> C'est une integrale impropre a  gauche. 
Soit $A \in \mathbb{R}_+$

$\begin{align}\int^{1}_{A} \frac{dt}{t} &= [ln(t)]^{1}_{A} \\
&= - ln(A)\end{align}$

:::warning
Cette expression tend vers $+\infty$ quand $A \to 0$. Cette integrale impropre n'est donc pas convergente.
:::

3. $\begin{align}\int^{+\infty}_{1} \frac{dt}{t^2}\end{align}$
> C'est une integrale impropre a droite. 
Soit $B \in \mathbb{R}_+$

$\begin{align}\int^{+\infty}_{B} \frac{dt}{t^2} &= [-\frac{1}{t}]^{+\infty}_{B} \\
&= -\frac{1}{B} + 1\ ou\ (-\frac{1}{B} + 1) \underset{B \to +\infty}{\to} 1 \end{align}$

:::warning
Ainsi Elle est CV et = 1
:::

4. $\begin{align}\int^{1}_{0} \frac{dt}{t^{\alpha}} &= [-\frac{1}{(\alpha - 1)x^{\alpha - 1}}]^{1}_{0} \\ 
&= -\frac{1}{\alpha - 1} + \frac{1}{\alpha - 1} \\ 
&= 0\end{align}$

4. $\begin{align}\int^{+\infty}_{1} \frac{dt}{t^{\alpha}}\end{align}$
5. $\begin{align}\int^{+\infty}_{0} \frac{dt}{t^{\alpha}} = ?\end{align}$