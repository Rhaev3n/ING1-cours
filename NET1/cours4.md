[NET1] Reseaux (4)
===

> But de la couche 3 : trouver son chemin dans un reseau

Routeur : 
- Decremente le TTL (Time To Leave) des paquets
- Check la table de routage pour repropager le paquet


La couche 4 utilise un **End-To-End Protocol**
- Problematiques qui concernent les destinataires finaux

# IP

**RFC 1918** : Definit 3 prefixes d'adresse sont reserves a un usage prive (on peut s'en servir de chez soi sans permission) peut pas s'en servir sur Internet
- 10.0.0.0/8
- 192.168.0.0/16
- 172.16/12 (de 172.16.0.0 a 172.31.255.255)

==**Problematique**== 
Comment 2 personnes ayant la meme addresse en local peuvent communiquer par Internet ? 

### Envoi d'un paquet depuis un reseau local

Lorsqu'un paquet sort du reseau local, en arrivant au routeur on remplace l'adresse du destinataire (locale) par l'addresse publique -> On utilise du SNAT

**SNAT (Source Network Address Translation)** : On traduit notre addresse de source

### Reception d'un paquet dans un reseau local

> Le routeur doit se souvenir qui a envoye tel paquet quand il en recoit un paquet pour son reseau local > Besoin de state > C'est la merde

:::info
**Solution**
On redirige les paquets en fonction du port sur lequel il est envoye
:::

++Problemes++ : 
- Les routeurs sont obliges de regarder ce qui se passe dans la couche 4
- C'est n'importe quoi.
- Le NAT c'est de la merde.

**DNAT (Destination Network Address Translation)** : On veut contacter une machine dans un reseau prive

> Probleme du Hair Pinning

# Iptables

[// iptables flowchart](https://stuffphilwrites.com/2014/09/iptables-processing-flowchart/)
![](https://i.imgur.com/605IZj3.jpg)


3 scenarios possibles avec les paquets : 
- **Input** : Je recois un paquet
- **Output** : J'envoie un paquet
- **Forward** : Repropager un paquet qui n'est pas pour moi a un autre

On ne s'interesse qu'aux noeuds de type **filter** et **nat**
- **filter** : Firewall (Accept, drop, reject)
- **nat** : NAT
---

## Table filter

- Lister toutes les regles de la table filter
    - sudo iptables -t filer -L
- Ajouter une regle dans la table filter : 
    - sudo iptables -t filter -A INPUT -p tcp --dport 4242 -j reject
        - On rejete les paquets envoyes sur le port 4242
    - sudo iptables -t filter -A INPUT -p tcp --dport 4242 -j reject
        - Drop les paquets envoyes

## Table nat

On s'interesses aux tables Pre-Routing et Post-Routing

- DNAT dans Pre-Routing
- SNAT dans Post-Routing

Masquerade = SNAT