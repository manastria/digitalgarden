---
{"dg-publish":true,"permalink":"/vscode/vs-code-configuration-markdown/","title":"VS Code - configuration markdown"}
---


# VS Code - configuration markdown


Voici la configuration que j’utilise dans les projets qui contiennent des fichiers Markdown. Ces fichiers se situent dans le répertoire `.vscode` du projet.

Le fichier `extensions.json` permet de proposer une liste d’extensions à installer pour le *workspace* :

```json
{
    "recommendations": [
        "davidanson.vscode-markdownlint",
        "mushan.vscode-paste-image",
        "hediet.vscode-drawio",
        "bierner.markdown-emoji",
        "ms-vscode.wordcount",
        "jerriepelser.copy-markdown-as-html",
        "yzhang.markdown-all-in-one",
        "jjaakko.markdown-kbd",
        "bierner.markdown-mermaid",
        "takumii.markdowntable",
        "editorconfig.editorconfig",
        "esbenp.prettier-vscode",
        "d3v.pastespecial"
    ]
}
```

Le fichier `settings.json` permet de mettre en place une configuration spécifique pour le *worksapce* :

```json
{
    "markdownlint.config": {
        "MD013": false
    },
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "files.exclude": {
        "**/.obsidian": true,
        "**/.obsidian.mobile": true
    }
}
```

### Explications
- Le fichier commence par désactiver la règle [MD013](https://github.com/markdownlint/markdownlint/blob/main/docs/RULES.md) de
[markdownlint](https://github.com/markdownlint/markdownlint) qui est un outil qui vérifie la syntaxe Markdown.
- `editor.defaultFormatter` :
[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) est le formateur par défaut.
- `editor.formatOnSave` :
On formate automatiquement le fichier lors de la sauvegarde
- `files.exclude` :
Liste des répertoires excluent de VS Code.

## Configuration généralisé des éditeur de texte
De nombreux éditeurs de texte supporte le projet [[editorconfig\|editorconfig]]. Le fichier de configuration ci-dessous permet de paramétrer mes fichiers Markdown.

Le fichier `.editorconfig` situé à la racine du *workspace* :

```editorconfig
# EditorConfig is awesome: https://EditorConfig.org

# top-most EditorConfig file
root = true

[*]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = false
insert_final_newline = false

[*.md]
trim_trailing_whitespace = true
indent_style = space
insert_final_newline = true
```

Ce fichier fonctionne avec le plugin [[vscode/plugins/EditorConfig for VS Code\|EditorConfig for VS Code]].
