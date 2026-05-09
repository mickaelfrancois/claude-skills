# claude-skills

Marketplace personnel de plugins [Claude Code](https://claude.ai/code) pour le développement .NET / C# / Blazor.

## Installer le marketplace

```
/plugin marketplace add mickaelfrancois/claude-skills
```

---

## Plugins disponibles

### `dotnet-essentials`

Skills essentiels pour le développement .NET / C# / Blazor.

**Installer le plugin :**

```
/plugin install dotnet-essentials@mickael-francois-skills
```

**Skills inclus :**

| Skill | Description |
|---|---|
| `changelog` | Génère une entrée CHANGELOG.md depuis le dernier tag git, crée le commit et le tag de release |
| `work-guidelines` | Règles de workflow git à appliquer en début de session (branche feature obligatoire, squash en fin de tâche) |

**Utiliser un skill :**

```
/dotnet-essentials:changelog
/dotnet-essentials:work-guidelines
```

---

## Structure du repo

```
claude-skills/
├── .claude-plugin/
│   └── marketplace.json       ← catalogue du marketplace
└── plugins/
    └── dotnet-essentials/
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/
            ├── changelog/
            │   └── SKILL.md
            └── work-guidelines/
                └── SKILL.md
```

## Mettre à jour le marketplace

```
/plugin marketplace update mickael-francois-skills
```
