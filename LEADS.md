# Research Lead Registry

A lead connects a controllable input to sensitive data or an action across a
concrete trust boundary. A suspicious string, dependency, or dangerous
function is not sufficient by itself.

## States

- `Idea`: unstructured intuition.
- `Static hypothesis`: partial path demonstrated in a verified artifact.
- `Runtime ready`: preconditions and minimum test are defined.
- `Confirmed`: impact correlated by controlled evidence.
- `Dismissed`: a guard or runtime behavior disproves the path.
- `Parked`: a legitimate precondition is missing, with a precise resumption
  condition.

## Registry

| Identifier | State | Asset / version | Boundary and path | Expected impact | Next evidence | Verdict condition |
| --- | --- | --- | --- | --- | --- | --- |
| To create | Idea |  |  |  |  |  |

## Naming

Give every lead a stable identifier using `<AREA>-<NNN>`, where `AREA` is a
short uppercase name for the relevant surface or subsystem and `NNN` is a
three-digit sequence. Examples include `AUTH-001`, `IPC-002`, and `UPDATE-003`.

Do not include status, severity, version, or a product build in the identifier.
Those properties may change while the identifier must remain stable.

Use `<LEAD-ID>-<short-kebab-case-title>` as the common filename stem:

```text
reports/potential-vulnerabilities/AUTH-001-session-ownership-check.md
reports/runtime-validations/AUTH-001-session-ownership-check.md
reports/AUTH-001-session-ownership-check-final.md
```

When the state changes, update this registry and move the canonical record when
appropriate; do not rename it to reflect the new state. A dismissed lead keeps
the same identifier and filename so its analysis remains easy to find without
creating a duplicate investigation.

Name supporting evidence `<LEAD-ID>-E<NN>-<short-description>.<extension>`, for
example `AUTH-001-E01-runtime-result.txt`, and register it in
`reports/evidence/README.md`.

## Discipline

Create a file under `reports/potential-vulnerabilities/` only when the
caller, input, guard, consumer, and impact are concrete. Move or duplicate the
summary under `reports/runtime-validations/` after runtime
validation.

Never promote a hypothesis because it appears severe. The verdict must state
what was observed, what static analysis proves, what remains inferred, and what
runtime testing confirms.

A parked or dismissed lead must state the exact new caller, consumer, version
delta, state transition, guard bypass, representation mismatch, or composition
that would justify reopening it.
