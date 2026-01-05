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

node1.tp1.efrei
```
VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.1/24          0.0.0.0           00:50:79:66:68:00  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6800/64
```


node2.tp1.efrei
```
VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.2/24          0.0.0.0           00:50:79:66:68:01  10002  127.0.0.1:10003
       fe80::250:79ff:fe66:6801/64
```

## 4. IP Setup

🌞 **Définir une IP statique sur les deux machines**

node1.tp1.efrei
```
VPCS> ip 10.1.1.1
Checking for duplicate address...
PC1 : 10.1.1.1 255.255.255.0
```

node2.tp1.efrei
```
VPCS> ip 10.1.1.2
Checking for duplicate address...
PC1 : 10.1.1.2 255.255.255.0
```
🌞 **Proof !**

node1.tp1.efrei
```
VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.1/24          0.0.0.0           00:50:79:66:68:00  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6800/64
```


node2.tp1.efrei
```
VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.2/24          0.0.0.0           00:50:79:66:68:01  10002  127.0.0.1:10003
       fe80::250:79ff:fe66:6801/64
```

🌞 **Effectuer un `ping` d'une machine à l'autre**

node1.tp1.efrei
```
VPCS> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=1.415 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=1.502 ms
84 bytes from 10.1.1.2 icmp_seq=3 ttl=64 time=1.647 ms
84 bytes from 10.1.1.2 icmp_seq=4 ttl=64 time=1.620 ms
84 bytes from 10.1.1.2 icmp_seq=5 ttl=64 time=1.409 ms
```

## 5. Analyze

🌞 **Protocolz ?**

```
ARP
```

📁 **`p1_ping.pcap`** 




