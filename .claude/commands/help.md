# GSD Help

Display the command reference for GSD.

## Instructions

Output the following help information:

```
# GSD Commands

## Session
| Command | Description |
|---------|-------------|
| `/gsd` | Start session with portfolio overview |
| `/end` | End session and save state |

## Meetings
| Command | Description |
|---------|-------------|
| `/brief [program]` | Pre-meeting preparation for a program |
| `/debrief [program]` | Capture notes after a program meeting |

## Portfolio
| Command | Description |
|---------|-------------|
| `/board` | Visual portfolio board (kanban view) |
| `/tree` | Tree view of all programs and initiatives |
| `/portfolio` | Portfolio review with executive summary |

## Programs
| Command | Description |
|---------|-------------|
| `/newprogram` | Add a new program to the portfolio |
| `/decision [program]` | Log a major decision |

## Setup & Help
| Command | Description |
|---------|-------------|
| `/setup` | First-time GSD configuration |
| `/help` | Show this command reference |

---

**Examples:**
- `/brief 1` — Prepare for Program 1 check-in
- `/brief marketing` — Prepare for marketing check-in
- `/debrief customer-acme` — Capture notes from Acme meeting
- `/decision bd-partners` — Log a decision for BD program

**Quick Reference:**
- Programs use **numbers** (1, 2, 3) or **slugs** (program-blue-marketing)
- Initiatives use **letters** within programs (a, b, c)
- Combine them: `1a` = Program 1, Initiative a
- Run `/tree` to see all programs and initiatives with their codes

Want details on a specific command? Just ask!
```

Then offer to explain any command in more detail if the user asks.
