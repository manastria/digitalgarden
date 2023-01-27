---
{"dg-publish":true,"permalink":"/windows/ssh/windows-installation-open-ssh/","title":"Windows - Installation OpenSSH"}
---

# Windows - Installation OpenSSH

## Installer OpenSSH avec les « Paramètres Windows »

Les deux composants OpenSSH peuvent être installés à l’aide des Paramètres Windows sur les appareils Windows Server 2019 et Windows 10.

Pour installer les composants OpenSSH :

1. Ouvrez **Paramètres**, sélectionnez **Applications** > **Applications et fonctionnalités**, puis **Fonctionnalités facultatives**.
2. Parcourez la liste pour voir si OpenSSH est déjà installé. Si ce n’est pas le cas, sélectionnez **Ajouter une fonctionnalité** en haut de la page, puis :
3. Recherchez **OpenSSH Client** et cliquez sur **Installer**.

Une fois l’installation terminée, revenez à **Applications** > **Applications et fonctionnalités et Fonctionnalités facultatives**. Vous devriez voir OpenSSH dans la liste.

> [!INFO] L’installation d’OpenSSH Server crée et active une règle de pare-feu appelée OpenSSH-Server-In-TCP. Cela autorise le trafic SSH entrant sur le port 22. Si cette règle n’est pas activée et que ce port n’est pas ouvert, les connexions sont refusées ou réinitialisées.