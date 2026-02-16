# GitHub Workflow Skill

Ein Claude Code Skill für Issue-basierte Entwicklung mit GitHub Flow.

## Features

- **Automatischer Session-Start**: Erkennt GitHub-Repos und lädt offene Issues
- **Issue-Auswahl**: Präsentiert Issues sortiert nach Priorität zur Auswahl
- **Branch-Management**: Erstellt Feature-Branches pro Issue (`feature/123-beschreibung`)
- **Pull Requests**: Einheitliches PR-Format mit automatischer Issue-Verlinkung
- **Issue-Templates**: Konsistente Templates für neue Issues (Standard, Bug, Feature)

## Installation

```bash
git clone https://github.com/martinvidec/github-workflow-skill.git ~/.claude/skills/github-workflow-skill
```

Oder in der Projekt-`.claude/settings.json`:
```json
{
  "skills": [
    "github.com/martinvidec/github-workflow-skill"
  ]
}
```

## Workflow

### 1. Session starten

Beim Start in einem GitHub-Repo lädt der Skill automatisch offene Issues und präsentiert sie zur Auswahl:

- Issues mit `priority:high` oder `urgent` Label zuerst
- Zugewiesene Issues
- Nach Alter sortiert

### 2. An Issue arbeiten

Nach Auswahl eines Issues:
- Branch wird erstellt: `feature/<nummer>-<beschreibung>`
- Issue-Details werden geladen
- Commits referenzieren das Issue

### 3. Pull Request erstellen

Bei Fertigstellung wird ein PR mit einheitlichem Format erstellt:
- Summary
- `Closes #<nummer>` für automatisches Schließen
- Changes-Liste
- Test Plan

## Konventionen

| Element | Format | Beispiel |
|---------|--------|----------|
| Feature-Branch | `feature/<nr>-<beschreibung>` | `feature/42-user-login` |
| Bugfix-Branch | `fix/<nr>-<beschreibung>` | `fix/99-null-pointer` |
| Commit | Conventional Commits | `feat: Add login (#42)` |

## Issue-Templates

Der Skill enthält Templates für:
- **Standard Issue**: Beschreibung, Motivation, Akzeptanzkriterien
- **Bug Report**: Reproduktionsschritte, erwartetes/tatsächliches Verhalten
- **Feature Request**: Use Case, vorgeschlagene Lösung, Alternativen

## Voraussetzungen

- [GitHub CLI](https://cli.github.com/) (`gh`) installiert und authentifiziert
- Git konfiguriert

## Lizenz

MIT
