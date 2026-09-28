# Test Design Gate

Keep teaching within the agreed depth/time boundary and reuse demonstrated command familiarity.

## Establish Provisional Correctness

Compare implementation with its contract and examples; inspect control flow, shapes/types, errors, side effects, and affected callers. Run existing focused checks or a safe smoke example. Call the result provisionally correct; testing increases confidence without proving correctness.

Existing tests may run before the gate. Do not design new function-specific tests for the learner before their proposal.

## Ask, Wait, Evaluate

Ask: "Does this function need dedicated tests? If so, what behaviors or cases should we test, and why?" Wait unless the learner already supplied a proposal. Do not reveal a checklist first.

Explicitly agree, partially agree, or correct with reasons. Retain useful cases and explain missing risks, redundancy, implementation-detail assertions, or unsuitable test levels.

Consider only relevant behaviors: representative success, boundaries, missing/empty or invalid input, state/side effects, regressions, and external interactions. Choose unit, integration, contract, UI, or manual checks appropriate to the boundary. For trivial delegation, generated code, or disposable exploration, dedicated tests may be unnecessary; ask for the existing coverage path and confirm or correct it.

## Coach Implementation

1. Prioritize the smallest valuable case. Have the learner state setup/input, action, expected observable result, and why failure matters.
2. Explain unfamiliar test APIs and runner arguments only as needed. A correct independent use needs no extra quiz.
3. Give at most a placeholder skeleton; the learner chooses values/assertions and writes the test.
4. Review assertions, independence, determinism, and readable failures. Run the focused test, interpret it together, then run the appropriate broader checks.

For a bug fix, demonstrate the failure with a regression test before or alongside the fix when practical. Fake only genuine external boundaries; avoid excessive mocking and coverage-percentage targets.
