# Part 1 : Most simplest LAN

## 1. Intro

![Topologie n°1](assets/img/topo1.png)

???+ note

    Pour cette partie on a juste besoin de "clients réseau" : un machin qui a une carte réseau et peut donc avoir une adresse IP. Envoyer des `ping` pour tester. Et c'est tout, ça nous va.  
    Donc vous pouvez utiliser des VMs Rocky si vous voulez, **mais sinon, GNS3 propose les VPCS : des clients réseau ultra simpliste.**  
    Je vous recommande très fort d'utiliser ça pour économiser des ressources et pas attendre 15 plombes après vos VMs.

**Un LAN (ou "Réseau Local" en français) c'est juste un réseau formé de plusieurs machines connectées PHYSIQUEMENT entre elles.**

Pour ça, chaque machine a besoin d'au moins **une carte réseau** (ou *interface réseau* ou encore *NIC* pour *Network Interface Controller*).  
Et on relie par des câbles les machines entre elles. (Merci captain obvious ?)

**On va donc commencer au plus simple : deux machines connectées par un câble.**

Les objectifs de cette partie :

- monter la topologie dans GNS3 *(drag'n'drop des machins et tirer des câbles dans GNS3)*
- définir des IPs sur les deux machines
- visualiser l'IP choisie, ainsi que l'adresse MAC prédeterminée
- vérifier que les deux machines peuvent communiquer en faisant un `ping`
- visualiser le `ping` avec Wireshark

![Not sure](assets/meme/notsure.png)

## 2. Tableau d'adressage

Vous utiliserez les IPs suivantes pour cette partie :

| Machine           | Adresse IP    |
| ----------------- | ------------- |
| `node1.tp1.efrei` | `10.1.1.1/24` |
| `node2.tp1.efrei` | `10.1.1.2/24` |

??? warning

    Dans aucun des TPs je ne tolérerai que vous choisissiez/mettiez d'autres adresses que celles que j'indique, quand j'en indique.  
    La raison est simple : vous imposer une adresse, c'est une contrainte. Vous ne pouvez pas choisir une yolo facilité qui sortirai de j'sais pas où (genre le DHCP de Vbox).  
    Ca vous oblige à faire du setup manuel. C'EST PEDAGOGIQUE EN FAIT EN FAIT.

---

## 3. Know your MAC

🌞 **Déterminer l'adresse MAC de vos deux machines**

- depuis le terminal de chacun des clients (VM Rocky ou VPCS), déterminer son adresse MAC
- une seule commande est nécessaire sur chaque client

---

## 4. IP Setup

🌞 **Définir une IP statique sur les deux machines**

- depuis le terminal des machines Linux
- indiquez dans le compte-rendu l'ensemble des commandes réalisées
- montrez le contenu des fichiers que vous éditez (si vous en éditez)

🌞 **Proof !**

- prouver que votre changement d'IP est effectif, en une commande

🌞 **Effectuer un `ping` d'une machine à l'autre**

- c'est la commande `ping`, sans surprise vous me direz

## 5. Analyze

➜ **Wireshark !**

- vous pouvez faire un clic droit sur un câble dans GNS3 pour lancer une capture des trames qui passent dans le câble
- visualiser le `ping` entre les deux machines
- enregistrez la capture avec Wireshark (format `.pcap` ou `.pcapng`), et vous la joindrez au compte-rendu dans le dépôt git

??? note

    **Euh j'attire votre attention sur le fait que cette feature est GIGA STYLÉE.**  
    D'habitude, pour lancer une capture Wireshark, faut être sur un client, et capturer le trafic qui passer par une interface réseau.  
    C'est pas le cas ici.  
    GNS simule littéralement une capture du contenu du câble. **Genre comme si on coupait le câble au milieu et qu'on faisait un man-in-the-middle physique quoi.**  
    Trop stylé, trop pratique.

![Sniff](assets/meme/wireshark_sniff.png)

🌞 **Protocolz ?**

- déterminer quel protocole est utilisé pour envoyer des "pings"
- écrivez votre réponse dans le compte-rendu

📁 **`p1_ping.pcap`** 

- contient des ping/pong (request/reply)
- **ne contient QUE des pings et aucun autre trafic**
- mettez-moi genre 3 ou 4 aller retours

---

➜ **[Prout. Lien vers la partie 2 : Bring that switch in](2_switch.md)**
