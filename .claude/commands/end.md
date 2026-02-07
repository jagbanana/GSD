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

### 3. Verify State

Check that all changes have been persisted:
- Program files updated
- Decision log current
- Action items captured
- Portfolio summary reflects current state

### 4. Generate Output

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

### 5. Optional: Prompt for Notes

Ask if there's anything else to capture before ending:
- Thoughts to remember
- Items to revisit
- Context for next session

## Notes

- This command is optional but recommended for clean session boundaries
- If the user just closes Claude Code, state is still persisted from individual commands
- Focus on what was accomplished, not what wasn't
