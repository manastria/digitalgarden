---
{"dg-publish":true,"permalink":"/git/affichage-des-commits-en-cli/"}
---


# Affichage des commits en CLI

Ajouter l’alias suivant permet d’afficher en ligne de commande le graph des commits : 

```console
git config --global alias.lg "log --oneline --graph --decorate --all"
```