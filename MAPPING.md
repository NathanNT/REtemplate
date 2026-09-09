# Project Mapping

## Objective

Describe how the product is organized and how its major components interact.
The mapping is an architectural model, not a file-by-file inventory. It should
make trust boundaries, data flows, privileged consumers, and exposed interfaces
easy to understand before detailed vulnerability analysis begins.

## Product baseline

Record the overall application version used for the research. Add separate
versions only when independently deployed services or clients clearly differ.

| Product | Overall version / build | Release or acquisition date | Platforms / environments | Source |
| --- | --- | --- | --- | --- |
| To be completed |  |  |  |  |

## Mapping workflow

1. Identify the product's top-level structure from documentation, directory
   layout, package manifests, configuration, and observed runtime behavior.
2. Group files into logical components such as client, launcher, local service,
   backend, updater, plugin system, web application, API, and data store.
3. Record each component's responsibility, execution context, privilege level,
   and principal dependencies.
4. Trace how components communicate through files, IPC, sockets, HTTP,
   WebSocket, QUIC, RPC, serialization, queues, or shared storage.
5. Identify which component authenticates the caller and which component makes
   the final authorization decision.
6. Mark external input, privilege changes, parser transitions, and movement of
   sensitive data as trust boundaries.
7. Label uncertain relationships as inferences and list the observation needed
   to confirm them.
8. Link a research lead to the relevant component and interaction entries.

## Components

| Component | Technology / runtime | Responsibility | Runs where / as whom | Main dependencies | Trust level | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| To be completed |  |  |  |  |  |  |

## Per-component analysis

When reverse engineering requires more detail, create a lightweight component
note under `analysis/ID-<component-name>.md`. Use a stable, lowercase,
kebab-case identifier for the logical component rather than for a particular
file or version.

Keep the note minimal:

```markdown
# ID-component-name

**Role:** Short description of the component's responsibility.

## Interactions

| Direction | Component | Function | Arguments | Result / effect | Notes |
| --- | --- | --- | --- | --- | --- |
| Incoming or outgoing | `ID-peer` | `function()` | Relevant arguments | Return value, state change, or action | Useful behavior |

## Notes

Free-form reverse-engineering notes.
```

Add one row for each relevant function involved in an intercomponent
interaction. Record what its arguments represent, what the function does, and
what it returns or changes. It is not necessary to document unrelated internal
functions.

## Component interactions

| Source | Destination | Interface / protocol | Data or command exchanged | Authentication | Authorization owner | Evidence / status |
| --- | --- | --- | --- | --- | --- | --- |
| To be completed |  |  |  |  |  |  |

## Exposed surfaces and trust boundaries

| Surface | Controlling actor | Receiving component | Parser or handler | Boundary crossed | Sensitive capability or data |
| --- | --- | --- | --- | --- | --- |
| To be completed |  |  |  |  |  |

## Architecture sketch

Keep a compact diagram or text model synchronized with the tables above. For
example:

```text
Untrusted client
  -> public interface
  -> protocol or request handler
  -> authentication service
  -> authorization decision
  -> privileged service
  -> data store or operating-system capability
```

## Evidence discipline

Use the general application version to anchor the map. Do not calculate or
record a hash for every file. Record a SHA-256 only when a specific binary,
library, archive, or generated input becomes important to a detailed static
analysis, runtime validation, or vulnerability report.

Do not infer that a component is exposed merely because it exists in the
installation tree. Confirm that it is loaded, reachable, or invoked in the
authorized environment before treating the path as active.
