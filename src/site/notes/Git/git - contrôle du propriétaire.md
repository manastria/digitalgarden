---
{"dg-publish":true,"permalink":"/git/git-controle-du-proprietaire/","title":"Git – Contrôle du propriétaire du dépôt local"}
---

# Git – Contrôle du propriétaire du dépôt local

Le système de gestion de versions Git fonctionne avec un dossier `.git` situé dans votre projet. Si git ne le trouve pas, il remonte l’arborescence pour en trouver un.

Or, avec ce système, Git pouvait de manière non intentionnel manipuler le dépôt de quelqu’un d’autre.

Pour éviter cela, dès que Git détecte que l'utilisateur n'est pas propriétaire du dossier, il s’arrête et il affiche le message d'erreur `fatal: unsafe repository ('C:/projets/mon-projet' is owned by someone else)`.

Si votre ordinateur n'est pas partagé avec un autre utilisateur, et que vous êtes sûr de vous, vous pouvez suivre la consigne donnée par le client Git et ajouter le répertoire `C:/projets/mon-projet` à la liste des répertoires ignorés.

```
git config --global --add safe.directory C:/projets/mon-projet
```

Depuis la version 2.35.3, la vérification du propriétaire du répertoire peut être désactivée. Il faut que vous soyez sûr de vous, car cela ajoute une grosse vulnérabilité au niveau de la sécurité. Il faut également s'assurer d'être le seul utilisateur de l'ordinateur. En utilisant le caractère `*`, on indique avec la même commande que tous les répertoires sont ignorés lors de la vérification.

```
git config --global --add safe.directory '*'
```