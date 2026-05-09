# Marketplace Claude Code — Structure initiale

## Contexte

Repo public `claude-skills` (GitHub : Mickaël FRANCOIS). Objectif : créer un marketplace Claude Code personnel distribué via git, utilisable avec `/plugin marketplace add mickael-francois/claude-skills`.

## Approche retenue

**Mono-repo** : tous les plugins vivent dans ce même repo sous `plugins/`. Le fichier catalogue `.claude-plugin/marketplace.json` les référence par chemin relatif (`./plugins/<nom>`).

## Structure de répertoires

```
claude-skills/
├── .claude-plugin/
│   └── marketplace.json      ← catalogue du marketplace
└── plugins/                  ← répertoire des futurs plugins (vide initialement)
```

## Contenu de marketplace.json

```json
{
  "name": "mickael-francois-skills",
  "description": "Personal Claude Code plugins for .NET/C#/Blazor development",
  "owner": {
    "name": "Mickaël FRANCOIS",
    "email": "mickael@francois.ovh"
  },
  "metadata": {
    "pluginRoot": "./plugins"
  },
  "plugins": []
}
```

## Comment ajouter un plugin plus tard

1. Créer `plugins/<nom-plugin>/.claude-plugin/plugin.json`
2. Ajouter les fichiers du plugin (skills, agents, hooks…)
3. Ajouter l'entrée dans `marketplace.json` : `{ "name": "<nom>", "source": "./<nom-plugin>" }`

## Distribution

Les utilisateurs ajoutent le marketplace avec :
```
/plugin marketplace add mickael-francois/claude-skills
```
