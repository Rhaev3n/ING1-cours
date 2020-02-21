[THEG] Theorie des graphes (1)
===

==**Problematiques sur les graphes**==  
- **Coloration de graphe**
- **Plus court chemin**
    - (1-1, 1-n, n-n, oriente, avec poids)
- **Le voyageur de commerce (TSP)**
    - Visiter tous les sommets du graphe
- **Tri topologique**
    - (Makefile, tableur)
- **Probleme des flots max**
- **Connexite**
- **Arbres couvrants**
    - Arbre : graphe acyclique connexe
- **Chemin / cycle eulerien**
    - Visite toutes les aretes 1 fois
- **Cycle Hamiltonien**
    - Visite tous les sommets 1 fois 
- **Decider si un graphe est planaire**
    - Graphe planaire : Peut etre represente dans le plan sans croisement d'aretes
- **Isomorphisme de graphe**
    - Peut on permuter les sommets d'un graphe 1 pour obtenir le graphe 2 ?
- **Epaisseur de graphe**
- **Couplage maximum**
- **Clique maximale**
    - Clique : Sous-graphe complet
- **Couverture des sommets par les aretes**
- **Couverture des aretes par les sommets**
- **Denombrer les arbres couvrants**
- **Theoreme de Kirchhoff**
    - Le nombre d'arbres couvrants d'un graphe G est egal a la valeur absolue de n'importe quel co-facteur de la matrice laplacienne de G
    - $L_G = D_G - A_G$ (laplacienne de G : matrice des degres - matrice d'adjacence de G)
    - ![](https://i.imgur.com/AIRpFP2.png)

### Complexites

**P** : Le probleme peut etre resolu par une machine de Turing *deterministe* en un *temps polynomial*

**NP** : Le probleme peut etre resolu par une machine de Turing *non-deterministe* en un *temps polynomial*

![](https://i.imgur.com/BVaxrEP.png)

|Algo|Complexite|
|:--:|:--:|
|Coloration de graphe|NP-Complet|
|Plus court chemin|P|
|Vendeur de commerce|NP-Hard|
|Tri topologique|Lineaire|
|Probleme de flots max|P|
|Connexite|P|
|Arbres couvrants|P|
|Chemin / cycle eulerien|Lineaire|
|Cycle Hamiltonien|NP-Complet|
|Graphe planaire|Lineaire|
|Isomorphisme de graphe|NP|
|Epaisseur de graphe|NP-Hard|
|Couplage maximum|Lineaire|
|Clique maximale|NP-Complet|
|Couverture des sommets par les aretes|Lineaire|
|Couverture des aretes par les sommets|NP-Complet|
|Denombrer les arbres couvrants|P|

### Definitions

**Graphe oriente**  
![](https://i.imgur.com/Dag0OoB.png)

**Graphe non-oriente**  
![](https://i.imgur.com/HLAMogn.png)

**Graphe pondere**  
Il y a des poids sur les aretes ou les arcs

**Connexe**  
Il existe un chemin entre toute paire de sommet

**Arbre**  
Graphe acyclique connexe

**DAG**  
Directed acyclic graph

> DAG $\neq$ arbre

**Degre d'un sommet**  
Nombre d'aretes incidentes  
$\sum_{x \in V}deg(x) = 2x$ nombre d'aretes

> Sur graphe oriente : On a degre **entrant** et **sortant**

```
for x in V:
    for y in succ(x):
        // execute 2x nombre d'aretes
```

**Graphe simple**  
Graphe sans aretes en double et sans boucles

**Graphe multiple**  
On autorise aretes doubles et boucles

## Plan

> 6 seances

1. Culture et vocabulaire
2. Cycles euleriens et DFS
3. BFS, Rubik's cube, Plus court chemin
4. BFS, Rubik's cube, Plus court chemin
5. Couplages, connexite
6. Couplages, connexite