# dotnet-essentials Plugin Skeleton Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Créer le squelette du plugin `dotnet-essentials` dans le marketplace `claude-skills` et l'enregistrer dans le catalogue.

**Architecture:** Le plugin vit dans `plugins/dotnet-essentials/` avec un manifeste `plugin.json` et un répertoire `skills/` vide (`.gitkeep`). Le marketplace `marketplace.json` est mis à jour pour référencer ce plugin via son nom (résolu grâce au `pluginRoot`).

**Tech Stack:** JSON, Git

---

### Task 1 : Créer la structure du plugin

**Files:**
- Create: `plugins/dotnet-essentials/.claude-plugin/plugin.json`
- Create: `plugins/dotnet-essentials/skills/.gitkeep`

- [ ] **Step 1 : Créer les répertoires**

```bash
mkdir -p plugins/dotnet-essentials/.claude-plugin
mkdir -p plugins/dotnet-essentials/skills
```

- [ ] **Step 2 : Créer `plugin.json`**

Créer `plugins/dotnet-essentials/.claude-plugin/plugin.json` avec ce contenu exact :

```json
{
  "name": "dotnet-essentials",
  "description": "Essential skills for .NET/C#/Blazor development",
  "version": "0.1.0"
}
```

- [ ] **Step 3 : Créer le placeholder du répertoire skills**

```bash
touch plugins/dotnet-essentials/skills/.gitkeep
```

- [ ] **Step 4 : Vérifier la structure**

```bash
find plugins/dotnet-essentials -type f
```

Résultat attendu :
```
plugins/dotnet-essentials/.claude-plugin/plugin.json
plugins/dotnet-essentials/skills/.gitkeep
```

- [ ] **Step 5 : Commit**

```bash
git add plugins/dotnet-essentials/
git commit -m "feat: add dotnet-essentials plugin skeleton"
```

---

### Task 2 : Enregistrer le plugin dans le marketplace

**Files:**
- Modify: `.claude-plugin/marketplace.json`

- [ ] **Step 1 : Lire le contenu actuel de `marketplace.json`**

Lire `.claude-plugin/marketplace.json`. Il contient actuellement :

```json
{
  "name": "mickael-francois-skills",
  "description": "Personal Claude Code plugins for .NET/C#/Blazor development",
  "owner": {
    "name": "Mickaël FRANCOIS"
  },
  "metadata": {
    "pluginRoot": "./plugins"
  },
  "plugins": []
}
```

- [ ] **Step 2 : Mettre à jour `plugins` pour y ajouter le plugin**

Remplacer `"plugins": []` par :

```json
"plugins": [
  {
    "name": "dotnet-essentials",
    "source": "dotnet-essentials",
    "description": "Essential skills for .NET/C#/Blazor development"
  }
]
```

Le fichier complet doit être :

```json
{
  "name": "mickael-francois-skills",
  "description": "Personal Claude Code plugins for .NET/C#/Blazor development",
  "owner": {
    "name": "Mickaël FRANCOIS"
  },
  "metadata": {
    "pluginRoot": "./plugins"
  },
  "plugins": [
    {
      "name": "dotnet-essentials",
      "source": "dotnet-essentials",
      "description": "Essential skills for .NET/C#/Blazor development"
    }
  ]
}
```

- [ ] **Step 3 : Valider**

```bash
claude plugin validate .
```

Résultat attendu : validation OK, aucune erreur, avertissement éventuel sur skills vides.

- [ ] **Step 4 : Commit**

```bash
git add .claude-plugin/marketplace.json
git commit -m "feat: register dotnet-essentials in marketplace"
```

---

## Après implémentation

Pour ajouter une skill dans le plugin, créer un fichier `plugins/dotnet-essentials/skills/<nom>/SKILL.md` avec ce frontmatter minimal :

```markdown
---
description: <description courte>
---

<contenu de la skill>
```

Puis incrémenter `version` dans `plugin.json` pour que les utilisateurs reçoivent la mise à jour.
