# Portfolio Summary

## User Profile

<!-- This section is populated by /setup -->

**Name:** [Not configured]
**Role:** [Not configured]
**Lines of Business:** [Not configured]

### Key OKRs

<!-- Organizational objectives this portfolio supports -->

1. [Run /setup to configure]

### Preferences

- **Communication Style:** [concise|detailed]
- **Health Weights:** Default

---

## Programs

<!-- Program inventory - updated by /setup and /newprogram -->

<!-- Use [[program-slug|Display Name]] wikilinks in the Program column for Obsidian navigation -->

| Program | Slug | Function | Owner | Cadence | Health |
|---------|------|----------|-------|---------|--------|
| [None configured] | - | - | - | - | - |

---

## Portfolio Health Summary

<!-- Auto-updated by /gsd and /portfolio -->

**Last Updated:** [Never]

| Health | Count | Programs |
|--------|-------|----------|
| 🟢 Green | 0 | - |
| 🟡 Yellow | 0 | - |
| 🔴 Red | 0 | - |

---

## Obsidian Dashboard

> The following sections render as live dashboards in Obsidian with the Dataview plugin.

### Programs Overview (Dataview)

```dataview
TABLE health, owner, meeting_cadence AS "Cadence", last_updated AS "Updated"
FROM "programs"
SORT number ASC
```

### Recent Decisions (Dataview)

```dataview
TABLE program, date, made_by
FROM "decisions"
WHERE id != null
SORT date DESC
LIMIT 10
```

### Upcoming Revisit Dates (Dataview)

```dataview
TABLE program, title, revisit_date
FROM "decisions"
WHERE revisit_date != null AND revisit_date >= date(today)
SORT revisit_date ASC
```

---

## Quick Reference

### Available Commands

| Command | Purpose |
|---------|---------|
| `/gsd` | Start session |
| `/brief [program]` | Pre-meeting prep |
| `/debrief [program]` | Post-meeting capture |
| `/board` | Portfolio board |
| `/portfolio` | Portfolio review with executive summary |

### Getting Started

Run `/setup` to configure your portfolio.

---

*Portfolio Summary - GSD Template*
