---
{"dg-publish":true,"permalink":"/windows/ssh/windows-ssh-deploiement-de-la-cle-publique/","title":"Windows SSH - Déploiement de la clé publique"}
---

# Windows SSH - Déploiement de la clé publique

À la date d’aujourd’hui (fin 2022), la commande `ssh-copy-id` n’existe pas dans la version Microsoft OpenSSH.

Il faudra copier le contenu de la clé publique dans le fichier `~/.ssh/authorized_keys` du serveur à l’aide de la commande `ssh`.

Ici, deux méthodes pour y arriver : 
- La métode simple si vous êtes déjà initié ;
- La méthode complète si vous avez peur de ne pas y arriver ;

## Méthode simple

```powershell
> type $env:USERPROFILE\.ssh\id_rsa.pub | ssh {IP-ADDRESS-OR-FQDN} "cat >> .ssh/authorized_keys"
```

## Méthode complète
Exécutez l’une des commandes suivantes, dans une fenêtre PowerShell locale en remplaçant le nom de l’utilisateur et de l’hôte comme il convient, pour copier votre clé publique locale sur l’hôte SSH.

```powershell
$USER_AT_HOST="your-user-name-on-host@hostname"

$PUBKEYPATH="$HOME\.ssh\id_rsa.pub"

-- OU --

$PUBKEYPATH="$HOME\.ssh\id\_ed25519.pub"
```

```powershell
$pubKey=(Get-Content "$PUBKEYPATH" | Out-String); ssh "$USER_AT_HOST" "mkdir -p ~/.ssh && chmod 700 ~/.ssh && echo '${pubKey}' >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

Cette dernière commande se connecte au serveur pour y copier la clé publique. Il faudra donc utiliser une connexion avec un mot de passe.

Vous devriez maintenant pouvoir vous connecter avec la clé et non plus le mot de passe.
