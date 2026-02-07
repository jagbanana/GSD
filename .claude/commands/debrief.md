# GSD Debrief

Capture meeting notes and update program state after a check-in.

## Arguments

- `$ARGUMENTS` - The program slug (e.g., "marketing", "customer-acme")

## Instructions

### 1. Load Program

Read the program file from `programs/$ARGUMENTS.md`

If the file doesn't exist, show error and list available programs.

### 2. Present Capture Template

Show the current state and prompt for updates:

```
## Debrief: [Program Name]
**Date:** [Today's Date]

Let's capture what happened in the meeting. I'll walk through each section.
You can skip any section that had no updates.

### Initiative Updates
For each active initiative, any changes to status or progress?

**[Initiative 1]** (currently: [Stage], [X]%, [Status])
> [Waiting for user input]

**[Initiative 2]** (currently: [Stage], [X]%, [Status])
> [Waiting for user input]

### Milestone Updates
Any milestones completed, delayed, or at risk?
> [Waiting for user input]

### Risk Updates
Any new risks? Changes to existing risks? Risks resolved?
> [Waiting for user input]

### Dependency Updates
Any dependencies resolved or newly blocked?
> [Waiting for user input]

### Decisions Made
Any decisions made during this meeting? (Will be logged to decision log)
> [Waiting for user input]

### Action Items
Any new action items? (Include owner and due date)
> [Waiting for user input]

### Open Discussion Notes
Anything else notable from the conversation?
> [Waiting for user input]
```

### 3. Process User Input

As the user provides updates for each section:
- Parse the information
- Confirm understanding
- Ask clarifying questions if needed

### 4. Apply Updates

Update the following files:

**Program file (`programs/$ARGUMENTS.md`):**
- Update initiative stages, progress, status
- Update milestone statuses
- Add/update/resolve risks
- Update dependency statuses
- Add entry to "Recent Updates" section with today's date
- Update `last_updated` in frontmatter

**Decision log (`state/decision-log.md`):**
- For any decisions made, create full decision entry
- Include: date, program, decision, made by, stakeholders, rationale, impact
- Ask user for rationale/impact if not provided

**Action items (`state/action-items.md`):**
- Add new action items with ID, action, program, owner, due date, status, created date

**Meeting notes (`meetings/[YYYY-MM-DD]-$ARGUMENTS.md`):**
- Create meeting notes file with full capture

### 5. Recalculate Health

After updates, recalculate program health and note any change.

### 6. Confirmation Output

```
## Debrief Complete: [Program Name]

**Updates Applied:**
- [Initiative]: [What changed]
- [Risk]: [Status change]
- [Milestone]: [Status change]

**Logged to Decision Log:**
- "[Decision summary]" (see state/decision-log.md)

**Action Items Created:**
- [ID]: [Action] ([Owner], [Due])

**Meeting Notes Saved:**
- meetings/[YYYY-MM-DD]-$ARGUMENTS.md

**Health Update:** [Previous emoji] [Previous] → [New emoji] [New]

Program file and logs updated. Run `/board` to see the portfolio view.
```

## Notes

- Be conversational - guide the user through each section
- If a section has no updates, acknowledge and move on
- For decisions, prompt for full context (rationale, impact) if not provided
- Generate unique action item IDs (A-XXX format, incrementing)
- Always confirm what was captured before finalizing
- If health changed significantly, highlight why
