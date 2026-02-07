# GSD Setup

Guide the user through first-time GSD configuration.

## Instructions

You are setting up GSD (Get Shit Done) for a new user. Follow this flow:

### 1. Welcome & Context

Start with:
```
Welcome to GSD: The Leadership OS

GSD helps senior leaders maintain visibility across their portfolio through:
- Structured program tracking
- Meeting preparation and capture
- Decision logging with full context
- Executive summaries

This setup will take about 10 minutes. I'll help you configure your portfolio.
```

### 2. User Profile

Gather:
- **Name:** User's name
- **Role:** Their title/role
- **Lines of Business:** What business areas they oversee (e.g., Services, Product, etc.)
- **Key OKRs:** Top 3-5 organizational goals they're driving toward
- **Communication Preference:** Concise or detailed responses

### 3. Program Inventory

For each program they oversee, gather:
- **Name:** Human-readable name (e.g., "Marketing")
- **Slug:** Lowercase, hyphenated (e.g., "marketing", "customer-acme")
- **Function:** Marketing, Customer Engagement, Business Development, Product, etc.
- **Line of Business:** Which LoB tags apply
- **Type:** "ongoing" (continuous) or "time-bound" (has end date)
- **Owner:** Who runs the program day-to-day
- **Meeting Cadence:** When they meet (e.g., "Tuesdays, Fridays")

Ask if they want to add initial initiatives for any programs.

### 4. Preferences

Confirm or adjust:
- Health calculation weights (show defaults, offer to customize)
- Meeting brief detail level

### 5. Generate Files

Create:
1. Update `state/portfolio-summary.md` with user profile and program list
2. Create a program file for each program in `programs/[slug].md` using the template
3. Initialize `state/decision-log.md` and `state/action-items.md`

### 6. Confirmation

Show:
```
## Setup Complete!

**Your Portfolio:**
[List programs with health indicators]

**Files Created:**
- programs/[slug].md for each program
- state/portfolio-summary.md
- state/decision-log.md (initialized)
- state/action-items.md (initialized)

**Next Steps:**
1. Run `/gsd` to start your first session
2. Use `/brief [program]` before meetings
3. Use `/debrief [program]` after meetings

Your GSD workspace is ready!
```

## File Templates

When creating program files, use `templates/program-template.md` as the base and fill in the gathered information.

When updating portfolio-summary.md, include:
- User profile section
- Program inventory table
- OKRs reference
- Last setup date

## Important Notes

- If the user already has programs configured, ask if they want to add more or reconfigure
- Validate slugs are lowercase with hyphens only
- Ensure meeting cadence is human-readable
- Don't create sample data - only what the user provides
