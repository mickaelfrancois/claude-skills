# Marketplace Structure Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Créer la structure minimale d'un marketplace Claude Code dans le repo `claude-skills`.

**Architecture:** Un fichier `.claude-plugin/marketplace.json` à la racine définit le catalogue. Un répertoire `plugins/` vide est prêt à accueillir les futurs plugins. Git ne trackant pas les répertoires vides, un fichier `.gitkeep` est ajouté dans `plugins/`.

**Tech Stack:** JSON (marketplace manifest), Git

---

### Task 1 : Créer le catalogue du marketplace

**Files:**
- Create: `.claude-plugin/marketplace.json`

- [ ] **Step 1 : Créer le répertoire `.claude-plugin/`**

```bash
mkdir .claude-plugin
```

- [ ] **Step 2 : Créer `marketplace.json`**

Créer `.claude-plugin/marketplace.json` avec ce contenu exact :

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

- [ ] **Step 3 : Valider la syntaxe**

```bash
claude plugin validate .
```

Résultat attendu : validation OK avec un avertissement `Marketplace has no plugins defined` (normal, les plugins viendront plus tard).

- [ ] **Step 4 : Commit**

```bash
git add .claude-plugin/marketplace.json
git commit -m "feat: add Claude Code marketplace manifest"
```

---

### Task 2 : Préparer le répertoire des plugins

**Files:**
- Create: `plugins/.gitkeep`

- [ ] **Step 1 : Créer le répertoire et le fichier de placeholder**

```bash
mkdir plugins
touch plugins/.gitkeep
```

- [ ] **Step 2 : Vérifier que git détecte le fichier**

```bash
git status
```

Résultat attendu : `plugins/.gitkeep` listé comme nouveau fichier non suivi.

- [ ] **Step 3 : Commit**

```bash
git add plugins/.gitkeep
git commit -m "chore: add plugins directory placeholder"
```

---

### Task 3 : Tester le marketplace localement

- [ ] **Step 1 : Ajouter le marketplace en local depuis Claude Code**

Dans une session Claude Code (terminal ou IDE), exécuter :

```
/plugin marketplace add .
```

Résultat attendu : marketplace `mickael-francois-skills` ajouté avec succès.

- [ ] **Step 2 : Vérifier que le marketplace est listé**

```
/plugin marketplace list
```

Résultat attendu : `mickael-francois-skills` apparaît dans la liste.

- [ ] **Step 3 : (Optionnel) Supprimer le marketplace de test local**

```
/plugin marketplace remove mickael-francois-skills
```

---

## Après implémentation

Une fois le repo pushé sur GitHub (`mickael-francois/claude-skills`), le marketplace sera disponible pour tous via :

```
/plugin marketplace add mickael-francois/claude-skills
```

Pour ajouter un plugin plus tard :
1. Créer `plugins/<nom>/.claude-plugin/plugin.json`
2. Ajouter les fichiers du plugin (skills, agents, hooks…)
3. Ajouter l'entrée dans `marketplace.json` : `{ "name": "<nom>", "source": "<nom>" }` (le `pluginRoot` ajoute automatiquement `./plugins/`)
