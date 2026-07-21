---
name: end-training
description: Save the complete English drill session and resumable learning state. Use ONLY when the learner runs /endtraining or explicitly asks to end and archive the current training session.
---

# End Training

Archive the current English training session without losing exercise-level detail, then update the resumable session record.

## Files

- Append the detailed session to `training-records/YYYY-MM-DD.md`, using the current local date.
- Update `english-fsi-session.md` as the canonical progress and continuation record.
- Resolve all paths from the current workspace root. Never read or write global OpenCode configuration or files outside the current workspace.

## Archive Procedure

1. Read `english-fsi-session.md` and today's archive file if they exist.
2. Identify training turns since the latest archived session or, when none exists, since the current training began.
3. Append a new numbered `Session` section to today's archive. Never overwrite an earlier session.
4. Preserve every available exercise attempt in chronological order, including:
   - pattern number and target structure;
   - drill type and item number;
   - prompt or source sentence;
   - learner's exact answer;
   - correct or incorrect result;
   - every spelling, grammar, vocabulary, and punctuation correction;
   - the accepted answer and Chinese translation when provided;
   - retries, rather than retaining only the final successful answer.
5. Include a short session summary with completed work, partial progress, recurring errors, and preferences stated by the learner.
6. If earlier turns are unavailable because conversation context was truncated, state exactly which portion is unavailable. Never reconstruct or invent missing attempts.

Use this structure for each archived session:

```markdown
## Session N - HH:MM

### Summary

### Exercise Log

#### Pattern X - target structure

| Drill | Item | Prompt | Learner answer | Result and correction | Chinese |
| --- | ---: | --- | --- | --- | --- |

### Errors and Review Notes

### Learner Preferences

### Resume From
```

Escape pipe characters inside table cells. Use `Not provided` for a Chinese translation that was not present; do not create a translation retroactively in the archive.

## Canonical Record

Update `english-fsi-session.md` after the detailed archive is written:

- Set `Last updated` to the current local date.
- Record newly completed patterns and both drill counts.
- Preserve previous completed work and notes.
- Add newly observed errors and learner preferences without duplicating existing entries.
- Replace stale current-position information with the exact next pattern, drill type, item number, prompt, and expected answer when known.
- Mark the session as paused if no next prompt has been issued.
- Ensure the continuation instructions prohibit repeating completed patterns unless the learner explicitly requests review.
- Preserve the learner's feedback format: after a correct answer, show the accepted English sentence followed by its Chinese translation in a Markdown `IMPORTANT` alert.

## Completion Response

Do not issue another exercise prompt. Report:

- the archive path;
- the canonical record path;
- the saved completion counts and exact resume position;
- any unavailable context that could not be archived.
