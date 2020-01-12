[PROBA] Probabilites discretes (2)
===

### Applications


++**Exercice 1**++ : 

Une urne contient 9 boules numerotees de 1 a 9. On tire 2 boules.
Determiner la probabilite d'obtenir 2 boules portant des numeros de meme parite dans les cas suivants : 
1. On tire 2 boules simultanemment
2. On tire une boule, on ne la remet pas et on tire la deuxieme 
3. On tire une boule, on la remet avant de tirer la deuxieme boule

++Question 1++

:::danger
**Rappel**

$\begin{align} Card \binom{n}{p} = \frac{n!}{n!(n-p)!} \end{align}$
:::

Univers : $\Omega = \{$ Combinaisons de 2 boules prises dans $U\}$ = l'ensemble des arrangements
$Card\ \Omega = C^2_9 = \binom{9}{2} = \frac{9!}{2!7!} = \frac{8 \times 9}{2} = \frac{72}{2} = 36$

Soit $A$: "Les 2 nombres obtenus sont de meme parite"


Il y a $\binom{4}{2}$ facons de choisir 2 boules pairse et $\binom{5}{2}$ facons de choisir 2 boules impaires

$Card\ A = \binom{4}{2} + \binom{5}{2}$

$P(A) = \frac{\binom{4}{2} + \binom{5}{2}}{36} = \frac{16}{36} = \frac{4}{9}$

++Question 2 (tirage sans remise)++

:::danger
**Rappel**

$\begin{align} A^p_n = \frac{n!}{(n-p)!} \end{align}$
:::

Soit $B$ : "Les 2 boules sont de meme parite"

$\Omega = \{$ 2_listes d'elements $\neq$ pris dans $U \}$
$Card\ \Omega = A^2_9 = \frac{9!}{(9-2)!} = \frac{9!}{7!} = 8 \times 9 = 72$

On note $B_1$ = boule paire et $B_2$ = boule impaire

$Card\ B = Card\ B_1 + Card\ B_2 = \frac{4!}{2!} + \frac{5!}{3!} = 12 +20 = 32$

D'ou $P(B) = \frac{Card\ B}{Card\ \Omega} = \frac{32}{72} = \frac{4}{9}$

> Equivalent d'effectuer des tirages simultannes et des tirages decales mais sans remise

++Question 3 (tirage avec remise)++

$\Omega = \{$ 2_listes pris dans $U \}$

$Card\ \Omega = 9^2 = 81$

$Card\ A = Card\ A_1 \cup Card\ A_2$ avec $Card\ A_1 = 4^2$ et $Card A_2 = 5^2$

D'ou $Card\ A = 4^2 + 5^2 = 41$
Donc $P(A) = \frac{41}{81}$

++**Exemple 2**++ : 

On considere une urne contenant 5 boules blanches, 4 boules noires et 3 boules bleues

1. On tire simultanement 3 boules dans l'urne $U$
    - Quelle est la probabilite d'obtenir 3 boules de la meme couleur ? 
    - Quelle est la probabilite d'obtenir 1 boule de chaque couleur ? 
2. On remet la boule dans l'urne en la remettant apres chaque tirage
    - Quelle est la probabilite d'obtenir 3 boules de la meme couleur ? 
    - Quelle est la probabilite d'obtenir 1 boule de chaque couleur ? 
3. On tire 3 boules successivement sans remise
    - Quelle est la probabilite d'obtenir 3 boules de la meme couleur ? 
    - Quelle est la probabilite d'obtenir 1 boule de chaque couleur ? 
    - Quelle est la probabilite que la premiere boule blanche tiree le soit au troisieme tirage? 

++Question 1++ : 


$\Omega = \{$ Combinaisons (parties) a 3 elements de $U \}$

$N = 12$
$U = \{boules\}$

$Card \Omega = \binom{12}{3} = \frac{12!}{3!9!} = \frac{10*11*12}{6} = 220$

++1.a++ :

$A$ : "On tire 3 boules de la meme couleur"

$Card\ A = Card\ A_{blanche} \cup Card\ A_{bleue} \cup Card\ A_{noire}$
$Card\ A_{blanche} = \binom{5}{3}$
$Card\ A_{noire} = \binom{4}{3}$
$Card\ A_{bleue} = \binom{3}{3}$

$Card\ A = \frac{5!}{3!2!} + \frac{4!}{3!1!} + \frac{3!}{3!0!} = 10 + 4 + 1 = 15$
Donc $P(A) = \frac{15}{220} = \frac{3}{44}$

++1.b++ :

$B$ : "Une boule de chaque couleur"

$B = B_{blanche} \cup B_{bleue} \cup B_{noire}$

$Card\ B_{blanche} = \binom{5}{1}$
$Card\ B_{noire} = \binom{4}{1}$
$Card\ B_{bleue} = \binom{3}{1}$

$P(B) = \frac{5 * 4 * 2}{220} = \frac{60}{220} = \frac{3}{11}$

++Question 2 (tirage avec remise)++

$\Omega = \{$ 3_listes d'elements de $U \}$
$Card\ \Omega = 12^3 = 1728$

++2.a++ :

$A$ : "3 boules de meme couleur"
$A_{blanche} = 5^3$, $A_{noire} = 4^3$, $A_{bleue} = 3^3$
$Card\ A = 5^3 + 4^3 + 3^3 = 125 + 64 + 27 = 216$

$P(A) = \frac{216}{1728} = \frac{1}{8}$

++2.b++ : 

$B$ : "1 boule de chaque couleur"

$Card\ B = 3! \times (5 * 4 * 3)$
$Card\ B = 6 \times 60$
$Card\ B = 360$

$P(B) = \frac{360}{12^3} = \frac{30}{12^3} = \frac{5}{24}$

++Question 3 (tirage sans remise)++ : 

$Card\ \Omega = A_{12}^3 = \frac{12!}{(12 - 3)!} = 10 \times 11 \times 12 = 1320$

++3.a++ : 

$A$ : "On tire 3 boules identiques"
$Card\ A = A_5^3 + A_4^3 + A_3^3 = \frac{5!}{2!} + \frac{4!}{1!} + \frac{3!}{0!} = 60 + 24 + 6 = 90$

$P(A) = \frac{3!90}{1320} = \frac{3}{44}$

++3.b++ : 

$A$ : "On tire 3 boules differentes"

$Card\ A = 3!A_5^1 \times A_1^4 \times A_3^1 = 3!\frac{5!}{4!} \times \frac{4!}{3!} \times \frac{3!}{2!} = 3!60$

$P(A) = \frac{360}{1320} = \frac{3}{11}$

++3.c++ :  

$A$ : "La 3eme boule tiree est blanche"

$Card\ A = A_7^1 \times A_6^1 \times A^1_5 = 7 \times 6 \times 5 = 210$
$P(A) = \frac{210}{1320} = \frac{7}{44}$

++**Exercice 3**++ : 

Un placard contient 10 chaussures toutes differentes
On prend 4 chaussures au hasard

1. Probabilite de tirer 2 paires completes
2. Probabilite de tirer au moins 1 paire
3. Probabilite de tirer une seule paire

$\Omega = \binom{20}{4} = \frac{20!}{4!6!} = \frac{17*18*19*2}{4!}$

A "2 paires completes"

$P(A) = \frac{\binom{10}{2}}{\binom{20}{4}} = \frac{3}{323} = 9009$

