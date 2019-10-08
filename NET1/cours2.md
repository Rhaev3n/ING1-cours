[NET1] Reseaux (2)
===

> IEEE802

**Rappel** : But de la couche 2 (DataLink) -> creer un reseau local

## Types d'interconnexion
**PTP** : Point to point protocol, connecte physiquement 2 machines ensemble (couche 1)
**Reseau en mailles** : cf Moodle
**Ring topology** : circualtion dans un seul sens ou chaque machine re-propage le message (n'existe plus)
**Topologie en bus** : Chaque machine est connectee sur un meme cable (le medium est partage -> une seule personne parle a la fois)
> Connecteurs co-axials 10BASE-5 & 10BASE-2 & 100BASE-T
**Topologie en etoile** : Appareil central qui interconnecte toutes les machines (Plus commune)

## Domaines
**Domaine de collision** : Endroit ou on ne peut parler qu'un seul a la fois (Section critique) -> Un endroit ou le medium est partage
**Domaine de broadcast** : L'ensemble des machines qui recoivent un message lorsque je fais un broadcast

## Modes de transmissions
**Simplex** : Mode de transmission unidirectionnel (l'information ne va que dans un sens)
> ex : Radio

**Half-Duplex** : L'emetteur et le recepteur peuvent parler, mais pas les 2 en meme temps
> ex : Dialogue entre 2 individue, talkie-walkie

**Full Duplex** : Fete du slip -> Tout le monde peut parler en meme temps (Aucun problem)
> ex : Sockets

## Historique 
**CSMA/CP (Algo d'Ethernet)**
CS : Carrier sens
MA : Multiple Access
CP : Collision Detection
> Topologie en bus
> Algo de MAC
> Standardise en 1983 par IEEE802.3

**MAC** : Medium Access Control
**EoTP** : Ethernet over Twisted Pair
Cable ethernet moderenes = 8P8C -> Cable RJ45 sans "boule"

Arret de la topologie en bus pour la *topologie en etoile*
**HUB** : Machine centrale du reseau en etoile, propage a tout le monde

**Switch** : successeur du HUB

## Trame Ethernet
|Preamble (7o)|SFD (1o)|MAC Destination (6o)|MAC Source (6o)|EtherType (2o)|PayLoad (460-1500o)|FCS (4o)|IPG (12o)|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|

![](https://i.imgur.com/TT1ty8k.png)

> Ici MAC : adresse de la machine au sein du reseau local
> Avec WireShark, on voit la MAC Destination, MAC Source, l'EtherType et le Payload

Le switch attend de recevoir une trame d'un de ses ports (physique), il retient / apprend son adresse MAC, et construit une FIB

**FIB** (Forwarding Information Base) : Association de port et adresses MAC correspondantes

**Boucle reseau** : Double connexion de deux switchs -> pose probleme lors d'un broadcast

**STP** : Spanning Tree Protocol (arbre de recouvrement -> casse les cycles d'un graphe pour en faire un arbre) Permet de determiner une topologie sans boucles

## VLANS

> Problematique : Faire plusieurs reseaux locaux mais sans ajouter un nouveau switch pour chacun

-> On simule des reseaux locaux au sein d'un switch
Standardise par 802.1Q

On peut configurer les ports des switch en 2 modes : 
- Mode **access** (avec un numero) : Les machines accedant au switch un meme numero sont considerees comme etant du meme reseau local
- Mode **trunk** : On rajoute un header Ethernet pouvant connecter des switch (partage des politiques de VLAN)
![](https://i.imgur.com/BpgKBHI.png)

> Pour interconnecter ces switch, on doit utiliser un **routeur**
> Router (L3) + Switch (L2) = Switch L3