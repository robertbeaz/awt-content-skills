# awt-content-skills

Content-Marketing-Orchestrator für **AWT Finanz GmbH** als Claude Code Plugin.

## Was dieser Skill kann

| Befehl | Funktion |
|--------|----------|
| `/awt-content keyword <thema>` | Keyword-Recherche + Cluster-Strategie |
| `/awt-content blog <thema>` | Vollständiger Blog-Artikel (Brief → Outline → Artikel → SEO → GEO) |
| `/awt-content newsletter <thema>` | Newsletter oder E-Mail-Sequenz erstellen |

## Installation

```bash
# 1. Dieses Plugin klonen
git clone https://github.com/robertbeaz/awt-content-skills ~/.claude/plugins/awt-content-skills

# 2. Abhängige Plugins installieren
git clone https://github.com/AgriciDaniel/claude-blog ~/.claude/plugins/claude-blog
git clone https://github.com/aaron-he-zhu/seo-geo-claude-skills ~/.claude/plugins/seo-geo-claude-skills
git clone https://github.com/coreyhaines31/marketingskills ~/.claude/plugins/marketingskills

# 3. Skill registrieren
cp -r ~/.claude/plugins/awt-content-skills/skills/awt-content ~/.claude/skills/awt-content

# 4. Markenkontext in Projektordner kopieren
mkdir -p .agents && cp ~/.claude/plugins/awt-content-skills/product-marketing-context.md .agents/product-marketing-context.md
```

Dann Claude Code neu starten — `/awt-content` ist sofort verfügbar.

## Abhängigkeiten

- [AgriciDaniel/claude-blog](https://github.com/AgriciDaniel/claude-blog) — Blog-Workflows
- [aaron-he-zhu/seo-geo-claude-skills](https://github.com/aaron-he-zhu/seo-geo-claude-skills) — SEO & GEO Optimierung
- [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) — Newsletter & E-Mail-Workflows

## Branding

Die Datei `product-marketing-context.md` enthält das vollständige Markenprofil von AWT Finanz GmbH
und wird von jedem Workflow automatisch als Kontext eingelesen.
