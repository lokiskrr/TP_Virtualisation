# Part 1 : Most simplest LAN

## 1. Intro

## 2. Tableau d'adressage

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

📁 [p1_ping.pcap](./p1_ping.pcapng)




