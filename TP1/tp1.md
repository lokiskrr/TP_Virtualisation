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
[root@efrei-xmg4agau1 ~]# cat /etc/dnsmasq.conf
interface=enp0s8

dhcp-range=10.1.1.10,10.1.1.50,12h
dhcp-option=option:netmask,255.255.255.0
```

🌞 **Récupérer une IP automatiquement depuis les 3 nodes**

```
VPCS> ip dhcp
DDORA IP 10.1.1.45/24 GW 10.1.1.253
```

```
VPCS> ip dhcp
DDORA IP 10.1.1.46/24 GW 10.1.1.253
```

```
VPCS> ip dhcp
DDORA IP 10.1.1.47/24 GW 10.1.1.253
```
📁 [p3_dhcp.pcap](./p3_dhcp.pcapng)

## 5. DHCP lease

🌞 **Bail DHCP**

```
1767920998 00:50:79:66:68:02 10.1.1.47 VPCS1 01:00:50:79:66:68:02
1767920908 00:50:79:66:68:01 10.1.1.46 * 01:00:50:79:66:68:01
1767920561 00:50:79:66:68:00 10.1.1.45 * 01:00:50:79:66:68:00
~
```

🌞 **Use `grep`**

```
[root@efrei-xmg4agau1 /]# cat var/lib/dnsmasq/dnsmasq.leases | grep VPCS1
1767920998 00:50:79:66:68:02 10.1.1.47 VPCS1 01:00:50:79:66:68:02
```

# Part 4 : real haxor

## 1. DHCP spoofing

### A. Setup

🌞 **Installez et configurez un serveur DHCP** sur votre machine attaquante

```
[root@atk ~]# systemctl status dnsmasq
● dnsmasq.service - DNS caching server.
     Loaded: loaded (/usr/lib/systemd/system/dnsmasq.service; enabled; preset: disabled)
     Active: active (running) since Thu 2026-01-08 15:41:14 CET; 4min 3s ago
 Invocation: 1ce686c97ca44f9d9cfd39080e92c812
    Process: 820 ExecStart=/usr/sbin/dnsmasq (code=exited, status=0/SUCCESS)
   Main PID: 844 (dnsmasq)
      Tasks: 1 (limit: 5840)
     Memory: 1.8M (peak: 2.2M)
        CPU: 44ms
     CGroup: /system.slice/dnsmasq.service
             └─844 /usr/sbin/dnsmasq

janv. 08 15:41:14 atk systemd[1]: Started dnsmasq.service - DNS caching server..
janv. 08 15:41:14 atk dnsmasq[844]: reading /etc/resolv.conf
janv. 08 15:41:14 atk dnsmasq[844]: using nameserver 172.26.129.138#53
janv. 08 15:41:14 atk dnsmasq[844]: using nameserver 172.26.129.139#53
janv. 08 15:42:55 atk dnsmasq-dhcp[844]: DHCPDISCOVER(enp0s8) 00:50:79:66:68:01
janv. 08 15:42:55 atk dnsmasq-dhcp[844]: DHCPOFFER(enp0s8) 10.1.1.246 00:50:79:66:68:01
janv. 08 15:42:55 atk dnsmasq-dhcp[844]: DHCPDISCOVER(enp0s8) 00:50:79:66:68:01
janv. 08 15:42:55 atk dnsmasq-dhcp[844]: DHCPOFFER(enp0s8) 10.1.1.246 00:50:79:66:68:01
janv. 08 15:42:56 atk dnsmasq-dhcp[844]: DHCPREQUEST(enp0s8) 10.1.1.246 00:50:79:66:68:01
janv. 08 15:42:56 atk dnsmasq-dhcp[844]: DHCPACK(enp0s8) 10.1.1.246 00:50:79:66:68:01 VPCS1
```

🌞 **Test !**

```
VPCS> ip dhcp
DDORA IP 10.1.1.246/24 GW 10.1.1.37
```

### B. Race !

📁 [p4_dhcp_race.pcap](./p4_dhcp_race.pcapng)

Prewt. 🐈




