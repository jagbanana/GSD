# GSD New Program

Add a new program to the portfolio.

## Instructions

### 1. Introduction and Number Assignment

Read all existing program files to determine the next available program number.

```
## Add New Program

I'll help you add a new program to your portfolio. This will create a program
file and update your portfolio summary.

This will be assigned program number [X].
```

### 2. Gather Program Details

Prompt for each required field:

```
**Program Name:**
(Human-readable name, e.g., "Marketing" or "Customer - Acme Corp")
> [Waiting for user input]

**Slug:**
(Lowercase with hyphens for file naming, e.g., "marketing", "customer-acme")
> [Waiting for user input]

**Function:**
(e.g., Marketing, Customer Engagement, Business Development, Product, Engineering)
> [Waiting for user input]

**Line of Business:**
(Which business lines does this support? e.g., Services, Program-Blue, or both)
> [Waiting for user input]

**Type:**
- "ongoing" - Continuous program without a defined end date
- "time-bound" - Project with a target completion date
> [Waiting for user input]

**Owner:**
(Who runs this program day-to-day?)
> [Waiting for user input]

**Meeting Cadence:**
(When do you typically meet? e.g., "Tuesdays, Fridays" or "Weekly on Mondays")
> [Waiting for user input]

**Related OKRs:**
(What organizational objectives does this program support?)
> [Waiting for user input]
```

### 3. Initial Initiatives (Optional)

```
Would you like to add initial initiatives for this program? (yes/no)
```

If yes, for each initiative:
```
**Initiative Name:**
> [Input]

**Stage:** (Backlog / Evaluation / Planning / In Flight / Complete)
> [Input]

**Target Completion Date:** (YYYY-MM-DD or "Ongoing")
> [Input]

**Brief Description:**
> [Input]

Add another initiative? (yes/no)
```

### 4. Initial Risks/Dependencies (Optional)

```
Any known risks or dependencies to document now? (yes/no)
```

If yes, gather basic information for each.

### 5. Create Program File

Generate `programs/[slug].md` using the template structure:

```markdown
---
name: [Program Name]
number: [Next Available Number]
slug: [slug]
function: [Function]
line_of_business: [LoB tags]
type: [ongoing|time-bound]
owner: [Owner Name]
meeting_cadence: [Cadence]
last_updated: [Today's Date]
health: green
health_override: null
okrs:
  - [OKR 1]
  - [OKR 2]
---

# [Program Name]

## Overview
[To be filled in - brief description of the program]

## Current Initiatives

### [Initiative Name]
- **Stage:** [Stage]
- **Target Complete:** [Date]
- **Progress:** 0%
- **Status:** On track
- **Description:** [Description]

## Milestones

| Milestone | Target Date | Status | Notes |
|-----------|-------------|--------|-------|

## Risks

| Risk | Impact | Likelihood | Mitigation | Owner | Status |
|------|--------|------------|------------|-------|--------|

## Dependencies

| Dependency | Type | Status | Blocked By | Notes |
|------------|------|--------|------------|-------|

## Recent Updates

### [Today's Date]
- Program created

## Open Questions for Leadership

- [Add questions as they arise]

## Notes

[Additional context and background]
```

### 6. Update Portfolio Summary

Add the new program to `state/portfolio-summary.md` program list.

### 7. Confirmation

```
## New Program Created: [#] [Program Name]

**Program Number:** [#]
**File:** programs/[slug].md
**Function:** [Function]
**Line of Business:** [LoB]
**Owner:** [Owner]
**Meeting Cadence:** [Cadence]

**Initial Initiatives:**
1. [Initiative Name] ([Stage], target [Date])
...
(or "None - add initiatives as they're identified")

Program added to portfolio.

**Next Steps:**
- Run `/board` to see updated portfolio view
- Use `/brief [#]` (or `/brief [slug]`) before your first meeting
- Edit programs/[slug].md to add more detail

Would you like to add another program?
```

## Validation

- **Slug:** Must be lowercase, letters/numbers/hyphens only, no spaces
- **Slug uniqueness:** Check that no existing program has the same slug
- **Type:** Must be "ongoing" or "time-bound"

## Notes

- Keep the initial setup lightweight - details can be added later
- The program starts with "green" health since there's no history
- Encourage filling in the Overview section after creation
- If user skips optional sections, that's fine - the structure is there for later
