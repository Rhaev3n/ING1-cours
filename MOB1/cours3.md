[MOB1] Modelisation Objet (3)
===

> [// slides cours](https://www.lrde.epita.fr/~didier/lectures/aop/aop_01_classes_and_objects.pdf)

## Instanciation

- Processus de creation d'un objet a partir d'une classe
- Une classe permet d'instancier plusieurs objets similaires
- Un objet n'est l'instance que d'une seule classe

![](https://i.imgur.com/ZF99kCG.png)

> Relation de dependance (en pointilles)
> Nom d'objet obligatoirement souligne

## Cycle de vie d'un objet

- Dynamique (comme toute autre valeur), cree, utilise puis detruit pendant l'execution
- Construction et Destruction
> Pas specifique a l'oriente objet, tout type est concerne

## Construction

- Vision atomique de la phase de creation d'un objet
- Assure sa coherence interne
- **Constructeur** : Procedure speciale (sans type de retour)
    - Fourni par default (mais modifiable)
    - Nom predefini
    - Allocation / initialisation

> [[foo alloc] init arg1: val1]; (Objective-C) Certains langages contiennent encore une separation explicite entre allocation et initialisation


- ++Constructeur de la classe Human en UML++
```uml
Human
-------
name : string
size : float
birth_year : unsigned 
-------
«create»
Human (name : string, size : float, birth_year : unsigned)
```

---
- ++Constructeur de la classe Human en C\+\+++
```cpp=
class Human
{
    std::string name_;
    float size_;
    unsigned birth_year_;
    Human (const std::string& name, float size, unsigned birth_year);
};Human::Human (const std::string& name, float size, unsigned birth_year)
: name_ (name), size_ (size), birth_year_ (birth_year)
{}
```

```cpp=
Human::Human (const std::string& name, float size, unsigned birth_year)
: name_ (name), size_ (size), birth_year_ (birth_year)
{}
```

> Le '&' est une reference en C++ (similaire a un pointeur)

```cpp=
Human h1 = Human ("Alain Térieur", 1.80, 1970);
Human h2 ("Alex Térieur", 1.78, 1975);
Human h3 { "Vladimir Guez", 1.83, 1980 };
auto h4 = Human { "Anne Titgoutte", 1.85, 1985 };
Human* h5 = new Human ("Corinne Titgoutte", 1.68, 1990);
auto h6 = std::make_unique<Human> ("Justine Titgoutte", 1.70, 1995);
```

> auto : maniere de detecter automatiquement le type (de facon statique)

> 'std::make_unique<Human>' : garantie qu'il n'y a qu'une reference sur cet objet (le compilateur sait qu'il peut le detruire une fois qu'il n'est plus utilise)
> /!\ Pas comme un garbage collector

---
- ++Constructeur de la classe Human en JAVA++
```java=
class Human {
    String name;
    float size;
    int birthYear;
    
    Human (String _name, float _size, int _birthYear) {
        name = _name;
        size = _size;
        birthYear = _birthYear;
    }
}
```
> En JAVA, obligation de mettre le constructeur dans la classe

> Dans tous les langages orientes objets faisant du dispatch simple, pointeur cache (this)

```java=
Human h1 = new Human ("Alain Térieur", 1.80f, 1970);
```

## Destruction

- Vision atomique de la phase de disparition d'un objet
- Assure le nettoyage
- **Destructeur** : 
    - Procedure speciale (pas de type de retour)
    - Fourni par defaut
    - Nom predefini
    
---
- ++Destructeur en UML++
```uml=
Human
---
---
«destroy»
~Human ()
```

> Tres rare d'appeler un destructeur en UML

---
- ++Destructeur en C\+\+++
```cpp=
class Human {
~Human ();
};
```

De preference en dehors de la classe : 
```cpp=
Human::~Human ()
{}
```

```cpp=
// Called automatically for stack-allocated objects
// Called by explicit pointer deletion:
delete h5;
// Called automatically for smart pointers (ex make_unique)
```

> *delete est a new ce que free() est a malloc()*

--------------

## Desctruction (Finaliseur)

**Finaliseur** : Langage a garbage collector

**Garbage collector** : Supprimer la gestion de memoire manuelle du programmeur (composant logiciel qui analyse automatiquement les zones non  utilisees de la memoire)
> Ici on ne sait pas *quand* les objets vont etre detruits

```java=
class Human {
    void finalize () { ... }
}
```
> Mais peu fiable

```java=
// Called automatically by the garbage collector
// Don't do this for real!
h1 = null;
System.gc ();
```
> On force le garbage collector a s'executer

---
# Portee de l'information

## Niveau instance

![](https://i.imgur.com/JOJ5gYu.png)

- **Attribut d'instance** : une declaration par classe, une valeur par objet
> Prototype dans la classe, definition par objet

- **Methodes** : une declaration par classe ("single dispatch"), mais l'acces au contenu specifique est specifique a chaque objet

```cpp=
void Human::hello ()
{
    std::cout << "Hello! I'm " << name_ << ", "
    << size_ << "m, "
    << age () << "yo.\n";
}

h1.hello ();
h5->hello ();
```

```java=

class Human {
    void hello () {
        System.out.println ("Hello! I'm " + name + ", "
        + size + "m, "
        + age () + "yo.");
    }
}

h1.hello ();
```

---
## Attributs de classe

![](https://i.imgur.com/gPrLNX3.png)

- Attributs definis dans la classe et communs a tous les objets
- Acces ne necessite donc pas l'existance d'une instance
- *static* en JAVA et en C++

```cpp=
// C++

class Human {
    static unsigned population_;
};
    
// Access via objects: h1.population_ / h5->population_
unsigned Human::population_ = 0;
Human::Human (const std::string& name, float size, unsigned birth_year) {
    population_ += 1;
}

Human::~Human () {
    population_ -= 1;
}
```


```java=
// JAVA

class Human {
    // Access via the class: Human.population
    // Access via objects: h1.population
    static int population = 0;
    Human (String _name, float _size, int _birthYear) {
        population += 1;
    }
    
    void finalize () {
        population -= 1;
    }
}
```

