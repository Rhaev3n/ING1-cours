[THL] Theorie des langages (2)
===

## Automates

$\varnothing \to \varnothing \Rightarrow\ \  \to o\ \ \ o\to$
$\{\varepsilon\} = \varepsilon \Rightarrow\ \ o\overset{\varepsilon}{\to} o\to$
$\forall a \in \sum \{a\} \to a \Rightarrow$
```graphviz
digraph hierarchy {
    rankdir=LR;

    ""->{":)"} [label="a"]
    ""->{":("} [label="!a"]
}
```
----------------
Concatenation . : 
```graphviz
digraph hierarchy {
    rankdir=LR;
    "L1"->{"L2"} [label=":)"]
    "L1"->{""} [label=":("]
    "L2"->{":("} [label=""]
    "L2"->{":)"} [label=""]

}
```

**Machine a etats** : $(Σ, Q, ICQ, FCQ, S)$
> Σ : Langage
> Q : Etats
> ICQ : Etats d'entree
> FCQ : Etats finaux
> S : Transitions

Automate de $L_1 \cup L_2$
```graphviz
digraph hierarchy {
    rankdir=LR;
    node [shape = point ]; qi

    node [shape = circle];
    qi->""
    ""->"L1" [label="ε"]
    ""->"L2" [label="ε"]
    "L1"->" " [label="ε"]
    "L2"->" " [label="ε"]
}
```

---
### Automate deterministe
> Objectif : rendre cet automate deterministe

$a^*n + na^*$
```graphviz
digraph hierarchy {
    rankdir=LR;
    node [shape = point ]; qi
    node [shape = point ]; qj


    node [shape = circle];
    qi->"0"
    "0"->"1" [label="ε"]
    "0"->"7" [label="ε"]
    "0"->"6" [color=red] [label="n"]
    "0"->"8" [color=red] [label="n"]
    "0"->"3" [color=red] [label="a"]
    "7"->"8" [label="n"]
    "8"->"9" [label="ε"]
    "9"->"10" [label="ε"]
    "10"->"11" [label="a"]
    "11"->"10" [label="ε"]
    "11"->"12" [label="ε"]
    "12"->"13" [label="ε"]
    "9"->12 [label="ε"]
    "1"->"2" [label="ε"]
    "1"->"4" [label="ε"]
    "2"->"3" [label="a"]
    "3"->"2" [label="ε"]
    "3"->"4" [label="ε"]
    "4"->"5" [label=""]
    "5"->"6" [label="ε"]
    "6"->"13" [label="ε"]
    13->qj
}
```

**Epsilon fermeture** : tous les etats auquels om peut acceder sans consommer de charactere

> On liste les etats et leurs transitions epsilon

|εf()|1|2|3|
|:--:|:--:|:---:|:---:|
|0|0, <span style=color:red;>1</span>, 7|0, <span style=color:red;>1, 2, 4</span>, 7|0, 1, 2, 4, 7|
|1|1, 2, <span style=color:green;>4</span>|1, 2, <span style=color:green;>4, 5</span>|1, 2, 4, 5|
|2|2|2|2|
|3|3, 2, <span style=color:green;>4</span>|3, 2, <span style=color:green;>4, 5</span>|3, 2, 4, 5|
|4|4, 5|4, 5|
|5|5|5|5
|6|6, 13|6, 13|6, 13|
|7|7|7|7|
|8|8, <span style=color:blue;>9</span>|8, <span style=color:blue;>9, 10, 12</span>|8, 9, 10, 12, 13|
|9|9, 10, 12|9, 10, <span style=color:magenta;>12, 13</span>|9, 10, 12, 13|
|10|10|10|10|
|11|11, 10, <span style=color:magenta;>12</span>|11, 10, <span style=color:magenta;>12, 13</span>|12, 13|
|12|12, 13|12, 13|12, 13|
|13|13|13|13|

++Resultat++ :
```graphviz
digraph hierarchy {
    rankdir=LR;
    node [shape = point ]; qi
    node [shape = point ]; qj
    node [shape = point ]; qk
    node [shape = point ]; qq
    
    node [shape = circle];
    qi->"0"
    "0"->"3" [label="a"]
    "0"->"6" [label="n"]
    "0"->"8" [label="n"]
    "3"->"3" [label="a"]
    "3"->"6" [label="a"]
    6->qk
    8->11 [label="a"]
    8->qj
    11->11 [label="a"]
    11->qq
}
```

Un etat est dit **utile** si il est a la fois accessible et co-accessible
**Emonder** un automate : Supprimer les etats non-accessibles ou non co-accessibles
- Etat **accessible** : Il existe un mot faisant passer l'automate de l'etat initial a cet etat (on peut acceder a cet etat depuis l'entree)
- Etat **co-accessible** : Il existe un mot faisant passer l'automate de cet etat a un etat final
