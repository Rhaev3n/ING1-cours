[NET1] Reseaux (3)
===

> Modele TCP/IP (L3 et L4)

## IP (Internet Protocol)

Avant, le L3 et L4 etaient regroupes en un seul truc : Le Transmission Control Program

**Vint Cerf** (fondateur de l'Internet Society) et **Jon Postel** (editeur des RFC)

Principe historique des classes
- Si premier bit de l'adresse IP = 0 -> classe A (/8 0-127)
- Si premier bit de l'adresse IP = 10 -> classe B (/16 128-191)
- Si premier bit de l'adresse IP = 110 -> classe C (/24 192-243)

On utilise maintenant les **CIDR** (Classless Inter Domain Routing)

**IANA** (Internet Assigned Numbers Authority) : Attribut les classes (Historiquement le pseudo de Jon Postel)
**ICANN** (1998) : Cree par Jon Postel, sur-ensemble de l'IANA

Aujourd'hui, l'IANA est une branche de l'ICANN qui gere plusieurs choses : 
- Gestion des noms de domaines
- Gestion des IP
- Gestion des protocoles

----
#### IANA IPv4 Address Space Registry
IANA : Delegue des /8 au RIR

**RIR (Regional Internet Registry)** : 
![](https://i.imgur.com/1WwMGwT.png)
- Distribue les /8 aux registres locaux (LIR), aux fournisseurs d'acces Internet

## Chemin d'un paquet d'une IP vers l'autre

- Ne sait pas a l'avance quel chemin il va suivre
- Ne sait que la ou il est et les adresses auxquelles il est directement connecte grace a la table de routage

**Table de routage** : Contient les adresses des reseaux auxquels le routeur est directement connecte, des routes et une route par defaut

> Les routeurs les plus hauts de la chaine des contiennent l'integralite des routes d'Internet

**DFZ** (Default Free Zone) : Ensemble des routeurs n'utilisant pas de routes par defaut pour acheminer leurs paquets vers une destination
> Leurs tables de routage sont les DFT (Default Free Tables)

**PMTU (Path MTU ou Path Maximum Transmission Unit)** : 
Il ne faut pas que la taille du paquet depasse la taille maximale autorisee par l'ensemble des liens traverses (le PMTU)
- Envoi de message quand MTU trop petite : On drop le paquet et on envoie un message d'erreur avec ICMP

### IP Header
![](https://i.imgur.com/rnyCWZ7.png)

> - Version 4
> - Taille dynamique
> - Flags : MF (1 = Je suis le dernier paquet fragmente) et DF (Don't Fragment)

**PMTU Discovery** : Algorithme pour s'assurer que le chemin est assez grand
- On envoie le paqsuet avec le flag DC a 1 et on parcourt le chemin, si on se prend un message d'erreur ICMP, on passe par un autre chemin etc

:::danger
ICMP necessaire au bon fonctionnement d'Internet
:::

> En combien de /27 je peux decouper mon /24 ? En $2^{(27-24)}$

## UDP (User Datagram Protocol)

- L4 Transport
- Sert au multiplexing (ports)

Ce qui peut mal se passer dans la vie d'un paquet
- LOSS (empeche par TCP)
- DUPLIQUE (empeche par TCP)
- REORDERED (empeche par TCP)
- CORRUPTED (empeche par UDP)

## UDP vs TCP

==Headers TCP et UDP==
![](https://i.imgur.com/UBs1peL.png)

UDP : 
- Connectionless
- Unicast, broadcast, multicast

TCP : 
- Protocol One To One
- Connexion oriented protocol
- Ne peut faire que de l'unicast (le paquet n'a qu'un destinataire)

## TCP (Transmission Control Protocol)

- Abstraire le fait qu'un message a ete envoye en plusieurs paquets

*3 Way Handshake* : Etablit quand on initie une connexion TCP
- 1: SYN 0 (Sequence number) 42 (Data offset)
- 2: Ack 43
- 2: SYN 51 (Data offset) 
- 1: Ack 52