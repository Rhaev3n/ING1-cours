[LOGI] Logique du premier ordre (1)
===

# Modes de definition

## C'est quoi definir ?

- Ecrire une phrase dans un dictionnaire
> Mot = mot1 mot2 mot3 ... motn
> 
**Definition linguistique** (ou definition de type dictionnaire)

## Mode de definition inductive

Un type $\mathcal{T}$ est defini par induction lorsqu'on donne : 
- **Atomes** : $a_1...a_n$ de type $\mathcal{T}$ (briques elementaires du type $\mathcal{T}$)
- **Constructeurs** : $f_1\ f_2...f_p$ avec un certain nombre d'arguments $r_1, r_2...r_n$, de sorte que $f_1(t_1...t_{r1})$ est de type $\mathcal{T}$
- **Condition d'arret**

++Exemple++ : $\mathcal{T}$ integer
- Atome : 
    - 0000 est un integer
    - $\square$ est un integer
- Operateur : $\nearrow$ a un argument ($*$ int alors $\nearrow *$ int)
- Condition d'arret : s'arreter (a un moment)

Condition d'arret = s'arreter : Condition $\omega$

### Mots

**Les mots (Induction)** sur l'alphabet $\Sigma$
- Atomes : 
    - Tout element $s$ de $\Sigma$
    - Le mot dit "vide"
- Operations : la concatenation (2 arguments)
- Condition d'arret : $\omega$

On note $\Sigma *$ le type obtenu

## Logique Propositionnelle

Par induction on cree un type "formule propositionnelle" ou encore type $\mathcal{F}$
On a donc : 
- $\mathcal{V}$ : symboles de variables propositionnelles
- A B ... Z : event munis d'indices ($X_{100}$, $Z_{172}$ etc)
- $\mathcal{C}$ : connecteurs logiques (nb args) 
    - $\wedge$(2) $\lor$(2) $\Rightarrow$(2) $\iff$(2) $\lnot$(1) $\top$(0) $\bot$(0)

$F_0$ est construit : 
- Atomes $\top$ $\bot$, tout element de $mathcal{V}$
- Operateurs : Si $\varphi$ et $\psi$ sont de type $F_0$ alors $\varphi \cap \psi$; $\ \ \varphi \cup \psi$; $\ \ \varphi \Rightarrow \psi$; $\ \ \varphi \iff \psi$; $\ \ \lnot \varphi$ en sont aussi
- Condition d'arret $\omega$

++Exemple++ : 
- A
- $E \Rightarrow X_{42}$
- $Z_{172} \wedge \lnot X_{172}$
- type $F_0$

:::danger
$(A \Rightarrow B) \wedge C$
$A \Rightarrow (B \wedge C)$
:::

## Procedure de verification de constructions de type $F_0$

On observe que 
- $FAUX \Rightarrow VRAI$ n'est pas de type $F_0$ (symboles pas definis dans mon alphabet)
- $\wedge \wedge \Rightarrow AX$ n'est pas de type $F_0$ meme en polonais ($\wedge$ attend 2 arguments)

On peut donc discriminer dans $\Sigma *$ avec $\Sigma = \mathcal{V} \cup \mathcal{C}$

> Dans $\Sigma *$ > types $F_0$ et non types $F_0$

On met en entree des mots de  $\Sigma *$ et en sortie on a $\begin{cases}accept\ (si\ dans\ F_0) \\ reject\ sinon\end{cases}$

**Algo**

$\varphi = s_1 s_2 ... s_n (s_i \in \Sigma)$

**Valuation** : $S \to V(s) := arite - 1$
> ex : V($\Rightarrow) = 2 - 1 = 1$

Arite : nombre d'elements qui s'accrochent a un symbole

**Process**
| $\varphi$        | $s_1 s_2 ... s_N$ |
| ---------------- | ----------------- |
| V                | $v_1 v_2 ... v_N$ |
| $\Sigma_{cumul}$ |                   |

Stop at : $\Sigma_{cumul} < 0$ (a un moment) ou (lecture du dernier symbole)

**==Theoreme==**

En choisissant "Accept", ssi le process s'arrete en validant les 2 conditions, on obtient une **procedure de verification de $F_0$**

++Exemple++ : 
|          | $\Rightarrow \wedge \lor A \lnot B \wedge C H$ |
| -------- | ---------------------------------------------- |
| V        | 1 1 1 -1 0 -1 1 -1 -1                          |
| $\Sigma$ | 1 2 3 2 2 1 2 1 0                              |

$V \neq -1$ donc pas de type $F_0$