# dotnet-essentials Plugin — Design

## Contexte

Plugin Claude Code personnel pour le développement .NET/C#/Blazor, hébergé dans le marketplace `mickael-francois-skills`.

## Structure

```
plugins/dotnet-essentials/
├── .claude-plugin/
│   └── plugin.json
└── skills/
    └── .gitkeep
```

## plugin.json

```json
{
  "name": "dotnet-essentials",
  "description": "Essential skills for .NET/C#/Blazor development",
  "version": "0.1.0"
}
```

## Entrée dans marketplace.json

```json
{
  "name": "dotnet-essentials",
  "source": "dotnet-essentials",
  "description": "Essential skills for .NET/C#/Blazor development"
}
```

Le champ `source` est résolu par le `metadata.pluginRoot: "./plugins"` du marketplace, ce qui donne `./plugins/dotnet-essentials`.

## Skills prévus (à ajouter manuellement)

- Workflow : commit avant démarrage, squash en fin de tâche (2 skills existants)
- Code review C# (à créer)
- Unit tests C# (à créer)

## Installation

Une fois le repo pushé :
```
/plugin marketplace add mickael-francois/claude-skills
/plugin install dotnet-essentials@mickael-francois-skills
```
