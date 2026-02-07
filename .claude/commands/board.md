# GSD Board

Display a visual portfolio board showing all initiatives across programs.

## Instructions

### 1. Load All Programs

Read all program files from `programs/` directory.
Extract all initiatives with their metadata.

### 2. Compile Initiative Data

For each initiative across all programs, extract:
- Initiative name
- Parent program name and slug
- Stage (Backlog, Evaluation, Planning, In Flight, Complete)
- Progress percentage
- Status (On track, At risk, Blocked)
- Target completion date
- Days since program was last updated

### 3. Calculate Visual Indicators

- **Health color:** Based on status
  - On track → 🟢 Green
  - At risk → 🟡 Yellow
  - Blocked → 🔴 Red
- **Staleness warning:** If program not updated in 7+ days, flag it
- **Overdue indicator:** If target date is past and not complete

### 4. Generate Board Output

Create a text-based kanban board:

```
# Portfolio Board
**Generated:** [Date, Time]

## Summary
Total Initiatives: [X] | 🟢 [X] On Track | 🟡 [X] At Risk | 🔴 [X] Blocked

---

## Backlog
┌─────────────────────────────────┐
│ 🟢 [Initiative Name]            │
│    [Program Name]               │
│    Target: [Date]               │
└─────────────────────────────────┘

## Evaluation
[Cards...]

## Planning
┌─────────────────────────────────┐
│ 🟡 [Initiative Name]            │
│    [Program Name]               │
│    ████████░░░░░ 35%            │
│    Target: [Date]               │
│    ⚠️ 10 days since update       │
└─────────────────────────────────┘

## In Flight
┌─────────────────────────────────┐
│ 🟢 [Initiative Name]            │
│    [Program Name]               │
│    ████████████░░ 75%           │
│    Target: [Date]               │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│ 🔴 [Initiative Name]            │
│    [Program Name]               │
│    ██████░░░░░░░░ 40%           │
│    Target: [Date] ⏰ OVERDUE     │
└─────────────────────────────────┘

## Complete (Last 30 Days)
┌─────────────────────────────────┐
│ ✅ [Initiative Name]            │
│    [Program Name]               │
│    Completed: [Date]            │
└─────────────────────────────────┘

---

**Filter options:** Ask me to filter by program, line of business, or health status.
**Details:** Ask about any initiative for more information.
```

### 5. Progress Bar Rendering

Use block characters for progress bars:
- `█` for filled portions
- `░` for empty portions
- 14 characters total width
- Calculate: filled = round(progress / 100 * 14)

Examples:
- 0%: `░░░░░░░░░░░░░░`
- 25%: `████░░░░░░░░░░`
- 50%: `███████░░░░░░░`
- 75%: `███████████░░░`
- 100%: `██████████████`

### 6. Filtering Support

If the user asks for filtered views:
- **By program:** Show only initiatives from specified program
- **By line of business:** Show initiatives from programs tagged with that LoB
- **By health:** Show only green/yellow/red items
- **By stage:** Show only items in a specific stage

### 7. Empty States

If no initiatives exist:
```
# Portfolio Board

No initiatives found.

To add initiatives:
1. Run `/newprogram` to add a program, or
2. Edit an existing program file to add initiatives

See `templates/program-template.md` for the initiative format.
```

If a stage is empty, show:
```
## [Stage]
(No initiatives)
```

## Notes

- Complete initiatives should only show those from the last 30 days to keep the board focused
- The board is a snapshot - remind users to run `/gsd` for a more comprehensive status
- Offer to drill into any specific initiative if the user wants more details
