# Project Architecture and CLI Practice

Read this reference when code is accumulating in notebooks, reusable modules or scripts are needed, or the learner needs terminal/configuration practice.

## Choose the Smallest Useful Shape

Keep a notebook when the work is exploratory, visual, narrative, or intentionally disposable. Extract code when it is reused, difficult to test in a cell, parameterized for repeated runs, responsible for I/O, or stable enough to have a contract.

For a small Python project, a module plus a thin runner and tests may be enough. As it grows, a typical shape is:

```text
project/
  src/<package>/       reusable logic and adapters
  tests/               behavior checks
  notebooks/           exploration, plots, narrative
  scripts/ or CLI      thin orchestration entry points
```

Do not impose `src/`, packaging, or several layers when a single module and test file are clearer. Explain what pressure justifies each new file or boundary.

## Keep Notebooks Thin and Reproducible

- Put reusable computation in importable functions; let the notebook choose inputs, call them, and visualize results.
- Avoid correctness that depends on hidden cell order or stale state.
- Re-run from a fresh kernel/top to bottom after extraction.
- Keep one-off plots and narrative in the notebook unless reuse warrants moving them.

## Teach Real Terminal Execution

Use the project's actual interpreter and paths. Python source normally runs as a `.py` file or module, not as `run.exe`:

```powershell
python .\scripts\run_simulation.py --num-events 100
python -m package.run --num-events 100
```

Prefer module execution when it makes imports and package boundaries clearer. Explain unfamiliar working-directory, environment, or command details within the agreed scope. Hyphenated CLI flags are conventional; many parsers accept both `--flag value` and `--flag=value`, but teach the spelling actually defined by the program.

For Python `argparse`, introduce only the pieces needed now:

```python
parser.add_argument("--num-events", type=int, default=100)
args = parser.parse_args()
# value is available as args.num_events
```

Explain `type`, the choice between `default` and `required`, and the exact value for the current run. Mention `choices`, validation, `help`, `--seed`, or output paths only when likely to matter next. Coach the learner to run `--help`, one normal smoke command, and one invalid-input command.

Use function arguments for in-process behavior, CLI flags for per-run choices, config files for many related non-secret settings, and environment variables or approved secret stores for secrets. Keep parsing and I/O thin so the core function remains directly testable.

## Architecture Coaching Sequence

1. Inspect the current tree and identify responsibilities already present.
2. Propose the smallest split and explain the dependency direction.
3. Have the learner create or move one piece at a time.
4. Run imports or `--help` early to catch path problems.
5. Keep the notebook or runner working after each move.
6. Apply the function test-design gate to extracted logic.

## Teach Change-Impact Reasoning

Before a nontrivial change, trace the relevant path through the whole codebase:

```text
changed contract or state
  -> direct callers/importers
  -> adapters, persistence, or external boundaries
  -> downstream outputs and user-visible behavior
  -> tests, fixtures, scripts, and notebooks that encode the old assumption
```

Inspect real call sites, imports, configuration, schemas, and tests rather than guessing from one file. Ask the learner to predict the affected areas and likely failure modes. Correct or complete their map, then choose focused checks for direct dependents and broader checks for shared contracts. Teach dependency direction and stable boundaries so they learn to ask, "If this changes, who relies on it?"
