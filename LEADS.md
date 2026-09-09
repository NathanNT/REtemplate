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

## Discipline

Create a file under `reports/potential-vulnerabilities/` only when the
caller, input, guard, consumer, and impact are concrete. Move or duplicate the
summary under `reports/runtime-validations/` after runtime
validation.

Never promote a hypothesis because it appears severe. The verdict must state
what was observed, what static analysis proves, what remains inferred, and what
runtime testing confirms.
