# GSD Tree

Display a tree view of all programs and their lettered initiatives.

## Instructions

### 1. Load All Programs

Read all program files from `programs/` directory.
Sort programs by their `number` field (ascending).

### 2. Extract Initiative Data

For each program, extract all initiatives with:
- Letter (a, b, c, etc.)
- Name
- Stage
- Status

### 3. Generate Tree Output

Create a text-based tree view:

```
═══════════════════════════════════════════════════════
   Portfolio Tree
═══════════════════════════════════════════════════════

[#] Program Name (health indicator)
 ├─ [letter] Initiative Name [Stage] (Status)
 ├─ [letter] Initiative Name [Stage] (Status)
 └─ [letter] Initiative Name [Stage] (Status)

[#] Program Name (health indicator)
 └─ (no initiatives)

...

───────────────────────────────────────────────────────
Summary: [X] Programs | [Y] Initiatives
Quick Reference: Use "1a", "2b", etc. to reference initiatives
───────────────────────────────────────────────────────
```

### 4. Formatting Rules

**Program line:**
- Show program number in brackets: `[1]`
- Show program name
- Show health indicator: 🟢 🟡 🔴

**Initiative line:**
- Use tree characters: `├─` for middle items, `└─` for last item
- Show letter in brackets: `[a]`
- Show initiative name
- Show stage in brackets: `[In Flight]`
- Show status indicator:
  - On track → (On track) or no indicator
  - At risk → ⚠️
  - Off track / Blocked → 🚫
  - Not started → (Not started)

**Programs without initiatives:**
- Show `└─ (no initiatives)`

### 5. Example Output

```
═══════════════════════════════════════════════════════
   Portfolio Tree
═══════════════════════════════════════════════════════

[1] Marketing 🟢
 ├─ [a] Website Revamp [In Flight]
 ├─ [b] Content Strategy [Planning]
 └─ [c] Analytics Setup [Backlog]

[2] Product Management 🟢
 ├─ [a] User Journey Refinement [In Flight]
 └─ [b] Feature Prioritization [In Flight]

[3] Sales 🟢
 └─ (no initiatives)

[4] Customer Success 🟡
 ├─ [a] Renewals Process [In Flight] ⚠️
 └─ [b] Onboarding Improvements [Evaluation]

───────────────────────────────────────────────────────
Summary: 4 Programs | 7 Initiatives
Quick Reference: Use "1a", "2b", etc. to reference initiatives
───────────────────────────────────────────────────────
```

### 6. Filtering Support

If the user provides arguments, support filtering:
- `/tree [#]` - Show only that program's tree (e.g., `/tree 1`)
- `/tree [slug]` - Show only that program's tree (e.g., `/tree marketing`)
- `/tree in-flight` - Show only In Flight initiatives
- `/tree at-risk` - Show only At Risk initiatives

### 7. Empty State

If no programs exist:
```
═══════════════════════════════════════════════════════
   Portfolio Tree
═══════════════════════════════════════════════════════

No programs found.

Run `/setup` to configure your portfolio, or
Run `/newprogram` to add a program.

═══════════════════════════════════════════════════════
```

## Notes

- This is the quickest way to see all programs and initiatives at a glance
- Use the letter codes (1a, 2b, etc.) to quickly reference initiatives in other commands
- The tree is sorted by program number, initiatives by their letter order
