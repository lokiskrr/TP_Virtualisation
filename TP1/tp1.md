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


# Part 2 : Bring that switch in

## 1. Intro

## 2. Tableau d'adressage

## 3. Même chose en fast

🌞 **Déterminer l'adresse MAC de vos trois machines**

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

node3.tp1.efrei
```
VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.3/24          0.0.0.0           00:50:79:66:68:02  10010  127.0.0.1:10011
       fe80::250:79ff:fe66:6802/64

```

🌞 **Définir une IP statique sur les trois machines**

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

node3.tp1.efrei
```
VPCS> ip 10.1.1.3/24
Checking for duplicate address...
PC1 : 10.1.1.3 255.255.255.0
```

🌞 **Effectuer des `ping` d'une machine à l'autre**

node1 --> node2
```
VPCS> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=1.704 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=1.205 ms
84 bytes from 10.1.1.2 icmp_seq=3 ttl=64 time=1.147 ms
84 bytes from 10.1.1.2 icmp_seq=4 ttl=64 time=1.431 ms
84 bytes from 10.1.1.2 icmp_seq=5 ttl=64 time=1.226 ms
```

node2 --> node3
```
VPCS> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=1.019 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=1.004 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=1.666 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=1.856 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=1.644 ms
```

node1 --> node3
```
VPCS> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=1.915 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=1.951 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=1.468 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=1.483 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=1.450 ms
```

## 4. ARP old friend

🌞 **Afficher la table ARP de `node1`**

```
VPCS> show arp

00:50:79:66:68:02  10.1.1.3 expires in 72 seconds
```

📁 [p2_arp_node2.pcap](p2_arp_node2.pcapng)


📁 [p2_arp_node3.pcap](./p2_arp_node3.pcapng)

# Part 3 : DHCP is a nice guy

## 1. Intro

## 2. Tableau d'adressage

## 3. Setuuuup

🌞 **Installer un serveur DHCP**

```

```

📁 **`p3_dhcp.pcap`**

## 5. DHCP lease

🌞 **Bail DHCP**

```

```

🌞 **Use `grep`**

```

```

# Part 4 : real haxor

## 1. DHCP spoofing

### A. Setup

🌞 **Installez et configurez un serveur DHCP** sur votre machine attaquante

```

```

🌞 **Test !**

```

```

### B. Race !

📁 **`p4_dhcp_race.pcap`**

## 2. BONUS : DHCP starvation

🌞 **Proof !**

```

```

## 3. BONUS : ARP poisoning

🌞 **Proof !**

```

```

Prewt. 🐈




