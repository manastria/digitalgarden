---
{"dg-publish":true,"permalink":"/vscode/ssh-windows/vs-code-et-ssh-windows/","title":"VS Code et SSH windows"}
---

# VS Code et SSH windows


# Utilisation de VS Code SSH sous Windows

## Architecture

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_41b8958c53ffe2bc.png)

## Installation d’OpenSSH

Voir : [[Windows/SSH/Windows - Installation OpenSSH\|Windows - Installation OpenSSH]]

## Démarrage rapide : Utilisation des clés SSH

Pour configurer l’authentification basée sur une clé SSH pour votre hôte distant. Nous allons d’abord créer une paire de clés, puis copier la clé publique sur l’hôte.

### Créer votre paire de clés SSH locale

Vérifiez si vous avez déjà une clé SSH sur votre machine locale. Elle se trouve généralement dans `~/.ssh/id_rsa.pub` sous macOS/Linux, et dans le répertoire `.ssh` de votre dossier de profil utilisateur sous Windows (par exemple `C:\Users\your-user\.ssh\id_rsa.pub`).

Si vous n’avez pas de clé, exécutez la commande suivante dans un terminal local / PowerShell pour générer une paire de clés SSH :

```
ssh-keygen -t ed25519
```

Ou, pour générer des fichiers de clé avec l’algorithme Ed25519, exécutez la commande suivante

```
ssh-keygen -t rsa -b 4096
```

### Autorisez votre machine Windows à se connecter

Voir : [[Windows/SSH/Windows SSH - Déploiement de la clé publique\|Windows SSH - Déploiement de la clé publique]]

## Utilisation et configuration de l’agent SSH sous Windows


Voir : [[Windows/SSH/Utilisation et configuration de l’agent SSH sous Windows\|Utilisation et configuration de l’agent SSH sous Windows]]

### Ajouter une clé dans l’agent

Maintenant, chargez vos fichiers de clés dans `ssh-agent` :

```
ssh-add "$HOME\.ssh\id_ed25519"
```

Ou pour l’algorithme RSA :

```
ssh-add "$HOME\.ssh\id_rsa"
```

Après avoir terminé ces étapes, chaque fois qu’une clé privée est nécessaire pour l’authentification de ce client, ssh-agent va automatiquement récupérer la clé privée locale et la transmettre à votre client SSH.

> [!attention] Il est fortement recommandé de sauvegarder votre clé privée dans un emplacement sécurisé, puis de la supprimer du système local après l’avoir ajoutée à ssh-agent. La clé privée ne peut pas être récupérée auprès de l’agent si un algorithme fort a été utilisé, tel que Ed25519 dans cet exemple. Si vous perdez l’accès à la clé privée, vous devrez créer une nouvelle paire de clés et mettre à jour la clé publique sur tous les systèmes avec lesquels vous interagissez.

## Configuration de VSCode

### Installer l’extension

**[Install the Remote – SSH extension](vscode:extension/ms-vscode-remote.remote-ssh)**.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_890c82c16566eafc.png)

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_cc63df3eedc8e547.png) La barre d’état distant montre l’état du contexte de fonctionnement de VS Code : local ou distant.

En cliquant dessus, les commandes `Remote - SSH` apparaîtront

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_2a45ad58c28d7882.png)

### Connexion par SSH

Vous aurez remarqué un indicateur dans le coin inférieur gauche de la barre d’état. Cet indicateur vous indique dans quel contexte VS Code est exécuté (local ou distant). Cliquez sur l’indicateur pour faire apparaître une liste de commandes d’extension à distance.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_4c788c61a73060c7.png)

Choisissez la commande Remote-SSH : Connect to Host et connectez-vous à l’hôte en saisissant les informations de connexion de votre VM au format suivant : user@hostname.

Avant de vous connecter en mode distant - SSH, vous pouvez vérifier que vous êtes en mesure de vous connecter à votre VM via une invite de commande en utilisant ssh user@hostname.

Définissez l’utilisateur et le nom d’hôte dans la zone de texte des informations de connexion.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_27762eefe9551f3f.png)

VS Code va maintenant ouvrir une nouvelle fenêtre (instance). Vous verrez alors une notification indiquant que le « VS Code Server » est en train de s’initialiser sur l’hôte SSH. Une fois que le serveur VS Code est installé sur l'hôte distant, il peut exécuter des extensions et parler à votre instance locale de VS Code.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_da0924e4f52abcd8.png)

Vous saurez que vous êtes connecté à votre VM en regardant l’indicateur dans la barre d’état. Il indique le nom d’hôte de votre VM.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_55f32ece8592e33b.png)

L’extension Remote - SSH apporte également une nouvelle icône sur votre barre d’activité, et en cliquant dessus, vous ouvrirez l’explorateur Remote. Dans la liste déroulante, sélectionnez SSH Targets, où vous pouvez configurer vos connexions SSH. Par exemple, vous pouvez enregistrer les hôtes auxquels vous vous connectez le plus et y accéder à partir d’ici au lieu de saisir l’utilisateur et le nom d’hôte.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_dd20c5d930ed1c75.png)

Une fois que vous êtes connecté à votre hôte SSH, vous pouvez interagir avec des fichiers et ouvrir des dossiers sur la machine distante. Si vous ouvrez le terminal intégré (Ctrl+ù), vous verrez que vous travaillez dans un shell bash alors que vous êtes sous Windows.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_b8a830ce8fd2e05c.png)

Vous pouvez utiliser le shell bash pour parcourir le système de fichiers sur la VM. Vous pouvez également parcourir et ouvrir des dossiers sur le répertoire d’origine distant avec **Fichier** > **Ouvrir un dossier**.

![](file:///C:/Users/jpdemory/AppData/Local/Temp/lu6180ert3.tmp/lu6180erti_tmp_6fa6941645d03e8d.png)

### Terminer votre connexion SSH

Vous pouvez terminer votre session via SSH et revenir à l'exécution de VS Code localement avec **Fichier** > **Fermer la connexion à distance**.

## Voir aussi

https://www.it-connect.fr/chapitres/authentification-ssh-par-cles/

https://www.it-connect.fr/cours/comprendre-et-maitriser-ssh/

https://stackoverflow.com/a/65230314

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
