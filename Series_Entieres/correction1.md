[SE] Series entieres (Correction Evaluation Formative 1)
===

## Ecritures en series entieres

++Exercice 1++ : 

$\sum_{n \geq 0} a_n x^n$

![](https://i.imgur.com/BuB5xBm.png)

a. Premier terme $(-2) + (-1)x + ...$
c. $1/x + 2/x^2+...$
e. Serie entiere dont les termes au dela de 10 sont nuls

## Rayons de convergence 

++Exercice 2++ : 

![](https://i.imgur.com/yRAkMxp.png)

a. Vrai car = 1
e. Vrai car = 1
d. Vrai car = 1
c. Faux car les series geometriques divergent au 2 bords de leur rayon de convergence

++Exercice 3++ : 

![](https://i.imgur.com/5Y9B2ie.png)

$a_n = (1/5)^n$
$\frac{a_{n+1}}{a_n} = (1/5) \times 5^n = 1/5 \to 1/5$

++Exercice 4++ : 

![](https://i.imgur.com/Sa9P4C4.png)

$\frac{2^{n+1} + 3^{n+1}}{2^n + 3^n} = 3\frac{(2/3)^{n+1} + 1}{(2/3)^n + 1} \to 3$

++Exercice 5++ : 

![](https://i.imgur.com/zyjQfOF.png)

$\frac{(n+1)^{n+1}}{n^n} \geq \frac{n^{n+1}}{n^n} = n \to +\infty$

++Exercice 6++ : 

![](https://i.imgur.com/SOzvaOj.png)

$\frac{(2(n+1))!}{((n+1)!)^2} \times \frac{(n!)^2}{(2n)!} = \frac{1}{(n+1)^2} \times (2n+2)(2n+1) \to 4$

++Exercice 7++ : 

![](https://i.imgur.com/LZQ7ZQD.png)

$1 + 0x + 0x^2 + 1x^3 + ... \to$ D'Alembert impossible, on utilise Cauchy
$x^{3n} = (x^3)^n$
Si $|x^3| < 1 \iff |x| < 1$ donc $\sum x^{3n}$ CV

++Exercice 8++ : 

![](https://i.imgur.com/LzDxtmj.png)
![](https://i.imgur.com/rsouaCU.png)

e. Calcul a la main
h. Rayon de CV 0
c. Faute dans la formule $\implies (n-10)!x^{n - 10}$ Derivee 10eme
f. $n^2 = n(n-1) + n$
$\sum n^2x^n = \sum n(n-1)x^n + \sum nx^n \to x^2 \times$ derivee 2nde de x 

## Developpements en Series entieres

++Exercice 9++ : 

![](https://i.imgur.com/TGbTfo4.png)

$\frac{1}{(2 - x)} = (1/2)(\frac{1}{1 - (x/2)}) = (1/2)\sum_{n=0}(x/2)^n = \sum \frac{x^n}{(x/2)^n}$

$\frac{1}{1-x} = \sum_{n \geq 0}x^n$

### Rappels DES
$\to \frac{1}{1+x} = \frac{1}{1- (-x)} = \sum_{n \geq 0}(-1)^nx^n$
$\to ln(1-x) = - \sum_{n \geq 0} \frac{x^{n+1}}{n+1}$
$\to \frac{-1}{(1-x)^2} = \sum_{n \geq 0} nx^{n-1}$
$\to e^x = \sum \frac{x^n}{n!}$

A partir de $e^{it} = cos(t) + isin(t)$
- $cos(t) = \sum \frac{(-1)^px^2p}{(2p)!}$
- $sin(t) = \sum \frac{(-1)^px(2p+1)}{(2p+1)!}$

++Exercice 10++ : 

![](https://i.imgur.com/YK8ZHAc.png)

e. $\frac{1}{1-x} = \sum x^n$ sur $]-1, 1[$
$= x \times \frac{1}{(1 - x)^2} = \frac{x}{(1-x)^2}$

## 
$f(x) = \frac{1}{1 - x} = \sum a_n (x-2)^n$

DES en 2

$g(y) = f(y + 2)\ \ (x = y + 2 \iff y = x - 2)$
$g(y) = \frac{1}{1 - (n-2)} = \frac{1}{-1-y} = (-1)\frac{1}{1+y} = - \sum(-1)y^n = \sum (-1)^{n+1}y^n$
