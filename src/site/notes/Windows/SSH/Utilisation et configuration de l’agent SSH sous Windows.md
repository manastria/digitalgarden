---
{"dg-publish":true,"permalink":"/windows/ssh/utilisation-et-configuration-de-l-agent-ssh-sous-windows/","title":"Utilisation et configuration de l’agent SSH sous Windows"}
---

# Utilisation et configuration de l’agent SSH sous Windows

## Utilisation et configuration de l’agent SSH sous Windows

### Définition

`ssh-agent` est l’agent d'authentification inclus dans la suite logicielle OpenSSH.

Un agent SSH stocke en mémoire les clés privées utilisées lors de l’authentification par clef publique (RSA, DSA, ECDSA) pendant toute la durée de la session. L’utilisation d’un agent, évite donc d’avoir à retaper la phrase secrète à chaque fois que l’on sollicite l’utilisation de la clé privée. L’agent se lance au début d’une session (graphique ou non) et tous les appels (fenêtres ou autres programmes) sont réalisés en tant que client du programme de l’agent SSH. Grâce à des variables d’environnement, l’agent peut être trouvé et être utilisé pour l’authentification lors de la connexion à d’autres machines en SSH.

Si vous vous connectez à un hôte SSH en utilisant une clé avec une phrase de passe, vous devez vous assurer que l’agent SSH est exécuté localement. VS Code ajoutera automatiquement votre clé à l’agent afin que vous n’ayez pas à saisir votre phrase de passe chaque fois que vous ouvrez une fenêtre VS Code distante.

### Configuration

Pour vérifier que l’agent fonctionne et est accessible depuis l’environnement de VS Code, exécutez `ssh-add -l` dans le terminal d’une fenêtre VS Code locale. Vous devriez voir une liste des clés de l’agent (ou un message indiquant qu’il n’a pas de clés). Si l’agent n’est pas en cours d’exécution, suivez ces instructions pour le démarrer. **Après avoir démarré l’agent, assurez-vous de redémarrer VS Code**.

Rappelez-vous que les fichiers de clés privées sont l’équivalent d’un mot de passe et que vous devez les protéger de la même manière que votre mot de passe. Pour vous aider, utilisez ssh-agent pour stocker en toute sécurité les clés privées dans un contexte de sécurité Windows associé à votre connexion Windows. Pour ce faire, démarrez le service ssh-agent en tant qu’administrateur et utilisez ssh-add pour stocker la clé privée.

Par défaut, le service ssh-agent est désactivé. Configurez-le afin d'être démarré manuellement.

Assurez-vous que vous travaillez en tant qu'administrateur.

```
Get-Service ssh-agent | Set-Service -StartupType Manual
```

## Démarrer le service

```
Start-Service ssh-agent
```

## Vérifier que le service est bien démarré

Ceci devrait retourner le statut "Running".

```
Get-Service ssh-agent
```


