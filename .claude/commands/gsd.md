# GSD Session Start

Begin a GSD session with a portfolio overview and surface items needing attention.

## Instructions

### 1. Establish Context

- Note the current date and day of week
- Read `state/portfolio-summary.md` to get user profile
- Read all program files from `programs/` directory
- List files in `decisions/` and read decisions from the last 7 days (by `date` in frontmatter)
- Read `state/action-items.md`

### 2. Calculate Health

For each program, calculate health score from:

| Factor | Weight | Green (1.0) | Yellow (0.5) | Red (0.0) |
|--------|--------|-------------|--------------|-----------|
| Milestone Progress | 30% | On track | <2 week slip | >2 week slip |
| Open High-Impact Risks | 25% | 0 open | 1-2 open | 3+ open |
| Days Since Update | 20% | <7 days | 7-14 days | >14 days |
| Blockers Awaiting Decision | 15% | 0 pending | 1 pending | 2+ pending |
| Dependency Health | 10% | All resolved | Some pending | Any blocked |

Final: >= 0.7 → 🟢 Green, >= 0.4 → 🟡 Yellow, < 0.4 → 🔴 Red

If `health_override` is set, use that instead but note it.

### 3. Update Portfolio Summary

Update `state/portfolio-summary.md` with freshly calculated values:
- Overwrite the **Portfolio Health Summary** table with the current health distribution (Green/Yellow/Red counts and program names)
- Set `Last Updated` to today's date
- Update the **Health** column in the **Programs** table to match the freshly calculated health for each program

### 4. Identify Items Needing Attention

- Programs not updated in 7+ days
- Overdue milestones
- Open decisions pending
- High-impact risks without recent updates
- Action items past their due date

### 5. Identify Upcoming Items

- Milestones in next 7 days
- Meetings scheduled (based on cadence and current day)

### 6. Generate Output

Format:
```
Good [morning/afternoon], [Name]. It's [Day], [Full Date].

**Portfolio Health:**
🟢 X programs on track | 🟡 X need attention | 🔴 X critical

**Needs Attention:**
- [#] [Program]: [Issue] ([days] days)
- ...

**Overdue Action Items ([count]):**
- [ID]: [Action] ([Program], assigned to [Owner], due [Date])
- ...
(Omit this section entirely if no action items are overdue)

**Upcoming This Week:**
- [Day]: [Milestone] ([#] [Program])
- ...

**Open Decisions ([count]):**
- [#] [Program]: [Decision needed]
- ...

**Today's Likely Meetings:**
- [#] [Program] (based on [cadence])
- ...

What would you like to focus on?
```

### 7. Session Logging

Create or append to `sessions/[YYYY-MM-DD].md` with:
- Session start time
- Portfolio health snapshot
- Items surfaced

## Notes

- If no programs exist, prompt user to run `/setup` first
- Greet appropriately based on time of day (morning/afternoon/evening)
- Be concise - this is a quick status, not a deep dive
- Offer natural next steps based on what needs attention
