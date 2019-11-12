[NET1] Reseaux (5)
===

# Applicatif

> DHCP
> HTTP

## DHCP

**DHCP (Dynamic Host Configuration Protocol)** : Fournit le minimum pour survivre : 
- **Adresse IP** 
- **Mask** (masque de sous-reseau)
- **Default GW** (Default gateway : IP du routeur)
- **DNS**

### Contacter le serveur DHCP

:::info
Comment contacter le DHCP quand on a pas encore recupere son addresse IP ?
:::

- On envoie un message de ==**discover**==

LAYER 2 $\Rightarrow$ Broadcast 
- Avec la MAC de destination FF:FF:FF:FF 
- IP source 0.0.0.0
- IP destination 255.255.255.255

LAYER 4 $\Rightarrow$ UDP
- Port source 68
- Port destination 67
> Rappel : Pas de broadcast en TCP

### Reponse

- Le serveur repond avec une ==**offer**==
- On accepte l'offre en faisant une ==**request**==
- Le serveur est ok, il repond avec une ==**acknoledge**==

> **DORA**

$\Rightarrow$ On passe par un **relay**

Sur chaque reseau local on installe un **relay**, qui est relie au **client** et peut contacter un **unique** DHCP

:::info
Les addresses recuperees ne sont pas forcement random
:::

## HTTP

- *Hypertext Transfer Protocol*
- Protocole de requete reponse (entre le client et le serveur)
- Fonctionne sur TCP
- Stateless

Plusieurs versions de HTTP
On parle ici de **HTTP 1.1**

### Format d'une URL
++Exemple++
http://toto.com/lol?mdr=42
- **scheme** : http
- **authority** (hostname) : toto.com
- **path** : lol
- **query string** : mdr=42

**Document hypertexte** : Documents connecte a d'autres documents (avec des liens hypertextes)
> Reseaux de documents interconnectes independamment de la machine sur laquelle ils se trouvent

### Verbes

**Verbes** : Methodes de requetes HTTP

- **GET** : demande d'un acces en lecture a un document
	- Safe : ne modifie pas le serveur
	- Peut etre mis en cache
- **POST** : demande la creation d'une ressource
	- envoi des donnees via formulaire
- **PUT** : Modifie ressource existante
- **DELETE** : Supprime resource

### Request HTTP

++Requete HTTP++ : 
GET /lol?mdr=42 HTTP/1.1
(DNT:1
ACCEPT
U-A
HOST) headers

> U-A : le type d'application utilisee par le client (Firefox etc)
> HOST obligatoire en HTTP/1.1

++Reponse++:
HTTP/1.1 200 OK
(CONTENT_TYPE
CONTENT_LENGTH) headers
content

> CONTENT_LENGTH : taille du body

### Exemple

nc (netcat) : envoie le message litteral sur le reseau
> nc google.com 80
> GET: /mdr HTTP/1.1
> HOST: google.com
> User-Agent: Ma bite

- HTTP devenue une API
- Aujourd'hui les applications se basent enormement sur HTTP / TLS (Transport Layer Security) pour communiquer

> HATEOAS : Http as the engine of the application state

**SOAP** fichier XML
**REST** (Representational State Transfer)

### Proprietes des verbes

GET, POST et DELETE sont idempotent (a l'oppose de POST) (f(f(x)) = f(x))

### Statuscode HTTP

- 1xx : informationnel
- 2xx : success
- 3xx : redirections
- 4xx : erreurs du client
- 5xx : erreurs du serveur