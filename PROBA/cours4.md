[PROBA] Probabilites discretes (4)
===

## Loi de Poisson de parametre $\lambda\mathcal{P}(\lambda)$

C'est la loi d'une variable aleatoire entiere positive qui satisfait  
$\begin{align}P(X=k) = e^{-\lambda}\frac{\lambda^k}{k!}\ \ \forall k \in \mathbb{N}\end{align}$

On obtient la loi de Poisson comme une approximation de la loi $B(n,p)$

==**Theoreme**==

La loi $B(n,p)$ **converge en loi** vers la loi de Poisson $\mathcal{P}(\lambda = np)$ lorsque $n \to +\infty$ et $p \to 0$

:::info
**Remarque** : 
En pratique, $B(n, p) \simeq \mathcal{P}(\lambda = np)$ des que $p<0,1$ et $n > 50$
:::

------------
**Esperance**

$E(X) = \sum_{k=0}^{+\infty} k P(X=k) = \sum^{+\infty}_{k=0} ke^{-\lambda}\frac{\lambda^k}{k!}$

$E(X) = e^{-\lambda} = \sum^{+\infty}_{k=1} \frac{\lambda^k}{(k-1)!}$
> Faire apparaitre le developpement en series de l'exponentielle

$E(X) = e^{-\lambda}\lambda \sum_{k=1}^{+\infty}\frac{\lambda^{k-1}}{(k-1)!} = e^{-\lambda}\lambda e^{\lambda}$

$E(X) = \lambda$

**Variance**

$V(X) = E(X^2) - E^2(X)$

$E(X) = \sum_{k=0}^{+\infty} k^2 e^{-\lambda} \frac{\lambda^k}{k!} = e^{-\lambda} \sum_{k=1}^{+\infty} k \frac{\lambda^k}{(k-1)!}$

$E(X^2) = e^{-\lambda} \sum{k=1}^{+\infty} = (k - 1 + 1) \frac{\lambda^k}{(k-1)!} = e^{-\lambda} (\sum{k=2}^{+\infty} \frac{\lambda^k}{(k-2)!} + \sum_{k=1}^{+\infty} \frac{\lambda^k}{(k-1)!})$

$E(X^2)= e^{-\lambda}(\lambda^2\sum_{k=2}^{+\infty}\frac{\lambda^{k-2}}{(k-2)!} + \lambda\sum_{k=1}^{+\infty} \frac{\lambda^{k-1}}{(k-1)!})$

$E(X^2) = (\lambda^2e^{\lambda} + \lambda e^{\lambda}) = \lambda^2 + \lambda$

$V(X) = \lambda^2 + \lambda - \lambda^2 = \lambda \implies V(X) = \lambda$

## Loi hypergeometrique $H(N, n, p)$

Soit une population de $N$ individus parmis lesquels une proportion $p$ possede un certain caractere (propriete).

On preleve un echantillon de $n$ individus dans cette population (tirage sans remise).

Soit $X$ la variable aleatoire qui represente le nombre d'individus de l'echantillon possedant le caractere

$\begin{align}P(X=k) = \frac{\binom{Np}{k}\binom{N-Np}{n-k}}{\binom{N}{n}}\end{align}$

> $\binom{Np}{k}$ : nombre de groupes de k individus possedant le caractere
> 
> $\binom{N-Np}{n-k}$ : nombre de groupes de n-k individus ne possedant pas le caractere
> 
> $\binom{N}{n}$ : nombre d'echantillons possibles

On dit que $X$ suit la loi hypergeometrique $H(N, n, p)$

:::info
**Remarque** : 
$H(N, n, p) \overset{CV en loi}\to_{N \to +\infty} B(n, p)$

En pratique, cette approximation est tres satisfaisante des que le "taux de sondage" $\frac{n}{N} < 10\%$
:::

$E(X) = np$

$V(X) = (\frac{N-n}{N-1}) npq\ \ ou\ q = 1 -p$

## Loi geometrique et loi de Pascal

La ==**loi geometrique**== est la loi du nombre d'essais necessaires pour faire apparaitre un evenement $A$ de probabilite p

$P(X=k) = (1-p)^{k-1}\times p = q^{k-1}p$ avec $q = 1-p\ \ \forall k \geq 1$

$E(X) = 1/p$

$V(X) = q / p^2$ avec $q = 1-p$

La ==**Loi de Pascal**== est la loi du nombre d'essais necessaire pour observer $n$ fois un evenement $A$ de probabailite $p$.

L'experience se termine par A

:::info
**Remarque** : 
On retrouve la loi geometrique si on prend $n=1$
:::

$P(X=k) = p\binom{k-1}{n-1} p^{n-1} (1-p)^{k-n}$

$P(X=k) = \binom{k-1}{n-1} p^n q^{k-n}\ \ \forall k \geq n$

$X = \sum_{i=1}^{n}X_i$ somme independante de lois geometrique
$X_i$ suit la loi $G(p)$

$E(X) - \sum_{i=1}^{n} E(X_i) = \sum_{i=1}^{n} 1/p$

$E(X) = \frac{n}{p}$

$V(X) = \sum_{i=1}^{n} V(X_i) = \sum_{i=1}^{n} q/p^2 = \frac{nq}{p^2}$ car $X_i$ sont independantes

### Rappels 
- Bernouilli : 1 epreuve, issue soit 0 ou 1
- Binomiale : Plusieurs Bernouilli
- Hypergeometrique : Certain caractere dans population
- Geometrique : Plusieurs essais, apparition d'un phenomene pour la premiere fois 
- Pascal : Plusieurs essais, apparition d'un phenomene n fois

## Exercices

++Exercice 1++ : 

La proportion de pieces defectueuses dans un lot de pieces est de 5%. Le controle de fabrication de pieces est tel que si la piece est bonne elle est acceptee avec la probabilite de 0.96
Si la piece est mauvaise, elle est refusee avec la probabilite de 0.98

On choisit une piece au hasard et on la controle

1. Quelle est la probabilite qu'il y ait une erreur de controle ?
2. Quelle est la probabilite qu'une piece acceptee soit mauvaise ?

++Notation des evenements++ :
$B$ : "piece bonne"
$A$ : "piece acceptee"
$E$ : "erreur de controle"

++Donnees de l'exercice++ : 
$P(\overline{B}) = 5\%$
$P(A/B) = 96\%$
$P(\overline{A}/\overline{B}) = 98\%$

1. Quelle est la probabilite qu'il y ait une erreur de controle ?

> On cherche la probabilite de E

$E = (A \cap \overline{B}) \cup (\overline{A} \cap B)$
> $\cap$ = et
> $\cup$ = ou

$(A \cap \overline{B})$ et $(\overline{A} \cap B)$ evenements incompatibles, pas d'intersection

$\begin{align}P(E) &= P(A \cap \overline{B}) + P(\overline{A} \cap B) \\&= P(A/\overline{B})P(\overline{B}) + P(\overline{A}/B)P(B) \\ &= 0.02 \times 0.05 + 0.04 \times 0.95 \\ &= 0.039\end{align}$

$P(E) = 3.9\%$

2. Quelle est la probabilite qu'une piece acceptee soit mauvaise ?

> On cherche la probabilite de $P(\overline{B}/A)$

Formule de Bayes
$\begin{align}P(\overline{B}/A) = \frac{P(A/\overline{B})P(\overline{B})}{P(A)}\end{align}$

$A = (A \cap B) \cup (A \cap \overline{B})$
$P(A) = P(A \cap B) + P(A \cap \overline{B})$
$P(A) = P(A/B)P(B) + P(A/\overline{B})P(\overline{B})$
$P(A) = 0.96 \times 0.95 + 0.02 \times 0.05$

$\begin{align}P(\overline{B}/A) = \frac{0.02 \times 0.05}{0.96 \times 0.95 + 0.02 \times 0.05} = 0.0011\end{align}$

--------------
++Exercice 2++ : 

On dispose de 2 des equilibres A et B  
Le de A a 4 faces rouges et 2 blanches  
Le de B a 2 faces rouges et 4 blanches  
Les 2 des sont equilibres

On lance une piece de monnaie telle que la proba d'obtenir pile soit 1/3  
Si on obtient pile, on decide de jouer uniquement avec A  
Sinon, on joue uniquement avec B

1. Calculer la probabilite d'obtenir rouge au premier coup
2. On a obtenu rouge aux 2 premiers coups. Calculer la probabilite d'obtenir rouge au troisieme
3. On a obtenu rouge aux n premiers roups $(n \in \mathbb{N}^*)$. Determiner la probabilite d'avoir utilise A

++Donnees de l'exercice++
$A$ : "Obtenir pile"  
$B$ : "Obtenir face"  
$R$ : "Obtenir rouge"  

$P(B) = 2/3$  
$P(R/B) = 1/3$  
$P(A)=1/3$  
$P(R/A)=2/3$

Soit $R_k$ "On obtient rouge au k-ieme coup"

1. Calculer la probabilite d'obtenir rouge au premier coup

$R_1 = (R_1 \cap A) \cup (R_1 \cap B)$ (evenements incompatibles)

$P(R_1) = P(R_1/A)P(A) + P(R_1/B)P(B)$
$P(R_1) = 2/3 \times 1/3 + 1/3 \times 2/3$
$P(R_1) = 4/9$

2. On a obtenu rouge aux 2 premiers coups. Calculer la probabilite d'obtenir rouge au troisieme

> On cherche la probabilite de $P(R_3/(R_1 \cap R_2))$

$P(R_3/(R_1 \cap R_2)) = \frac{P(R1 \cap R_2 \cap R_3)}{P(R_1 \cap R_2)}$

$R_1 \cap R_2 = (R_1 \cap R_2 \cap A) \cup (R_1 \cap R_2 \cap B)$

$P(R_1 \cap R_2) = P((R_1 \cap R_2)/A)P(A) + P((R_1 \cap R_2)/B)P(B)$
$P(R_1 \cap R_2) = (2/3)^2(1/3) + (1/3)^2(2/3)$
$P(R_1 \cap R_2) = (4/27) + (2/27) = 2/9$

$P(R_1 \cap R_2 \cap R_3) = P((R_1 \cap R_2 \cap R_3)/A)P(A) + P((R_1 \cap R_2 \cap R_3)/B)P(B)$
$P(R_1 \cap R_2 \cap R_3) = (2/3)^2(1/3) + (1/3)^2(2/3) = (8/81) + (2/81) = 10/81$

$P(R_3 / (R_2 \cap R_1)) = 10/81 \times 9/2 = 5/9$

3. On a obtenu rouge aux $n$ premiers roups $(n \in \mathbb{N}^*)$. Determiner la probabilite d'avoir utilise $A$

> On cherche la probabilite $P(A/(R_1 \cap R_2 \cap ... \cap R_n))$

$\begin{align}P(A/(R_1 \cap R_2 \cap ... \cap R_n)) &= \frac{P((R_1 \cap ... \cap R_n) / A)P(A)}{P(R_1 \cap ... R_n)} 
\\ &= \frac{P(R/A)^n P(A)}{P(R_1...R_n/A)P(A) + P(R_1...R_n/A)P(B)} 
\\ &= \frac{(P(R/A))^nP(A)}{(P(R/A))^(A) + (P(R/B))^nP(B)} 
\\ &= \frac{(2/3)^n * (1/3)}{(2/3)^n * (1/3) + (1/3)^n * (2/3)}
\\ &= \frac{2^n}{2^n + 2} = \frac{2^{n-1}}{2^{n-1} + 1} \end{align}$

---
++Exercice 3++

Le nombre d'appels telephoniques a un standard suit une loi de Poisson de parametre $\lambda$
Supposons que pour tous les appels, il y ait une probabilite $p$ que le correspondant demande un poste $A$

1. Calculer la probabilite qu'il y ait k appels vers $A$ sachant qu'il y a eu $n$ appels au standard
2. Calculer $p(n,k) = P((X=n) \cap (Y=k))$
> Ou $X$ = nombre d'appels vers le standard et $Y$ = nombre d'appels vers le poste $A$

3. Determiner la loi de $Y$

++Question 1++

On cherche $P(Y=k/X=n)$

$P(Y=k/X=n) = \binom{n}{k}p^k(1-p)^{n-k}$ (loi Binomiale)
Donc $Y/X$ suit $B(n,p)$

++Question 2++

$\begin{align}p(n,k) &= P((X=n) \cap (Y=k))
\\ &= P(Y=k/X=n) \times P(X=n)
\\ &= \binom{n}{k}p^k(n-p)^{n-k} \times e^{-\lambda}\frac{\lambda^{n}}{n!}
\\ &= \frac{p^k(1-p)^{n-k}}{k!(n-k)!} e^{-\lambda} \lambda^n\end{align}$

++Question 3++

$\forall k \in \mathbb{R}$
$\begin{align}(Y=k) = \bigcup_{n \geq k}^{+\infty} ((Y=k) \cap (X=n))\end{align}$

$\begin{align}P(Y=k) &= \sum_{n \geq k}^{+\infty} P((Y=k) \cap (X=n))
\\ &= \sum^{+\infty}_{n \geq k} \frac{p^k(1-p)^{n-k}}{k!(n-k)!}  e^{-\lambda} \lambda^n
\\ &= e^{-\lambda} \frac{p^k}{k!} \times \sum^{+\infty}_{n \geq k} \frac{((1-p)\lambda^{n-k})}{(n-k)!}
\\ &= \frac{e^{-\lambda}p^k}{k!} \lambda^k e^{(1-p)\lambda}
\\ &= \frac{(\lambda p)^k}{k!} e^{\lambda p} = \mathcal{P}(\lambda p)\end{align}$

++Conclusion++

$Y$ suit la loi de Poisson $\mathcal{P}(\lambda p)$

++Exercice 4++

Une urne contient 9 boules blanches et 5 boules noires
On tire sans remise 3 boules 

Soit $X$ la variable aleatoire : nombre de boules blanches observees

1. Calculer $X$ et $E(X)$
2. $\forall i \in [[0;3]]$, on note $A_i$ l'evenement $X = i$. Calculer $P(A_i)$
3. On remet les boules noires dans l'urne et on en prend une nouvelle. Quelle est la probabilite d'obtenir une boule blanche ?

++Question 1++

On utilise la loi Hypergeometrique : Prelevement d'une portion de population sans remise

$X$ suit $H(N=9,\ n=3,\ p=4/9)$


$P(X=k) = \frac{\binom{4}{k}\binom{5}{3-k}}{\binom{9}{3}}$

$X(\Omega) = [[0;3]]$ (nombre de valeurs possibles de X)  
$E(X) = np = 3 \times 4/9 = 4/3$

++Question 2++

:::info
**Rappel**

$\binom{a}{b} = \frac{a!}{b!(a-b)!}$
:::
$P(X=i) = \frac{\binom{4}{i}\binom{5}{3-i}}{\binom{9}{3}}$

$P(X=0)= \frac{\binom{4}{0}\binom{5}{3}}{\binom{9}{3}} = 5/42$  
$P(X=1) = 10/21$  
$P(X=2) = 5/14$  
$P(X=3) = 1/21$

++Question 3++

$P(B) = P(B/X=0)P(X=0) + P(B/X=1)P(X=1) + P(B/X=2)P(X=2) + P(B/X=3)P(X=3)$
$B = \bigcup_{i=0}^{3} (B \cap A_i)$

$P(B) = \sum^{3}_{i=0}P(B/A_i)P(A_i) = \sum_{i=0}^{3} \frac{4-1}{9-1}P(A_i)$