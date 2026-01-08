# TP2 : + de réseau + de hax

## 7. Proof or lie

🌞 **Tout le monde doit pouvoir se `ping`**

```
VPCS> ping 10.2.1.12
84 bytes from 10.2.1.12 icmp_seq=1 ttl=64 time=3.768 ms
84 bytes from 10.2.1.12 icmp_seq=2 ttl=64 time=4.381 ms
84 bytes from 10.2.1.12 icmp_seq=3 ttl=64 time=3.403 ms
84 bytes from 10.2.1.12 icmp_seq=4 ttl=64 time=4.268 ms
84 bytes from 10.2.1.12 icmp_seq=5 ttl=64 time=4.616 ms

VPCS> ping 10.2.2.12
84 bytes from 10.2.2.12 icmp_seq=1 ttl=64 time=6.294 ms
84 bytes from 10.2.2.12 icmp_seq=2 ttl=64 time=4.971 ms
84 bytes from 10.2.2.12 icmp_seq=3 ttl=64 time=4.810 ms
84 bytes from 10.2.2.12 icmp_seq=4 ttl=64 time=6.799 ms
84 bytes from 10.2.2.12 icmp_seq=5 ttl=64 time=4.704 ms

VPCS> ping 10.2.1.12
84 bytes from 10.2.1.12 icmp_seq=1 ttl=64 time=5.386 ms
84 bytes from 10.2.1.12 icmp_seq=2 ttl=64 time=3.810 ms
84 bytes from 10.2.1.12 icmp_seq=3 ttl=64 time=4.094 ms
84 bytes from 10.2.1.12 icmp_seq=4 ttl=64 time=4.024 ms
84 bytes from 10.2.1.12 icmp_seq=5 ttl=64 time=4.027 ms

VPCS> ping 10.2.2.11
84 bytes from 10.2.2.11 icmp_seq=1 ttl=64 time=5.054 ms
84 bytes from 10.2.2.11 icmp_seq=2 ttl=64 time=4.286 ms
84 bytes from 10.2.2.11 icmp_seq=3 ttl=64 time=4.713 ms
84 bytes from 10.2.2.11 icmp_seq=4 ttl=64 time=4.740 ms
84 bytes from 10.2.2.11 icmp_seq=5 ttl=64 time=4.112 ms
```

📁 **`p1_routed_ping.pcap`** 

# TP2 Part2 : C'est mieux avec internet

## 1. Accès internet routeur`

🌞 **Prouver que...**

```

```

📁 **`p1_no_nat.pcap`**

## 2. Accès internet clients

🌞 **Proooooooooof or lie**

```

```

📁 **`p1_nat.pcap`**

📁 **r1_running_config.txt**

## 3. Vrai accès internet clients

🌞 **Prove it**

```

```

## 4. DHCP again

🌞 **Test test test** : ajouter un nouveau VPCS au LAN1, le bro `node5.tp2.efrei`

```

```

# TP2 Part3 : Time to attack all this

## 1. Intro

## 2. Machine attaquante

## 3. ARP spoofing

📁 **`p3_arp_mitm.pcap`**

## 4. DHCP spoofing

### B. Proofs

🌞 **Test test test** : ajouter un nouveau VPCS au LAN1, le bro `node6.tp2.efrei`

```

```

📁 **`p3_dhcp_mitm.pcap`**

# TP2 Part4 : Alors koa c tou ? On refé just la mem choz ke o tp1 enfet enfet ? Bah non

## 1. Intro

## 2. Go for it

### A. Setup

🌞 **Préparer le DNS spoof**

```

```

### B. Vérification

🌞 **S'assurer que c'est up & running**, on en profite pour réviser un peu de shell

```

```

### C. Hax ?

🌞 **Relance ton attaque DHCP spoof** depuis la machine attaquante

```

```

🌞 **Test test test** : ajouter un nouveau VPCS au LAN1, le bro `node7.tp2.efrei`

```

```

📁 **`part4_dns_spoof.pcap`**, on doit y voir :
