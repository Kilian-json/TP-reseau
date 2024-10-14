I. ARP basics

☀️ Avant de continuer...
```
PS C:\Users\robre> ipconfig /all
Carte Ethernet Ethernet :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
  ☀️ Adresse physique . . . . . . . . . . . : 0A-00-27-00-00-05
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::caf0:4920:dd19:721c%5(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
   IAID DHCPv6 . . . . . . . . . . . : 621412391
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-86-56-EE-F4-6A-DD-2C-70-19
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

☀️Affichez votre table ARP
```
PS C:\Users\robre> arp -a
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 10.33.77.158 --- 0x12
  Adresse Internet      Adresse physique      Type
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école
```
PS C:\Users\robre> arp -a
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 10.33.77.158 --- 0x12
  Adresse Internet      Adresse physique      Type
 ☀️ 10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ Supprimez la ligne qui concerne la passerelle
```
PS C:\Windows\system32> arp -d 10.33.79.254 | arp -a
```

☀️ Prouvez que vous avez supprimé la ligne dans la table ARP
```
PS C:\Windows\system32> arp -d 10.33.79.254 | arp -a

Interface : 192.168.56.1 --- 0x5
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 10.33.77.158 --- 0x12
  Adresse Internet      Adresse physique      Type
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ Wireshark

Voir le document arp1.pcap

II. ARP dans un réseau local

1. Basics

☀️ Déterminer
Adresse IP du partage :
Adresse MAC :
```
PS C:\Windows\system32> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   ☀️Adresse physique . . . . . . . . . . . : F4-6A-DD-2C-70-19
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a01:cb01:307d:c647:2397:edca:ba9b:2fe1(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a01:cb01:307d:c647:acb7:5090:3fae:c289(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18(préféré)
   ☀️Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.14(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 16:12:40
   Bail expirant. . . . . . . . . . . . . : mercredi 9 octobre 2024 16:12:40
   Passerelle par défaut. . . . . . . . . : fe80::2037:a5ff:fe88:6764%18
                                       172.20.10.1
   Serveur DHCP . . . . . . . . . . . . . : 172.20.10.1
   IAID DHCPv6 . . . . . . . . . . . : 183790301
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-86-56-EE-F4-6A-DD-2C-70-19
   Serveurs DNS. . .  . . . . . . . . . . : fe80::2037:a5ff:fe88:6764%18
                                       172.20.10.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

☀️ DIY
```
PS C:\Windows\system32> ipconfig
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6. . . . . . . . . . . . . .: 2a01:cb01:307d:c647:2397:edca:ba9b:2fe1
   Adresse IPv6 temporaire . . . . . . . .: 2a01:cb01:307d:c647:e0db:129:a395:399d
   Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18
   ☀️Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.16
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Passerelle par défaut. . . . . . . . . : fe80::2037:a5ff:fe88:6764%18
                                       172.20.10.1
```

☀️ Pingz !
ping adresse IP:
```
PS C:\Windows\system32> ping 172.20.10.2

Envoi d’une requête 'Ping'  172.20.10.2 avec 32 octets de données :
Réponse de 172.20.10.2 : octets=32 temps=232 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=155 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=57 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=63 ms TTL=128

Statistiques Ping pour 172.20.10.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 57ms, Maximum = 232ms, Moyenne = 126ms
PS C:\Windows\system32> ping 172.20.10.4

Envoi d’une requête 'Ping'  172.20.10.4 avec 32 octets de données :
Réponse de 172.20.10.4 : octets=32 temps=1331 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=407 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=7 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=122 ms TTL=128

Statistiques Ping pour 172.20.10.4:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 7ms, Maximum = 1331ms, Moyenne = 466ms
```
ping site internet :
```
PS C:\Windows\system32> ping google.com

Envoi d’une requête 'ping' sur google.com [142.250.179.110] avec 32 octets de données :
Délai d’attente de la demande dépassé.
Réponse de 142.250.179.110 : octets=32 temps=210 ms TTL=110
Réponse de 142.250.179.110 : octets=32 temps=77 ms TTL=110
Réponse de 142.250.179.110 : octets=32 temps=191 ms TTL=110

Statistiques Ping pour 142.250.179.110:
    Paquets : envoyés = 4, reçus = 3, perdus = 1 (perte 25%),
Durée approximative des boucles en millisecondes :
    Minimum = 77ms, Maximum = 210ms, Moyenne = 159ms
```

2. ARP

☀️ Affichez votre table ARP !
```
PS C:\Windows\system32> arp -a

Interface : 192.168.56.1 --- 0x5
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 172.20.10.3 --- 0x12
  Adresse Internet      Adresse physique      Type
  172.20.10.1           22-37-a5-88-67-64     dynamique
  ☀️172.20.10.2           4c-82-a9-1c-e3-b7     dynamique
  ☀️172.20.10.4           d4-d8-53-78-45-b0     dynamique
  172.20.10.15          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```
videz votre table arp :
```
PS C:\Windows\system32> netsh interface IP delete arpcache
Ok.
```

☀️ Capture arp2.pcap

voir le document arp2

3. Bonus : ARP poisoning
Sur ma VM kali :
```
┌──(kilian㉿vmkali)-[~]
└─$ sudo su -   

┌──(root㉿vmkali)-[~]
└─# echo 1 > /proc/sys/net/ipv4/ip_forward

┌──(root㉿vmkali)-[~]
└─# arpspoof -i eth1 192.168.56.1
8:0:27:fd:42:35 ff:ff:ff:ff:ff:ff 0806 42: arp reply 192.168.56.1 is-at 8:0:27:fd:42:35
```