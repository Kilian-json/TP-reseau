YBOOST TUTO Active Directory

Partie 1 : Setup

1. Créer un nouvel utilisateur dans le domaine, je veux que vous me détailler comment vous avez fait.
![alt text](<Capture d'écran 2024-10-30 115137.png>)

J'ai ouvert "Windows Administrative Tools" puis "Active Directory Users and Computers"

![alt text](<Capture d'écran 2024-10-30 120351.png>)

Ensuite j'ai ouvert "yboost.local" j'ai fait un clique droit sur "users" pour je suis allé dans "New" puis "User".

![alt text](<Capture d'écran 2024-10-30 120942.png>)

J'ai écris ceci dans l'onglet de nouvel utilisateur.

![alt text](<Capture d'écran 2024-10-30 121306.png>)

Je lui ai ensuite attribué un mot de passe.

2. Donnez moi aussi une commande powershell pour créer un 2eme utilisateur
```
New-ADUser -Name "NomUtilisateur" -GivenName "Prénom" -Surname "Nom" -SamAccountName "NomUtilisateur" -UserPrincipalName "NomUtilisateur@domaine.com" -Path "CN=Users,DC=exemple,DC=com" -AccountPassword (Read-Host -AsSecureString "Entrez le mot de passe") -Enabled $true
```

3. Joignez le PC au domaine



4. Désactiver le compte par défaut que vous avez créer lors du setup du PC



5. Faites moi le rendu de la GPO