[IMASI] Introduction aux mathematiques du signal (2)
===

[// notebooks](https://www.lrde.epita.fr/~gtochon/MASI/)


## Autocorrelation 

Soient $x, y \in \mathcal{L}^2(\mathbb{R}), <x(t), y(t)> = \int_{-\infty}^{+\infty}x(t)\overline{y(t)}dt$

Si x et y a valeur reelle $\int_{-\infty}^{+\infty}x(t)y(t)dt$

$\int_{\mathbb{R}}|x(t)|^2dt \ \int_{\mathbb{R}}x(t)\overline{x(t)}dt = <x(t), x(t)> = ||x||^2 = Ex$

$y(t - \gamma)$ est a version retardee de y d'un temps $\gamma$

$<x(t), x(t - \gamma)> = \int_{\mathbb{R}}x(t)\overline{x(t - \gamma)}dt = \Gamma_{xx} =$ autocorrelation

- $\Gamma_{xx}(0) = <x(t), x(t - 0)> = \int_{\mathbb{R}}|x(t)|^2dt = ||x||^2 = Ex =$ energie du signal
- $\forall \gamma \in \mathbb{R}, |\Gamma_{xx}(\gamma)| = \Gamma_{xx}(0) \to$ autocorrelation maxinale en 0 (quand $\gamma = 0$)
- $\Gamma_{xx}$ est a symetrie hernitienne : $\Gamma_{xx}(-\gamma) = \overline{\Gamma_{xx}(\gamma)}$
	- Dans le cas reel : $\Gamma_{xx}(-\gamma) = \Gamma_{xx}(\gamma) \Rightarrow$ l'autocorrelation est **paire**

## Inter-correlation

$\Gamma_{xy}: \gamma \to <x(t), y(t- \gamma)> = \int_{\mathbb{R}}x(t)\overline{y(t - \gamma)}dt$
$\Gamma_{xy}(\gamma) =$ ressemblence entre $x$ et $y$ retarde de $\gamma$

$y(t) = x(t - t_0)$: x retarde de $\begin{align}t_0 \to \Gamma_{xy}(\gamma) &= <x(t), y(t - \gamma)> = <x(t), x(t - t_0 - \gamma)> \\ &= <x(t), x(t - (t_0 + \gamma))> \\ &= \Gamma_{xx}(t_0 + \gamma)\end{align}$

Autocorrelation maximale en 0: $t_0 + \gamma = 0 \iff \gamma = - t_0$
$\Gamma_{xy}(-t_0)$ est maximale

Pour 2 signaux x et y avec un retard $t_0$ inconnu : 
1. Calcul
2.

## Convolution

Le produit de convolution de 2 fonctions f et g est defini comme la fonction $h: t \to h(t) = (f \times g)(t) = \int_{\mathbb{R}}f(x)g(t - x)dx$

- Existence du produit de convolution : $f\ et\ g \in \mathcal{L}^1(\mathbb{R})$, alors $(f \times g)$ existe et $(f \times g) \in \mathcal{}L^1(\mathbb{R})$

==**Proprietes**==
- **Commutatif** : $f \times g = g \times f$
- **Bilineaire** : $f \times (g + \lambda h) = f \times g + \lambda f \times h$
- **Associatif** : $(f \times g) \times h = f \times (g \times h)$
- **Element neutre** : $f \times g = g \times f = f \Rightarrow g \equiv$ Delta de Dirac : $\gamma: \to t \begin{cases} 0,\ t \neq 0 \\+\infty,\ t = 0 \end{cases}$ et $\int_{\mathbb{R}}\gamma(t)dt = 1$
- **Derivation** : f et g derivables, $(f \times g)'(t) = (t' \times g)(t) = (f \times g')(t)$
- **Symetrie** : si f et g sont des fonctions paires ou impaires
	- $(f \times g)$ est pair si f et g sont de meme parite
	- $(f \times g)$ est impair si f et g de parites contraires