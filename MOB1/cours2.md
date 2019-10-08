[MOB1]  Modelisation Objets (2)
===

## L'approche orientee objet

### Terminologie
> Oriente objet ne veut plus rien dire aujourd'hui

Alan Key : inventeur de l'oriente objet (ainsi que du terme associe), alors que son idee aurait ete mieux resume par "Message-oriented programming"

### Les objets du monde reel

 - Un ==etat== (statique)
 - Un ==comportemant== (dynamique)
---
    Personne
        - Attribut statique : nom / prenom / age
        - Comportements dynamiques : mange / travaille / se deplace
    
---

    Avion : 
        - Attribut statique : marque / couleur
        - Comportement dynamique : prend passagers / se deplace

Chqaue objet a un attribut, mais pas le meme. Tout salarie a un employeur mais toute personne n'est pas salariee, un avion et une personne se deplacent, mais differemment 
-> La POO exprime ce genre de relations

### Historique

**SmallTalk** (langage de programmation de 1971, public en 1980)
- Alan Key et Dan Ingalls
- Principale idee : paradigme uniquement centre sur les envois de messages
- Premier langage dit "oriente-objet"

**Simula** (1962, surtout 1967)
- Ole-Johan Dahl et Kristen Nygaard
- Contenant deja tous les concepts techniques dont SmallTalk s'est inspire (notion de classe)

## Oriente objet aujourd'hui

> Java, C++, C#, Python et Lisp avec des couches orientees objet
- Aucune reelle definition
    - Nombreux langages aux visions tres differentes
    - Ensemble flou de concepts, ni exclusif ni exhaustif
    - Concepts mal definis / articules
    ---
- Effort de standardidation
    - OMG (Object Managment Group)
    - UML (Unified Modelling Language)

### Origine

- But initial : representer une famille d'objets similaires dotees de certaines proprietes connues 
- Mention des "Union classes"

```uml=
---
**Human**
---
name: string
size: float
birth_year: unsigned
---
---
```

```cpp
class C++
{
    std::string name_;
    float size_;
    unsigned birth_year_;
};
```

```java=
class Human
{
    String name;
    float size;
    int birthYear;
}
```

### Extension du modele de Hoare

- Les proprietes peuvent inclure du comportement
- "We needed subclasses of processes with own special actions and local data stacks, not only pure data records"

```uml=
---
**Human**
---
name: string
size: float
birth_year: unsigned
---
age() : unsigned
hello() : void
---
```

```uml=
---
**Nom**
---
Champs / Attributs / Slots
---
Methodes / Fonctions membres
---
```

> Limitation UML : Distinctions entre methodes et Attributs (suit l'approche fde Von Neumann)

```java=
class Human
{
    String name;
    float size;
    int birthYear;
    int age () { ... }
    void hello () { ... }
}
```

### Classe

 - Une classe est statique comme tout autre type de donnee **fixe et connu a la compilation**
 - Classe = nouveau type de donnee (limitation de l'approche objet classique)
 - API d'introspection dans certains langages (ex: Java)
 - Pas d'intercession (dans les langages statiques)

**Introspection** : Capacite d'un programme d'examiner son propre etat
**Intercession** : Capacite de se modifier soi-meme
