# Documentation Coaching

## Time the Work

Document stable feature slices once contracts, learner-designed tests, and callers are settled. Record urgent rationale, safety constraints, side effects, deprecations, units, and compatibility assumptions immediately. Batch private helpers; do not interrupt every helper or postpone all documentation until project completion.

At each slice, finish public docstrings, CLI/config help, and necessary API/guide updates before unrelated work. Add public API index entries only when required and workflow examples when useful. Keep private helpers out of user docs unless their contract needs explanation. If time runs out, record `Docs pending: <symbols/docs> | reason | next checkpoint` in coaching history and remove it when resolved.

## Coach the Content

Inspect the diff, callers, and repository conventions. Ask what a future caller or maintainer needs beyond the signature, code, types, and tests, and where it belongs. Let the learner draft; agree, partially agree, or correct with reasons, then assign one bounded edit.

Judge comments as needed for hidden rationale/invariants, unnecessary when clear code suffices, or requiring revision when stale, vague, syntax narration, or duplicated implementation. Prefer clearer code; keep comments beside the protected fact, remove commented-out code, and make TODOs actionable. Check whether the wording survives a naming or implementation change.

Follow repository docstring conventions; otherwise teach NumPy/scikit-learn style. For an unfamiliar format, show only relevant section roles and a skeleton: Parameters, Returns/Yields, Raises, Warns, See Also, Notes, References, Examples. Have the learner supply the prose.

For public scientific APIs, cover relevant accepted forms, shapes, dtypes, units, defaults, mutation, randomness, errors, and public attributes. Avoid repeating type hints or implementation steps; use deterministic examples when needed.

## Verify

Check accuracy, placement, clarity, and maintenance cost against signatures/defaults, behavior, examples, links, exports, API indexes, and CLI help. Update documentation with behavior changes. Use existing docstring lint, doctest, link checks, Sphinx, or MkDocs where relevant; teach unfamiliar commands within the session boundary. Do not add a documentation stack for this checkpoint.
