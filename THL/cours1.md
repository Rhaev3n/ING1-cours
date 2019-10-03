[THL] Theorie des langages (1)
===

# Compilateur 

### 2 phases : 
- Lecture d'un programme (THLR)
- Traduction et ecriture en langage machine

### Etapes du compilateur
1. **Analyseur lexical** : coupe le texte en token
3. **Verification syntaxique** : verifie si la sequence est correcte
4. **Analyse semantique** : analyse la sequence dans son contexte

# THLR

**Langage** : ensemble de symboles (non ordonne)
**∅** (langage vide) ≠ **{ε}** (langage contenant le mot vide)

**Mot** : suite finie de symboles (eventuellement vide)

**Alphabet Σ** : caracterise par son **cardinal** (Nombre de symboles dans l'alphabet)
**Σ*** : ensemble de tous les mots possibles generes sur l'alphabet Σ

### Operations sur des mots
∀u ∈ Σ*

#### Concatenation (Loi de composition interne)
u = abc
v = bcd
u.v = abcbcd
|u| + |v| = |uv|
element neutre : ε

### Operations sur des langages
∀L ∈ Σ*

- Union
- Intersection
- Complementaire

#### Concatenation
∀L1 ∈ Σ*, ∀L2 ∈ Σ*

**L1.L2** = prefixes dans L1, suffixes dans L2

> Exemple
> L1 = {ab, bc}, L2 = {bc, cd}
> L1.L2 = {abbc, abcd, bcbc, bccd}


--- 
∀n ∈ N
∀u ∈ Σ*

$$
u ^ n = \begin{cases}
        {ε \\
        uuu...u  (n fois)}
        \end{cases}
$$

---

$$
L^* = \bigcup^{\infty} _{{n\geq 0}}X^{n} = L^0 ULUL^2UL^3 \\
L^+ = LL^* = \bigcup _{{n>0}}L^{n}
$$

---

#### Prefixe
pref(abcaab) = {ε, a, ab, abc, abca, abcaa, abcaab}

## Langage rationnel

Un **langage rationnel** est defini par les elements suivants
- ∅
- {ε}
- ∀a ∈ Σ{a}

Et les operateurs suivants 
- U
- ∗
- ∙

## Expressions rationnelles

∙ devient (vide)
U devient |
∗ devient ∗

> Exemple
> L'expression ({+} U {-} U {ε}).({0} U {1} U {2} U ... U {9}∗)
> devient (+ | - | ε)(0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9)
