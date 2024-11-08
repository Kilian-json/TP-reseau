1. Quelques pings

🌞 Prouvez que votre configuration est effective
Sur mon pc:
```
PS C:\Windows\system32> Get-NetIPAddress -InterfaceAlias "Ethernet"


IPAddress         : fe80::caf0:4920:dd19:721c%5
InterfaceIndex    : 5
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 192.168.56.1
InterfaceIndex    : 5
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore
```
Sur ma VM:
```
kilian@kilian-VirtualBox:~$ ip addr show enp0s8
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:f1:dd:38 brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.104/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 468sec preferred_lft 468sec
    inet6 fe80::cf65:ee54:f788:35dd/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```

🌞 Tester que votre LAN + votre adressage IP est fonctionnel
```
PS C:\Windows\system32> ping 192.168.56.104

Envoi d’une requête 'Ping'  192.168.56.104 avec 32 octets de données :
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.56.104:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

🌞 Capture de ping
De mon pc:
```
PS C:\Windows\system32> ping 192.168.56.104

Envoi d’une requête 'Ping'  192.168.56.104 avec 32 octets de données :
Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.56.104:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms
```
De ma VM:
```
kilian@kilian-VirtualBox:~$ ping 192.168.56.1
PING 192.168.56.1 (192.168.56.1) 56(84) bytes of data.
64 bytes from 192.168.56.1: icmp_seq=1 ttl=128 time=0.493 ms
64 bytes from 192.168.56.1: icmp_seq=2 ttl=128 time=0.458 ms
64 bytes from 192.168.56.1: icmp_seq=3 ttl=128 time=0.567 ms
64 bytes from 192.168.56.1: icmp_seq=4 ttl=128 time=0.569 ms
^C
--- 192.168.56.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3590ms
rtt min/avg/max/mdev = 0.458/0.521/0.569/0.047 ms
```

II. Utilisation des ports

1. Animal numérique
   
🌞 Sur le PC serveur
```
kilian@kilian-VirtualBox:~$ nc -l 9999
```
🌞 Sur le PC serveur toujours
```
kilian@kilian-VirtualBox:~$ sudo ss -lnpt

 users:(("cupsd",pid=1186,fd=7))
LISTEN   0        1                  0.0.0.0:9999            0.0.0.0:* 
```

🌞 Sur le PC client
```
PS C:\Users\robre\Desktop\netcat-win32-1.12> ./nc 192.168.56.104 9999
```

🌞 Echangez-vous des messages
sur la VM serveur:
```
kilian@kilian-VirtualBox:~$ nc -l 9999
hello world
```
Sur le pc client:
```
PS C:\Users\robre\Desktop\netcat-win32-1.12> ./nc 192.168.56.104 9999
hello world
```
🌞 Utilisez une commande qui permet de voir la connexion en cours
sur le client:
```
PS C:\Users\robre\Desktop\netcat-win32-1.12> netstat -an | findstr :9999
  TCP    192.168.56.1:34678     192.168.56.104:9999    ESTABLISHED
```
sur le serveur
```
kilian@kilian-VirtualBox:~$ ss -ntp
State Recv-Q Send-Q           Local Address:Port          Peer Address:Port Process
ESTAB 0      0               192.168.56.104:9999          192.168.56.1:34678 users:(("nc",pid=6376,fd=4))
```
🌞 Faites une capture Wireshark complète d'un échange

voir le doc netcap1.pcap

III. Analyse de vos applications usuelles

1. Serveur web

🌞 Utilisez Wireshark pour capturer du trafic HTTP

voir le documment http.pcap

2. Autres services

🌞 Pour les 5 applications

navigateur connecté à un site aléatoire :
```
 PS C:\Users\robre\Desktop\netcat-win32-1.12> netstat -a -n -b | Select-String Firefox -Context 1,0
 [firefox.exe]
    TCP    192.168.1.13:35562     13.249.8.192:80        ESTABLISHED
```

steam :
```
[Steam.exe]
    TCP    127.0.0.1:27060        0.0.0.0:0              LISTENING
```

deezer :
```
PS C:\Users\robre\Desktop\netcat-win32-1.12> netstat -a -n -b | Select-String Deezer -Context 1,0
[Deezer.exe]
    TCP    192.168.1.13:35659     35.186.247.156:443     ESTABLISHED
```

Discord :
```
PS C:\Users\robre\Desktop\netcat-win32-1.12> netstat -a -n -b | Select-String Discord -Context 1,0
Discord.exe
    TCP    192.168.1.13:35096     162.159.135.234:443    ESTABLISHED
```