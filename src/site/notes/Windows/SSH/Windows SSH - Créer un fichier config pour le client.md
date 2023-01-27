---
{"dg-publish":true,"permalink":"/windows/ssh/windows-ssh-creer-un-fichier-config-pour-le-client/","title":"Windows SSH - Créer un fichier config pour le client"}
---

# Windows SSH - Créer un fichier config pour le client

### Création du fichier
```
# Create the config file with Powershell
New-Item -Path $HOME\.ssh\config -ItemType File
```
### Ouverture du fichier avec Notepad
```
# Open config File with Notepad
C:\WINDOWS\System32\notepad.exe $HOME\.ssh\config
```
### Ouverture du fichier avec VSCode
```

# or Open file with Visual Code
code $HOME\.ssh\config
```