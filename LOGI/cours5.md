[LOGI] Logique du premier ordre (last)
===

### Interpolation du ??? relationel de premier ordre

$\mathcal{L} = \begin{cases}c_1 ... c_p\ symboles\ constantes \\ f_1 ... f_k\ symboles\ de\ fonctions\ [nb\ args\ a_1 ... a_k] \\ R_1 ... R_n\ symboles\ de\ relations\ [arite\ r_1 ... r_n]\end{cases}$

:::danger
Contexte syntaxique $\neq$ contexte semantique

Contexte syntaxique : theorie - axiomes
Contexte semantique : Collection d'individus, domaine non vide
:::

On note M la collection et on donne une interpolation de $\mathcal{L}$ symbole a symbole

$Symboles\ \to\ individus$
$\mathcal{C}_i\ \to\ c_i\ (objet\ de\ M)$
$f_j\ \to\ (\mathcal{f}_j : M^{a_j} \to M)$
> NB : Les interpolations des symboles de fonctions sont de fait internes
 
$\mathcal{R}_p\ \to\ R_p\ relation\ d'arite\ r_p (si\ M\ ensemble, alors\ R_p \subset M^{r_p}$

Notons $\mathcal{M} = <M; <C_i>_{i \leq p}; <j_j>_{j \leq k}; <R_p>_{p \leq n}>$
On la nommera $\mathscr{L}$-realisation

:::info
Si S est un symbole de $\mathscr{L}$ on notera $\overline{S}^{\mathcal{M}}$ son interpretation dans $\mathcal{M}$
:::

++Exemple 1++ : 

Reprenons $\mathscr{L}$ de partie syntaxique : 
A (cte), B (fct, 2), C (rela, 1, predicat), D (rela, 2)

Donnons-en une $\mathscr{L}$-realisation / interpretation

Posons M = R et decrivons : 
$\overline{A}^R = 12$
$\overline{B}^R : (x;y) \to x + y$
$\overline{C}^R : vrai\ ssi\ l'est\ par ???$
$(\overline{C}^R = \mathbb{R}_+)$
$\overline{D}^R = =_\mathbb{R} \neq =_\mathbb{N}$

++Exemple 2++ : 

Prenons $\mathcal{L}_{ARI} : 0, 1, +, \times, \nearrow, \equiv$
Prenons E un ensemble infini denombrable et $M = \mathcal{P}(E)$ plus denombrable

On a $0\ \to\ \{e_1, e_2\}$
$\ \ \ \ \ \ \ \ \ 1 \to \varnothing$
$\ \ \ \ \ \ \ \ + \to ((A, B) \to A \cap B_C)$
$\ \ \ \ \ \ \ \ \times \to ((A, B) \to A \cup B)$
$\ \ \ \ \ \ \ \nearrow \to (A \to A_C)$
$\ \ \ \ \ \ \ \ \equiv \to C_E$

### Definition

Soit $\mathcal{T}$ une theorie du langage $\mathcal{L}$
Soit $\mathcal{M}$ une $\mathscr{L}$-realisqtion
On dira que "$\mathcal{M}$ est un modele de $\mathcal{T}$" lorsque si $\sigma$ est l'un des axiomes de $\mathcal{T}$ alors l'interpretation de $\sigma$ induite par $\mathcal{M}$ est "vraie" (pour tout $\sigma$ de $\mathcal{T}$)

++Exemple++ : 

Reprenons $\mathscr{L}_G$ et $\mathcal{T}_G$ : theorie des groupes
Posons $\mathcal{G} = <\mathbb{Z/_{24\mathbb{Z}}}; <0_{\mathbb{Z/_{24\mathbb{Z}}}}>, <+_{\mathbb{Z/_{24\mathbb{Z}}}}, \phi>, <=_{\mathbb{Z/_{24\mathbb{Z}}}}>>$
Ou $\phi: k \to \begin{cases}24 - k\ si\ k \neq 0_{\mathbb{Z/_{24\mathbb{Z}}}} \\ 0_{\mathbb{Z/_{24\mathbb{Z}}}}\ sinon\end{cases}$

Ainsi $\mathcal{G}$ est un modele de $\mathcal{T}_G$

Posons $\mathcal{N} = <\mathbb{N}, <0_{\mathbb{N}}>, <+_{\mathbb{N}}, k\to -k>; <=_{\mathbb{N}}>>$

$\mathcal{N}$ n'est pas une $\mathscr{L}_G$-realisation, en effet $k\to -k$ n'est pas un type $\mathbb{N} \to \mathbb{N}$ (en effet 2 $\neq$ -2)

### Indiction 

++Induisons explicitement l'interpretation++

Symboles $\to$ termes $\to$ formules $\to$ textes $\to$ contextes

$\mathscr{L}-realisation$

(2) : Termes 