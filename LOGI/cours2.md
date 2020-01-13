[LOGI] Logique du premier ordre (2)
===

## Semantique (le debut)

### **Constructive Inductive**
On definit : $\nu$ (assignation de variables)

$\nu: \mathcal{V} \to \{vrai;\ faux\}$
$symbole\ \to\ \nu(symbole)$

> Porte sur les atomes mais pas $\top$ et $\bot$

### **Gestion de connection** 
On definit $||\ ||_{\nu}$ semantique sur $F_0$ pour : 
- ++Atomes++: si $* \in \mathcal{V}$ alors $||*||_{\nu} = \nu(*)$
    - $||\top||_{\nu} = vrai$ et $||\bot||_{\nu} = faux$

- ++Constructeurs++ : Donnons nous $\phi$ et $\psi$ dans $F_0$
    - $||\phi \land \psi||_{\nu}= vrai$ ssi $||\phi||_{\nu} = vrai$ et $||\psi||_{\nu} = vrai$
    - $h(a *_E b) = h(a) *_{\nu} h(b)$
    - (neg): $||\lnot \phi||_{\nu} = vrai$ ssi $||\phi||_{\nu} = faux$
    - **Propriete de morphisme** : idem avec tous les autres correcteurs
- ++Arret++ : $\omega$

### Tarski moderne

Table de verite ET
|$\land$|Vrai|Faux|
|:--:|:--:|:--:|
|Vrai|Vrai|Faux|
|Faux|Faux|Faux|

Table de verite IMPLICATION

|$\Rightarrow$|Vrai|Faux|
|:--:|:--:|:--:|
|Vrai|Vrai|Faux|
|Faux|Vrai|Vrai|

Table de verite EQUIVALENCE

|$\iff$|Vrai|Faux|
|:--:|:--:|:--:|
|Vrai|Vrai|Faux|
|Faux|Faux|Vrai|

$(p \Rightarrow q) \Rightarrow p$
|p|q|$p \Rightarrow q$|$[...] \Rightarrow p$
|:--:|:--:|:--:|:--:|
|0|0|1|0|
|0|1|1|0|
|1|0|0|1|
|1|1|1|1|
En polonais : $\Rightarrow \Rightarrow pq\ p$

$p \Rightarrow (q \Rightarrow p)$
|p|q|$p \Rightarrow q$|$p \Rightarrow [...]$|
|:--:|:--:|:--:|:--:|
|0|0|1|1|
|0|1|0|1|
|1|0|1|1|
|1|1|1|1|
En polonais : $\Rightarrow p \Rightarrow qp$

### Formule de Pierce

La formule $P \Rightarrow (Q \Rightarrow P)$ est appelee **formule de Pierce** et ce quels que soient les choix de P; Q

On parle de "Loi de Pierce" pour designer le fait que : 
$\forall \nu: \mathcal{V} \to \{vrai; faux\}$ on a $||p \Rightarrow (q \Rightarrow p)||_{\nu} = vrai$

==**Definition (Tautologie)**==

$\forall \nu: \mathcal{V} \to \{...\}$ on a  $||\phi||_{\nu} = vrai$

### Antilogie

==**Definition analogue (Antilogie)**==

$||\phi||_{\nu}$

- $A \Rightarrow \lnot A$ : ni l'un ni l'autre
- $\lnot (A \lor B) \iff (\lnot A \lor \lnot B)$ : idem
- $\lnot \lnot A \Rightarrow A$ : tautologie
- $(\lnot A \lor \lnot B) \Rightarrow \lnot (A \land B)$

**Definition**
On dit que $\phi$ et $\psi$ sont semantiquement equivalentes lorsque : 
$|| \phi \iff \psi||_{\nu} = vrai$; quel que soit $\nu$

Autrement dit : $\phi \iff \psi$ est une tautologie

++Exemples remarquables++
|||
|:--:|:--:|
|$\lnot (A \lor B)$|$\lnot A \land \lnot B$|
|$\lnot (A \land B)$|$\lnot A \lor \lnot B$|
|$\lnot \lnot A$|$A$|
|$A \Rightarrow B$|$\lnot A \lor B$|

### Construction syntaxique

> Corps de texte (Femonstrations \ Preuves)

Introdution aux **sequents** (Ventzel)

++Notation++ : $\phi \vdash \psi$ sequent ou $\vdash$ : "demontre" ou "these"
> Ici $\phi$ est le premice et $phi$ la conclusion

- ++Atome++ : $\phi \vdash \psi$ $\ \ \forall \phi \in F_0$
- ++Constructeurs++ : 
    - Forme d'ecriture: $\frac{n\ sequents}{sequent\ final}[nom\  regle]$

### Regles

- $\begin{align}\frac{}{\phi \vdash \phi}\end{align}$ Axiome

- $\begin{align}\frac{\phi \vdash h\ \ \ \ \ \ \psi \vdash g}{\phi \land \psi \vdash h \land g}\end{align}$ [$\land$-intro]

- $\begin{align}\frac{\phi \vdash h\ \ \ \ \ \ \phi \vdash g}{\phi \vdash h \land g}\end{align}$ [i-intro]

- $\begin{align}\frac{\phi \vdash \psi \ \ \ \ \ \psi \vdash h}{\phi \vdash h}\end{align}$ [cut]

- $\begin{align}\frac{\phi \vdash A \Rightarrow B\ \ \ \ \ \phi \vdash A}{\phi \vdash B}\end{align}$ [Modus Podens]

- $\begin{align}\frac{\phi \vdash A\ \ \ \ \ \phi \vdash B \Rightarrow A}{\phi \vdash A \iff B}\end{align}$ [$\iff$-intro]

### Regles specifiques LK

==**Propriete**== : Ces 3 regles sont equivalentes

- $\begin{align}\frac{\phi_{\land} \lnot h \vdash \bot}{\phi \vdash h}\end{align}$ [par l'absurdre]

- $\begin{align}\frac{\phi \vdash h}{\top \vdash \phi_{\lor} \lnot \phi}\end{align}$ [tier Exclu]
> Rare cas d'utilisation de $\top$

- $\begin{align}\frac{\phi \vdash \lnot \lnot \psi}{\phi \vdash \psi}\end{align}$ [$\lnot \lnot$-elimination]

LI (Logique intuitioniste) Si on s'en passe

### Autres regles 

- $\begin{align}\frac{\phi \vdash h}{\phi \vdash h \lor g}\end{align}$ [affaiblissement]

- $\begin{align}\frac{\phi \vdash h\ \ \ \ \ \ \psi \vdash h}{\phi \lor \psi \vdash h}\end{align}$ [$\lor$-intro]

**Vocabulaire**

- On appelle **demontration** toute suite de sequents inductivement construite par ce processus.
- On appelle **preuve** toute demonstration n'utilisant que les regles de LI

> $\lnot \lnot A \vdash A$ est demontrable et non prouvable. En revanche $A \vdash \lnot \lnot A$ est prouvable
> 
- On appelle **theoreme** toute sequence finale d'une demonstration
