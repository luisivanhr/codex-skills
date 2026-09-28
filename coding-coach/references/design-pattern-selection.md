# Design Pattern Selection

Choose patterns from observed code pressure; never default to a favorite.

## Select From the Code

Inspect callers, variation, dependencies, tests, and likely changes. Describe the concrete pressure before naming a pattern. Present at most two or three plausible approaches, including the simplest direct solution. Recommend a pattern only when duplication, coupling, lifecycle, state, extension, or testing needs justify its cost. Prefer language/framework idioms over textbook ceremony.

Use this map internally; show only relevant candidates:

| Pressure | Simple starting point | Consider if needed |
| --- | --- | --- |
| Variable construction | creation function | Factory Method; Abstract Factory for families; Builder for stages |
| Interchangeable algorithms | callable or conditional | Strategy; Template Method for a stable inherited skeleton |
| Discoverable handlers | dictionary or switch | Registry, plugins |
| Queuing, retry, logging, undo | direct call | Command |
| Different interfaces | thin wrapper | Adapter; Facade for a subsystem |
| Layered behavior | wrapper | Decorator; Proxy for access/lifecycle |
| Ordered processing | explicit loop | Pipeline; conditional middleware/Chain of Responsibility |
| State-dependent behavior | enum and conditional | State, finite-state machine |
| Event consumers | direct calls | Observer; pub/sub for stronger decoupling |
| Persistence separation | data-access functions | Repository; Unit of Work for transactions |
| Part-whole trees | nodes and recursion | Composite |
| Hidden dependencies | explicit parameters | Dependency injection; container optional |
| UI separation | framework conventions | MVC, MVP, MVVM where appropriate |

Other patterns require corresponding evidence. A Singleton needs a real process-wide lifecycle and test isolation.

Clarify relevant distinctions: factories create while registries map; strategies select behavior while commands represent actions; adapters change interfaces, facades simplify subsystems, and decorators preserve interfaces while adding behavior. State follows lifecycle transitions; Strategy is usually caller-selected. Observer typically knows subscribers; pub/sub adds an intermediary.

## Explain and Implement

Map the chosen pattern's roles to actual files and callables. Explain the pressure, contract, dependency direction, why the simple option is insufficient, and the added cost and breakage surface.

Migrate one variant/caller through the smallest seam, apply the function test-design gate, and check direct and downstream dependents before migrating the rest and removing the obsolete path. Reconsider if the first slice adds ceremony without relieving the pressure.

Record patterns in coaching history after concrete explanation/use. Reuse demonstrated familiarity; check recognition only when useful within the agreed scope.
