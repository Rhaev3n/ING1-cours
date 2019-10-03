[NET1] Reseaux (1)
===

> Kit de survie en reseau

## Datalink Modele OSI (Open System Interconnect)

> ==Problematiques reseaux==
> 1. [PHY] Comment connecter 2 machines physiquement ? Par quel medium ?
> 2. [LAN] Comment connecter plus de machines a ce reseau ? En suivant quel schema ?
> 3. [INTERNET] Chacun parle son langage, mais il faut etablir une langue universelle
> 4. [TRANSPORT] Quelle abstraction va-t-on offrir a notre utilisateur
> 5. [SESSION] 
> 6. [PRESENTATION]
> 7. [APPLICATION]

1. **Topologie** : maniere de connecter differentes machines *localement*

> Un medium est **partage** (ex, l'air qu'on respire), il faut donc trouver un moyen de gerer son partage (ex, temps de parole)
 
2. **Controle d'acces au medium ou Media Access Control (MAC)** : tout le monde ne peut pas parler sur le medium en meme temps

3. **Internet (Inter Network)** : interconnection de reseaux

## Modele TCP/IP

> Concurrents du modele OSI
> Leur problematique n'est que l'interconnection
> Standardise par l'IETF

1. **TCP** : protocole repondant aux etapes 3 a 4 -> *l'interconnection*

Devenu l'**API des sockets** : **IP** qui s'occupe d'INTERNET, et donc de trouver son chemin dans le reseau et **TCP** qui ne s'occupe que du TRANSPORT

Les bas niveaux chez TCP/IP sont appeles Host Network (Pas leur probleme)

2. **Problematique bas niveau (PHY et LAN)**

> Differents protocoles, tous centralises et standardises par l'**IEEE802**

## Modele hybride

> Modele utilise aujourh'hui

1) **PHY** (Couche physique)
2) **DL** (Datalink)
3) **INTERNET** (IP)
4) **TRANSPORT**
7. **APPLICATION**
8. USER

## Protocoles existants

==Protocoles DL==
- WIFI
- ETH
- UFI

==Protocoles Internet==
- IPv4, IPv6

==Protocoles Transport==
- TCP
- UDP (absence de design, ex jv, telephonie, streaming -> peu important si on perd des paquets)
> **Multiplexage** : donnent plusieurs flux reseaux sur une meme machine -> **ports**

==Protocoles applicatifs==
- HTTP
- PTP
- SMTP
- SSH
- DHCP
- DNS

> Schema en sablier -> figure centrale d'IP (centralisation)
> Combo principal aujourd'hui : IP - TCP - HTTPS

## IP

**Switch (L2)** : Permet de creer un reseau local
**Router (L3)** : Interconnecte plusieurs reseaux locaux

> Toutes les machines au sein d'un reseau local ont le **meme prefixe** (qui permet de les identifier)
> > 198.18.42.0/24
> > 203.0.113.0/24
> > -> Les 24 premiers bits appartienent au prefixe

> Un routeur a autant d'addresses IP que de reseaux sur lequel il est connecte

**Nombre d'adresses possibles dans un reseau local** : 
    - Addresse sur 32 bits
    - Prefixe sur x bits (203.0.113.0/x) = ==2^(32 - x)== addresses possibles
    
> Prefixe 203.0.113 reserve aux exemple et a la documentation par le standart

Protocole ICMP : protocole de controle et de debug (ex: ping)