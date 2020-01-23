# Réseau Émergents

[**Articl SDN Architecture for 6LoWPAN Wireless Sensor Networks**](https://www.mdpi.com/1424-8220/18/11/3738/htm)

## Question 1:

Les motivations principales pour utiliser l’architecture SDN :
* __Agilité et flexibilité__ : améliore le contrôle du réseau et adapte rapidement aux changements aux besoins des entreprises. Le SDN facilite notamment la mise en place de nouveaux services.
* __Indépendance et innovation__ : Il permet aux fournisseurs du réseau d’être indépendants et y apporter leurs propres innovations.
* __Expansion vers IoT__ : Initialement utilisé pour les réseaux filaires, il se démocratise rapidement vers les réseaux sans fils afin de répondre aux besoins des objets connectés comme le réseau wifi des téléphones mobiles et le software-defined wireless sensor networks (SDWSN).


## Question 2:

* __Idée__ :

L’idée du SD6WSN est d’appliquer les principes du SDN au 6LoWPAN afin de supporter l’implémentation des applications réseaux complexes, ce que n’offre pas le protocole RPL (routing protocol for low power networks and losses) du 6LoWPAN.

De plus, 6LoWPAN utilise le protocole DODAG (destination oriented directed acyclic graph), ainsi que RPL. Cet algorithme n’élimine pas les boucles et dans le cas d’un goulot d’étranglement on observe plusieurs fragmentations des messages envoyés.

* __Choix du design & découverte du réseau__ :

![Architecture du SD6WSN](img1.png "Architecture du SD6WSN")


L’architecture SD6WSN comporte une couche de contrôle incluant la découverte de réseau et les fonctions de contrôle de flux, et le « southbound API » permet la communication entre cette couche de contrôle et les nœuds.

L’interface southbound utilise le protocole SD6WSNP et envoie ses messages à travers l’API CoAP de la librairie Libcoap.

RPL est toujours utilisé pour le routage des messages SD6WSNP pour réduire les coûts d’envoi et optimiser le trafic du réseau, cependant pour davantage de qualité de services le routage de paquets IPv6 vers le contrôleur est fait par le standard TCP/IP.

SD6WSNP définit 4 messages: node-mod, info-get, flow-mod and packet-in. Les messages sont classifié suivant les processus auxquels ils sont associés . Node-mod and info-get are utilisé pour la découverte du réseau :

Node-mod est le 1er message envoyé par SD6WSNP, depuis le contrôleur au routeur 6LBR, qui demande une notification à chaque fois qu’un nouveau nœud est identifié par RPL. Et après avoir reçu une notification, le contrôleur envoie un message info-get afin d’obtenir les voisins qui ont été découverts et leur qualité du trafic respective.

## Question 3:

Avec la flexibilité du paradigme SDN, on peut définir puissance d’émission de chaque nœud ainsi réduire la consommation d’énergie et augmenter la durée de vie de la batterie.

De plus, la découverte du réseau centralisée permet au le contrôleur d’avoir une vision globale de toute la topologie pour ainsi définir le meilleur chemin à emprunter ce qui permet aussi de réduire le trafic et l’énergie consommée.




-----------------------------------------------------------Fin-----------------------------------------------------------
