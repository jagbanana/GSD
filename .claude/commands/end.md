# GSD Session End

End the current GSD session and save state.

## Instructions

### 1. Session Summary

Compile what was accomplished during the session:
- Programs reviewed or updated
- Decisions logged
- Action items created
- Briefs generated
- Debriefs completed

### 2. Update Session Log

Append to `sessions/[YYYY-MM-DD].md`:
- Session end time
- Summary of activities
- Any items flagged for next session
- Include `[[program-slug]]` wikilinks when referencing programs reviewed
- Include `[[DEC-NNN-slug]]` wikilinks when referencing decisions logged

### 3. Verify State and Update Portfolio Summary

Check that all changes have been persisted:
- Program files updated
- Decision files created in `decisions/`
- Action items captured

Update `state/portfolio-summary.md` with current values:
- Recalculate health for each program using the standard health formula
- Overwrite the **Portfolio Health Summary** table with the current health distribution (Green/Yellow/Red counts and program names)
- Update the **Health** column in the **Programs** table to match current program health
- Set `Last Updated` to today's date

### 4. Meeting Note and Action Item Maintenance

**Meeting Note Archival:**
List all files in `meetings/` (not `meetings/archive/`). For each meeting note older than 30 days (based on the date in the filename YYYY-MM-DD):
1. **Verify preservation of key data:**
   - Check that any decisions referenced in the meeting note exist as files in `decisions/` (they should — /debrief creates them)
   - Check that any action items from the meeting exist in `state/action-items.md` (they should — /debrief creates them)
   - If anything is missing, flag it to the user before archiving
2. **Move the file:** Move the meeting note from `meetings/YYYY-MM-DD-program.md` to `meetings/archive/YYYY-MM-DD-program.md`
3. **Report:** At the end of the session output, include a line:
   "Archived [X] meeting notes older than 30 days to meetings/archive/"
   (Only show this line if X > 0)

**Action Item Archival:**
In `state/action-items.md`, check the "Recently Completed" section. For any completed items older than 30 days (by their Completed date):
1. Remove them from the "Recently Completed" table in `action-items.md`
2. This is safe because the action items are also recorded in their source meeting notes (which are archived, not deleted)
3. **Report:** At the end of the session output, include a line:
   "Archived [X] completed action items older than 30 days"
   (Only show this line if X > 0)

### 5. Generate Output

```
## Session Complete

**Duration:** [start time] - [end time]

**This Session:**
- [X] programs reviewed
- [X] decisions logged
- [X] action items created
- [X] briefs/debriefs completed

**Outstanding Items:**
- [Any items that weren't addressed]

**Reminder:** Your next likely meetings based on cadence:
- [Day]: [Program]
- ...

See you next time. Run `/gsd` to start your next session.
```

### 6. Optional: Prompt for Notes

Ask if there's anything else to capture before ending:
- Thoughts to remember
- Items to revisit
- Context for next session

## Notes

- This command is optional but recommended for clean session boundaries
- If the user just closes Claude Code, state is still persisted from individual commands
- Focus on what was accomplished, not what wasn't
