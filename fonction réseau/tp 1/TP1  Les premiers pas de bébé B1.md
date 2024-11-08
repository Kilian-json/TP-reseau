I. Récolte d'informations

🌞 Adresses IP de ta machine

affiche l'adresse IP que ta machine a sur sa carte réseau WiFi
```
PS C:\Users\robre> ipconfig

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.158
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```
affiche l'adresse IP que ta machine a sur sa carte réseau ethernet

```
Carte Ethernet Ethernet :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::caf0:4920:dd19:721c%5
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
   ```

   🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...
affiche l'adresse IP de la passerelle du réseau local
   ```
PS C:\Users\robre> ipconfig /all
Carte réseau sans fil Wi-Fi :

Suffixe DNS propre à la connexion. . . :
Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
Adresse physique . . . . . . . . . . . : F4-6A-DD-2C-70-19
DHCP activé. . . . . . . . . . . . . . : Oui
Configuration automatique activée. . . : Oui
Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18(préféré)
Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.158(préféré)
Masque de sous-réseau. . . . . . . . . : 255.255.240.0
Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:57:34
Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:57:35
🌞 Passerelle par défaut. . . . . . . . . : 10.33.79.254
Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
IAID DHCPv6 . . . . . . . . . . . : 183790301
DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-86-56-EE-F4-6A-DD-2C-70-19
Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                    1.1.1.1
NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ```
affiche l'adresse IP du serveur DNS que connaît ton PC
```
Carte réseau sans fil Wi-Fi :

Suffixe DNS propre à la connexion. . . :
Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
Adresse physique . . . . . . . . . . . : F4-6A-DD-2C-70-19
DHCP activé. . . . . . . . . . . . . . : Oui
Configuration automatique activée. . . : Oui
Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18(préféré)
Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.158(préféré)
Masque de sous-réseau. . . . . . . . . : 255.255.240.0
Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:57:34
Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:57:35
Passerelle par défaut. . . . . . . . . : 10.33.79.254
Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
IAID DHCPv6 . . . . . . . . . . . : 183790301
DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-86-56-EE-F4-6A-DD-2C-70-19
🌞Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8                                  1.1.1.1
NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
affiche l'adresse IP du serveur DHCP que connaît ton PC
```
Carte réseau sans fil Wi-Fi :

Suffixe DNS propre à la connexion. . . :
Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
Adresse physique . . . . . . . . . . . : F4-6A-DD-2C-70-19
DHCP activé. . . . . . . . . . . . . . : Oui
Configuration automatique activée. . . : Oui
Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18(préféré)
Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.158(préféré)
Masque de sous-réseau. . . . . . . . . : 255.255.240.0
Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:57:34
Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:57:35
Passerelle par défaut. . . . . . . . . : 10.33.79.254
🌞Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
IAID DHCPv6 . . . . . . . . . . . : 183790301
DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-86-56-EE-F4-6A-DD-2C-70-19
Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8                                    1.1.1.1
NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine

détermine s'il exise un pare-feu actif sur votre machine
```
PS C:\Users\robre> Get-NetFirewallProfile | ft Name,Enabled
Name    Enabled
----    -------
Domain     True
Private    True
Public     True
```
si oui, je veux aussi voir une commande pour lister les règles du pare-feu
```
PS C:\Users\robre> $rules=Get-NetFirewallRule
PS C:\Users\robre> $DisplayGroups=foreach ($rule in $rules){$rule.displaygroup}
PS C:\Users\robre> $DisplayGroups | Select-Object -Unique
Découverte de réseau Wi-Fi Direct
Recherche du réseau
Assistance à distance
Gestion à distance des journaux des événements
Gestion à distance des tâches planifiées
Coordinateur de transactions distribuées
Routage et accès distant
Réseau de base
Plateforme d’appareils connectés
Partage de fichiers et d’imprimantes
Windows Peer to Peer Collaboration Foundation
Service d’inscription de nom d’ordinateur Espace de collaboration Windows
Interruption SNMP
mDNS
Optimisation de livraison
Gestion de carte à puce virtuelle TPM
Arrêt à distance
Service iSCSI
Moniteur d’événements distants
Gestion des volumes à distance
Diagnostics de réseau de base
Source réseau Microsoft Media Foundation
Gestion des périphériques Windows
Infrastructure de gestion Windows (WMI)
Journaux et alertes de performance
Gestion à distance du Pare-feu Windows Defender
Gestion à distance de Windows
Analyse de l’ordinateur virtuel
Service WLAN - Protocole de coordination Application Services Platform WFD (utilise UDP)
Affichage sans fil
Résolution des problèmes recommandée
Serveur protocole DIAL
Gestion des services à distance
Gestion à distance de Windows (Compatibilité)
Routeur AllJoyn
Service WLAN - Règles du pilote en mode noyau de WFD Services
Service Accès réseau
Partage de proximité
DiagTrack
Protocole SSTP
Service de partage réseau du Lecteur multimédia Windows
Lecteur multimédia Windows
Fonctionnalité Diffuser sur un appareil
Unités Media Center Extender
Périphériques mobiles sans fil
@{Microsoft.Getstarted_10.2204.1.0_x64__8wekyb3d8bbwe?ms-resource://Microsoft.Getstarted/Resources/AppStoreName}
Flux du portail captif
Compte professionnel ou scolaire
E-mail et comptes
Windows Defender SmartScreen
Expérience Windows Shell
Narrateur
NcsiUwpApp
Xbox Game UI
Fonctionnalités Famille Microsoft
Visionneuse web de l’application de bureau
Xbox Game Bar Plugin
Xbox TCUI
Actualités
Microsoft Family
Epson Print and Scan
Movies & TV
Votre compte
Contenu Microsoft
Écran de verrouillage par défaut de Windows
Sécurité Windows
Contacts Microsoft
Windows Feature Experience Pack
Microsoft To Do
Calculatrice Windows
Programme d'installation d'application
Terminal Windows
Xbox Identity Provider
@{MicrosoftWindows.Client.LKG_1000.22621.3880.0_x64__cw5n1h2txyewy?ms-resource://MicrosoftWindows.Client.LKG/resources/ProductPkgDisplayName}
Hub de commentaires
Astuces Microsoft
Caméra Windows
{78E1CD88-49E3-476E-B926-580E596AD309}
Hôte de l'expérience du Microsoft Store
Services de jeu
ScreenXpert
Obtenir de l'aide
GlideX
Widgets Platform Runtime
Démarrage
Windows Web Experience Pack
Microsoft Defender
MyASUS
Courrier et calendrier
Microsoft Store
Microsoft Edge WebView2 Runtime
Google Chrome
Game Bar
Microsoft 365 (Office)
MSN Météo
ARMOURY CRATE
Xbox
```

II. Utiliser le réseau

🌞 Envoie un ping vers...

toi-même !
```
PS C:\Users\robre> ping 10.33.77.158

Envoi d’une requête 'Ping'  10.33.77.158 avec 32 octets de données :
Réponse de 10.33.77.158 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.158 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.158 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.158 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.77.158:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

vers l'adresse IP 127.0.0.1
```
PS C:\Users\robre> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

🌞 On continue avec ping. Envoie un ping vers...

ta passerelle

```
PS C:\Users\robre> ping  10.33.79.254

Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
```

un(e) pote sur le réseau
```
PS C:\Users\robre> ping 10.33.78.242

Envoi d’une requête 'Ping'  10.33.78.242 avec 32 octets de données :
Réponse de 10.33.78.242 : octets=32 temps=367 ms TTL=128
Réponse de 10.33.78.242 : octets=32 temps=144 ms TTL=128
Réponse de 10.33.78.242 : octets=32 temps=158 ms TTL=128
Réponse de 10.33.78.242 : octets=32 temps=174 ms TTL=128

Statistiques Ping pour 10.33.78.242:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 144ms, Maximum = 367ms, Moyenne = 210ms
```

un site internet
```
PS C:\Users\robre> ping rog.asus.com

Envoi d’une requête 'ping' sur fp32c2.adn.thetacdn.net [152.199.16.3] avec 32 octets de données :
Réponse de 152.199.16.3 : octets=32 temps=140 ms TTL=55
Réponse de 152.199.16.3 : octets=32 temps=34 ms TTL=55
Réponse de 152.199.16.3 : octets=32 temps=18 ms TTL=55
Réponse de 152.199.16.3 : octets=32 temps=18 ms TTL=55

Statistiques Ping pour 152.199.16.3:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 18ms, Maximum = 140ms, Moyenne = 52ms
```

🌞 Faire une requête DNS à la main

```
PS C:\Users\robre> Resolve-DnsName -Name www.thinkerview.com

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
www.thinkerview.com                            AAAA   49    Answer     2a06:98c1:3120::7
www.thinkerview.com                            AAAA   49    Answer     2a06:98c1:3121::7
www.thinkerview.com                            A      300   Answer     188.114.96.7
www.thinkerview.com                            A      300   Answer     188.114.97.7
```
```
PS C:\Users\robre> Resolve-DnsName -Name www.wikileaks.org

Name                           Type   TTL   Section    NameHost
----                           ----   ---   -------    --------
www.wikileaks.org              CNAME  1008  Answer     wikileaks.org

Name       : wikileaks.org
QueryType  : A
TTL        : 1348
Section    : Answer
IP4Address : 80.81.248.21


Name       : wikileaks.org
QueryType  : A
TTL        : 1348
Section    : Answer
IP4Address : 51.159.197.136


Name                   : wikileaks.org
QueryType              : SOA
TTL                    : 1008
Section                : Authority
NameAdministrator      : root.wlinfra.org
SerialNumber           : 2022082502
TimeToZoneRefresh      : 21600
TimeToZoneFailureRetry : 3600
TimeToExpiration       : 604800
DefaultTTL             : 1800
```
```
PS C:\Users\robre> Resolve-DnsName -Name www.torproject.org

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
www.torproject.org                             AAAA   150   Answer     2a01:4f9:c010:19eb::1
www.torproject.org                             AAAA   150   Answer     2620:7:6002:0:466:39ff:fe7f:1826
www.torproject.org                             AAAA   150   Answer     2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
www.torproject.org                             AAAA   150   Answer     2a01:4f8:fff0:4f:266:37ff:feae:3bbc
www.torproject.org                             AAAA   150   Answer     2620:7:6002:0:466:39ff:fe32:e3dd
www.torproject.org                             A      150   Answer     116.202.120.165
www.torproject.org                             A      150   Answer     116.202.120.166
www.torproject.org                             A      150   Answer     204.8.99.146
www.torproject.org                             A      150   Answer     95.216.163.36
www.torproject.org                             A      150   Answer     204.8.99.144
```

III. Sniffer le réseau

🌞 J'attends dans le dépôt git de rendu un fichier ping.pcap

ouvrir pinglb.pcapng
ouvrir ping copain+ site internet.pcapng

🌞 Livrez un deuxième fichier : dns.pcap

ouvrir dns.pcapng

IV. Network scanning et adresses IP

🌞 Effectue un scan du réseau auquel tu es connecté
```
PS C:\Users\robre> nmap -sn -PR 192.168.1.13/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-10-07 10:47 Paris, Madrid (heure dÆÚtÚ)
Nmap scan report for livebox.home (192.168.1.1)
Host is up (0.0040s latency).
MAC Address: 38:B5:C9:03:5E:30 (Ingram Micro Services)
Nmap scan report for andreponey.home (192.168.1.10)
Host is up (0.0049s latency).
MAC Address: 74:56:3C:E6:F4:9A (Giga-byte Technology)
Nmap scan report for pc-de-kilian.home (192.168.1.13)
Host is up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.32 seconds
```
🌞 Changer d'adresse IP
```
PS C:\Windows\system32> New-NetIPAddress -InterfaceIndex 18 -IPAddress 192.168.1.12

IPAddress         : 192.168.1.12
InterfaceIndex    : 18
InterfaceAlias    : Wi-Fi
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 32
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Tentative
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 192.168.1.12
InterfaceIndex    : 18
InterfaceAlias    : Wi-Fi
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 32
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Invalid
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : PersistentStore
```
```
PS C:\Windows\system32> ipconfig

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . : home
   Adresse IPv6. . . . . . . . . . . . . .: 2a01:cb19:63a:4d00:5b4:8a56:a44f:193c
   Adresse IPv6 temporaire . . . . . . . .: 2a01:cb19:63a:4d00:6c3d:9a39:5358:a63
   Adresse IPv6 de liaison locale. . . . .: fe80::aa00:bad:e9de:512%18
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.1.12
   Masque de sous-réseau. . . . . . . . . : 255.255.255.255
   Passerelle par défaut. . . . . . . . . : fe80::3ab5:c9ff:fe03:5e30%18
```