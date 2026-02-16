# GSD Decision

Log a major decision with full context and rationale.

## Arguments

- `$ARGUMENTS` - The program slug (e.g., "marketing", "customer-acme")

## Instructions

### 1. Validate Program

Read the program file from `programs/$ARGUMENTS.md`

If the file doesn't exist, show error and list available programs.

### 2. Gather Decision Details

Prompt the user for each element:

```
## Log Decision: [Program Name]

I'll help you document this decision for future reference.

**What was decided?**
> [Waiting for user input]

**Who made the decision?**
> [Waiting for user input]

**Who were the key stakeholders or supporters?**
> [Waiting for user input]

**What was the rationale?**
(Why was this the right choice? What alternatives were considered?)
> [Waiting for user input]

**What's the expected impact?**
(What changes as a result of this decision?)
> [Waiting for user input]

**Should this decision be revisited? If so, when?**
> [Waiting for user input - optional]
```

### 3. Confirm and Log

Show the complete decision record for confirmation:

```
## Decision Record (Draft)

**Decision:** [Summary]
**Program:** [Program Name]
**Date:** [Today's Date]
**Made By:** [Name]
**Stakeholders:** [Names]

**Rationale:**
[Full rationale text]

**Impact:**
[Expected impact text]

**Revisit Date:** [Date or "None"]

---
Does this look correct? (yes/edit/cancel)
```

### 4. Create Decision File

1. List files in `decisions/` directory to find the highest existing `DEC-NNN` number
2. Increment to get next number (or start at 001 if none exist)
3. Generate slug from decision summary (lowercase, hyphenated, max 5 words)
4. Create file `decisions/DEC-[NNN]-[slug].md`:

```markdown
---
id: DEC-[NNN]
title: [Decision Summary]
program: [program-slug]
date: [YYYY-MM-DD]
made_by: [Name]
stakeholders:
  - [Name 1]
  - [Name 2]
revisit_date: [Date or null]
tags:
  - decision
  - [program-slug]
---

# DEC-[NNN]: [Decision Summary]

**Program:** [[program-slug]]
**Date:** [YYYY-MM-DD]
**Made By:** [Name]
**Stakeholders:** [Names]

## Decision

[Full decision text]

## Rationale

[Rationale text - can be multiple lines/bullets]

## Impact

[Impact text - can be multiple lines/bullets]

## Revisit

[Date and conditions, or "N/A"]
```

### 5. Update Program File

Add reference to the program's "Recent Updates" section:

```markdown
### [YYYY-MM-DD]
- **Decision:** [Brief summary] — [[DEC-NNN-slug]]
```

If there are already 3 entries in Recent Updates, remove the oldest one.

### 6. Confirmation

```
## Decision Logged

**Decision:** [Summary]
**Program:** [Program Name]
**Date:** [Today's Date]
**Made By:** [Name]
**Stakeholders:** [Names]

**Rationale:**
[Brief rationale]

**Impact:**
[Brief impact]

**Revisit:** [Date or "N/A"]

Logged to decisions/DEC-[NNN]-[slug].md and referenced in programs/$ARGUMENTS.md.
```

## When to Use This Command

Encourage logging decisions for:
- Major resource allocation decisions
- Go/no-go decisions on initiatives
- Strategic direction changes
- Escalation decisions
- Scope changes
- Vendor/partner selections
- Any decision that might be questioned or revisited later

## Notes

- Decisions should be logged even if made outside of meetings
- The rationale is the most important part - future you will thank present you
- If the user is uncertain about stakeholders, prompt for who was consulted or informed
- Revisit dates are optional but valuable for decisions that should be reassessed
