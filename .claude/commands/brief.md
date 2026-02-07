# GSD Brief

Pre-meeting preparation for a program check-in.

## Arguments

- `$ARGUMENTS` - The program slug (e.g., "marketing", "customer-acme")

## Instructions

### 1. Load Program

Read the program file from `programs/$ARGUMENTS.md`

If the file doesn't exist:
```
Program "$ARGUMENTS" not found.

Available programs:
[list program slugs from programs/ directory]

Usage: /brief [program-slug]
```

### 2. Compile Current State

Extract from the program file:
- Overall health (calculated or overridden)
- Health factor breakdown
- Active initiatives with stage, progress, status
- Recent updates (last 2-3 entries)
- Open risks with impact/likelihood/status
- Pending dependencies
- Open questions for leadership
- Action items assigned to program team (from `state/action-items.md`)

### 3. Calculate Health Breakdown

Show each factor's contribution:
- Milestone progress: 🟢/🟡/🔴
- Open risks: 🟢/🟡/🔴
- Last updated: 🟢/🟡/🔴 ([X] days ago)
- Pending decisions: 🟢/🟡/🔴
- Dependencies: 🟢/🟡/🔴

### 4. Generate Suggested Questions

Based on the program state, suggest 3-5 questions:
- For initiatives that are yellow/red: Ask about blockers, mitigation, timeline impact
- For risks without recent updates: Ask for current status
- For dependencies pending resolution: Ask about progress and timeline
- For milestones approaching: Ask about confidence level
- For stale updates: Ask what's happened since last update

### 5. Output Format

```
## Brief: [Program Name]
**Prepared:** [Date], [Time]

### Health: [emoji] [Color]
- Milestone progress: [emoji] [Status]
- Open risks: [emoji] [Count] [high-impact]
- Last updated: [emoji] [X] days ago
- Pending decisions: [emoji] [Count]
- Dependencies: [emoji] [Status]

### Active Initiatives

| Initiative | Stage | Progress | Status |
|------------|-------|----------|--------|
| [Name] | [Stage] | [X]% | [emoji] [Status] |

### Recent Updates (from [Date])
- [Update item]
- [Update item]

### Open Risks
1. **[Risk name]** ([Impact]/[Likelihood])
   - Mitigation: [Mitigation plan]
   - Status: [Status]

### Pending Dependencies
| Dependency | Blocked By | Status |
|------------|------------|--------|

### Open Questions from Team
- [Question]

### Open Action Items for This Team
| Action | Owner | Due |
|--------|-------|-----|

### Suggested Questions for This Meeting

1. "[Question based on state analysis]"
2. "[Question based on state analysis]"
3. "[Question based on state analysis]"

---
Ready for your check-in. Run `/debrief $ARGUMENTS` after the meeting.
```

## Notes

- Focus on items that need discussion, not comprehensive status
- Suggested questions should be specific and actionable
- If program is all green with no issues, note that explicitly and suggest forward-looking questions
- Include the debrief reminder at the end
