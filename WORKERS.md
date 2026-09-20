# Sub-Agent Workflow

This optional workflow is used only when parallel delegation adds value. It is
provider- and model-independent.

## Roles

The orchestrator selects questions, coordinates ownership, combines results,
and makes final decisions. Workers handle bounded independent work such as:

- mapping a component or input surface;
- tracing one control-flow or data-flow path;
- searching references or version differences;
- reviewing a candidate for guards, contradictions, or missing assumptions.

## Task contract

Before spawning a worker, persist a short task under
`analysis/worker-results/<job-id>/task.md`. Include:

- the exact question and expected output;
- the target artifact, version, and identity;
- the worker's owned scope;
- relevant known results or closed paths;
- the stopping condition and approximate budget.

Use `checkpoint.md` only for work long enough to risk interruption. Persist the
usable final response as `result.md`; chat messages alone are not durable state.

## Parallel execution

Give workers non-overlapping questions and let the orchestrator continue a
separate useful task. Avoid assigning one live IDA session or another exclusive
backend to multiple agents at the same time. Before replacing an interrupted
worker, inspect its job directory and any still-running process.

## Fast review

The orchestrator does not repeat the complete worker analysis. Review the
result quickly:

1. Does the source-to-result logic follow without a missing transition?
2. Do the cited files, addresses, functions, or outputs exist and support the
   important claims?
3. Are relevant guards, contradictions, assumptions, and uncertainty stated?
4. Does the conclusion stay within the evidence and assigned scope?
5. Do one or two decisive spot checks pass?

Accept the result as a working lead when these checks pass. Request a focused
follow-up when a specific link is weak. Perform deeper independent validation
only when the result is inconsistent, poorly sourced, or will directly support
a high-impact final conclusion or external report.

## Result format

A useful worker result is concise and states:

- assigned boundary and question;
- observed facts with evidence references;
- resulting path or conclusion;
- guards and contradictory evidence;
- confidence and residual uncertainty;
- smallest useful next step or closure condition.
