# Decision Log

All major decisions across the portfolio, logged for future reference.

> Individual decisions are stored as `DEC-NNN-slug.md` files in this folder.
> Use `/decision [program]` in Claude Code to log new decisions.

---

## All Decisions

```dataview
TABLE program AS "Program", date AS "Date", made_by AS "Made By", stakeholders AS "Stakeholders"
FROM "decisions"
WHERE id != null
SORT date DESC
```

## Decisions by Program

```dataview
TABLE date AS "Date", title AS "Title", made_by AS "Made By"
FROM "decisions"
WHERE id != null
GROUP BY program
SORT date DESC
```

## Upcoming Revisit Dates

```dataview
TABLE program AS "Program", title AS "Decision", revisit_date AS "Revisit Date"
FROM "decisions"
WHERE revisit_date != null AND revisit_date >= date(today)
SORT revisit_date ASC
```

---

*Decision index powered by Dataview. Run `/decision [program]` in Claude Code to log new decisions.*
