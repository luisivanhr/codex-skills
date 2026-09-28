# Command Learning and History

Use for command teaching and continuity within the agreed session boundary.

## Teach Only the Gap

Check familiarity through recent work or a brief targeted question. For an unfamiliar command, function, API, operator, or pattern needed now, explain its family, minimal call shape, inputs/result, and relevant arguments and values. Mention at most one or two nearby options; give only enough syntax for the next attempt.

Recheck only relevant context, overload, or version changes. When recall help is needed, progress from family/result to argument roles to minimal syntax; use a different concrete explanation for repeated confusion. Stop drills after correct independent use.

## Local History

For substantive multi-session work, keep `coaching_history.md` at the project root. In Git, resolve the local exclude file with `git rev-parse --git-path info/exclude`, and mark any coach-added block. Do not change shared `.gitignore` unless asked. In a non-Git folder, keep history local and omit it from deliverables.

Record the agreed deliverable, depth/time boundary, next coding step, and useful deferred concepts. Distinguish material read, explanation demonstrated, and application demonstrated; reading alone does not prove understanding.

Use one row per meaningful symbol and context:

```text
- symbol or pattern | relevant arguments or roles | purpose/context | needs=yes|no | strength=unrated|weak|strong
- pathlib.Path.glob | pattern: str; ** for recursion | discover inputs in loader.py | needs=no | strength=strong
```

Labels describe observed skill in context, never the person. Use `unrated` without evidence, `needs=yes` after failed recall or repeated confusion, and `needs=no` after independent correct use. Merge rows after new evidence. Record patterns only after concrete project use.

Store no secrets, private values, full code, or long explanations. These are project coaching notes, not persistent personal memory. Follow the entrypoint's completion and cleanup steps.
