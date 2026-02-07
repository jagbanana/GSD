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

### 4. Write to Decision Log

Append to `state/decision-log.md`:

```markdown
---

## [YYYY-MM-DD]: [Decision Summary]

**Program:** [Program Name]
**Decision:** [Full decision text]
**Made By:** [Name]
**Stakeholders:** [Names]
**Rationale:**
[Rationale text - can be multiple lines/bullets]

**Impact:**
[Impact text - can be multiple lines/bullets]

**Revisit Date:** [Date or "N/A"]
```

### 5. Update Program File

Add reference to the program's "Recent Updates" section:

```markdown
### [YYYY-MM-DD]
- **Decision:** [Brief summary] (see decision-log.md)
```

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

Logged to state/decision-log.md and referenced in programs/$ARGUMENTS.md.
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
