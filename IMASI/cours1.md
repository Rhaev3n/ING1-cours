[IMASI] Introduction aux mathematiques du signal (1)
===

[// notebooks](https://www.lrde.epita.fr/~gtochon/MASI/)
> Partiel = QCM de 1h

# Definitions

**Signal** : Observation / Mesure d'un phenomene physique ou chimique  variant dans k;espace et / ou le temps et qui transporte de l'information
- $f(x, y, z, t)$

### Types de signaux

- **Analogique** : continu par rapport a la position / temps $\Rightarrow$ signaux "natifs", naturels
- **Numerique** : discret par rapport a toutes ses variables $\Rightarrow$ stockes sur un ordinateur (memoire finie)


$x: I \subset \mathbb{R} \to \mathbb{R}\ ou\ \mathbb{C}$
$\ \ \ \ \ \ t \to x(t)$

- x est de module **borne** : $|x(t)| < +\infty\ \  \forall t \in I$
- x est continu / possede un nombre fini de discontinuites

![](https://i.imgur.com/m4SPNx7.png)
Signal OK

# Signaux et vecteurs

L'ensemble des signaux a une structure d'espace vectoriel
Avec $x_1$ signal, $x_2$ signal, $\lambda$ constante
- $x_1 + x_2 \to$ signal
- $\lambda x_1 \to$ signal

$<\overset{\to}x, \overset{\to}y> = ||\overset{\to}x||.||\overset{\to}y||.cos(\Theta)$
$||\overset{\to}x|| = \sqrt{x_1^2 + x_2^2} = \sqrt{<\overset{\to}x, \overset{\to}x>}$

**En dimension n** : 
$\overset{\to}x \begin{cases}x_1 \\ . \\ . \\ x_n\end{cases}$  ;   $\ \ \ \overset{\to}y \begin{cases}y_1 \\ . \\ . \\ y_n\end{cases}$

$\begin{align}<\overset{\to}x, \overset{\to}y> &= x_1y_1 + ... + x_ny_n \\ &= \sum_{i = 1}^nx_iy_i\end{align}$

### Definition generale

E un espace vectoriel

$<,>: E \times E \to mathbb{R}$
$\ \ \ \ \ \ \ \ \ \ (\overset{\to}x, \overset{\to}y) \to <\overset{\to}x, \overset{\to}y>$

### 4 axiomes

- **Symetrie** : $\forall \overset{\to}x, \overset{\to}y \in E,  <\overset{\to}x, \overset{\to}y> = <\overset{\to}y, \overset{\to}x>$
- **Bilineaire** : $\forall \overset{\to}x_1, \overset{\to}x_2, \overset{\to}y \in E, \forall \lambda \in \mathbb{R}, <\overset{\to}x_1, \lambda \overset{\to}x_2, \overset{\to}y> = <\overset{\to}x_1, \overset{\to}y> + \lambda <\overset{\to}x_2, \overset{\to}y>$
- **Positif** : $<\overset{\to}x, \overset{\to}y> \geq 0$
- **Fefini** : $<\overset{\to}x, \overset{\to}y> = 0 \iff x = 0_E$

### Distance

$\begin{align}d(\overset{\to}x, \overset{\to}y) &= ||\overset{\to}x - \overset{\to}y|| \\ &= \sqrt{<\overset{\to}x - \overset{\to}y, \overset{\to}x - \overset{\to}y>}\end{align}$

> vecteur : espace discret

### Fonction integrable

**==Definition==**

Une fonction est dite *integrable* sur $I \subset \mathbb{R}$ ssi 
$\int_I |f(t)|dt < +\infty$ 

Une fonction est dite *p=integrable* sur $I \subset \mathbb{R}$ ssi
$\int_I |f(t)|^pdt < +\infty$ $\ \ \ \ f \in \mathcal{L}^p(I)$

++Exemple++ (pour p = 2) : 

$x \in \mathcal{L}^2(x), \ \ \int_I|x(t)|^2dt$

si $I = \mathbb{R}, \int_{\mathbb{R}}|x(t)|^2dt = Ex$ (energie du signal)

$\Rightarrow \mathcal{L}^2(\mathbb{R}) \equiv$ **espace des signaux d'energie finie**