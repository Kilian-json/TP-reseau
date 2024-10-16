TP5 : Un ptit LAN à nous

I. Setup

☀️ Uniquement avec des commandes, prouvez-que :
```
PS C:\Users\robre> ipconfig

Carte Ethernet Ethernet :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::caf0:4920:dd19:721c%5
   Adresse IPv4. . . . . . . . . . . . . .: 10.5.1.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
```


je ping mes 3 VM avec mon pc:
```
PS C:\Users\robre> ping 10.5.1.11

Envoi d’une requête 'Ping'  10.5.1.11 avec 32 octets de données :
Réponse de 10.5.1.11 : octets=32 temps=1 ms TTL=64
Réponse de 10.5.1.11 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.11 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.11 : octets=32 temps<1ms TTL=64

PS C:\Users\robre> ping 10.5.1.12

Envoi d’une requête 'Ping'  10.5.1.12 avec 32 octets de données :
Réponse de 10.5.1.12 : octets=32 temps=1 ms TTL=64
Réponse de 10.5.1.12 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.12 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.12 : octets=32 temps<1ms TTL=64

PS C:\Users\robre> ping 10.5.1.254

Envoi d’une requête 'Ping'  10.5.1.254 avec 32 octets de données :
Réponse de 10.5.1.254 : octets=32 temps=1 ms TTL=64
Réponse de 10.5.1.254 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.254 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.254 : octets=32 temps<1ms TTL=64
```

1. Accès internet routeur

☀️ Déjà, prouvez que le routeur a un accès internet
```
[kilian@routeur ~]$ ping www.ynov.com
PING www.ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=47 time=140 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=47 time=35.1 ms
```

☀️ Activez le routage
```
[kilian@routeur ~]$ sudo firewall-cmd --add-masquerade --permanent
[sudo] password for kilian:
success

[kilian@routeur ~]$ sudo firewall-cmd --reload
success
```

☀️ Prouvez que les clients ont un accès internet
```
[kilian@client2 ~]$ ping www.ynov.com
PING www.ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=46 time=37.7 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=2 ttl=46 time=108 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=3 ttl=46 time=54.8 ms
```

☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau
```
[kilian@client2 ~]$ sudo cat /etc/sysconfig/network-scripts/ifcfg-enp0s3
DEVICE=enp0s3
NAME=lan

ONBOOT=yes
BOOTPROTO=static

IPADDR=10.5.1.12
NETMASK=255.255.255.0
GATEWAY=10.5.1.254
DNS1=1.1.1.1
```

III. Serveur SSH

☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH
```
[kilian@routeur ~]$ sudo ss -lnpt | grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=697,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=697,fd=4))
```

☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert
```
[kilian@routeur ~]$ sudo ss -npt
State        Recv-Q        Send-Q               Local Address:Port               Peer Address:Port        Process
ESTAB        0             76                      10.5.1.254:22                     10.5.1.1:55077        users:(("sshd",pid=1235,fd=4),("sshd",pid=1221,fd=4))
```

IV. Serveur DHCP

☀️ Installez et configurez un serveur DHCP sur la machine routeur.tp5.b1
```
[kilian@routeur ~]$ sudo nano /etc/dhcp/dhcpd.conf

# DHCP configuration
# specify DNS server's hostname or IP address

option domain-name-servers     1.1.1.1;
# default lease time

default-lease-time 600;
# max lease time

max-lease-time 7200;
# this DHCP server to be declared valid

authoritative;
# specify network address and subnetmask

subnet 10.5.1.0 netmask 255.255.255.0 {
    # specify the range of lease IP address
    range dynamic-bootp 10.5.1.137 10.5.1.237;
    # specify broadcast address
    option broadcast-address 10.5.1.255;
    # specify gateway
    option routers 10.5.1.254;
}
```
☀️ Créez une nouvelle machine client client3.tp5.b1
```
[kilian@client3 ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:2d:22:d8 brd ff:ff:ff:ff:ff:ff
    ☀️ inet 10.5.1.137/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 395sec preferred_lft 395sec
    inet6 fe80::a00:27ff:fe2d:22d8/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


[kilian@client3 ~]$ ping 10.5.1.254
PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=1.82 ms
64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=0.892 ms
```

☀️ Consultez le bail DHCP qui a été créé pour notre client
```
[kilian@routeur dhcpd]$ cat dhcpd.leases
lease 10.5.1.137 {
  starts 2 2024/10/15 15:56:56;
  ends 2 2024/10/15 16:06:56;
  tstp 2 2024/10/15 16:06:56;
  cltt 2 2024/10/15 15:56:56;
  binding state free;
  ☀️hardware ethernet 08:00:27:2d:22:d8;
  uid "\001\010\000'-\"\330";
}
```

☀️ Confirmez qu'il s'agit bien de la bonne adresse MAC
```
[kilian@client3 ~]$ ip a
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
   ☀️ link/ether 08:00:27:2d:22:d8 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.137/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 331sec preferred_lft 331sec
    inet6 fe80::a00:27ff:fe2d:22d8/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```