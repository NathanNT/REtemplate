# Agent Workflow

## Resume order

Read these files completely, in order:

1. `README.md`
2. `MAPPING.md`
3. `LEADS.md`

Locate the latest `Handoff` entry in `JOURNAL.md`, then read only that bounded
entry and the records it references. Read `ACCESS.md` before SSH, IDA, staging,
tool installation or configuration, or other environment-specific access.

When the project is governed by a bug bounty or vulnerability disclosure
program, read `CONTRACT.md` before research and recheck it before each network
or runtime phase. Read `DOCS.md` only while creating or revising a submission
for such a program. Neither file is part of the default reverse-engineering
resume path.

Read `WORKERS.md` only when delegating work to sub-agents.

## Minimal workflow

1. Identify the exact target, build, environment, and research objective.
2. Acquire the artifact from a legitimate source and record its version,
   provenance, size, and SHA-256.
3. Search the map, leads, and targeted journal entries for the same boundary,
   identifiers, and path.
4. State the novelty condition: a new caller, consumer, version delta, state
   transition, guard bypass, representation mismatch, or composition. Reuse
   the existing conclusion when no novelty condition exists.
5. Map formats, processes, protocols, inputs, and relevant boundaries before
   deep analysis.
6. Explicitly distinguish observations, static analysis, inferences, and
   runtime validation.
7. For a security lead, require a connected caller, input, guard, consumer,
   boundary, and plausible impact.
8. Prepare the smallest experiment that can confirm or disprove the current
   hypothesis.
9. Use runtime analysis when it materially resolves the current question, and
   record its environment, inputs, observations, and cleanup.
10. Retain only necessary evidence, clean up temporary objects, and update the
    journal, map, and leads.

## High-impact reasoning

- Trace controlled input through its complete official delivery and
  consumption path rather than assessing a parser or sink in isolation.
- Compare the representation validated with the one later stored or consumed:
  identifiers, paths, owners, lengths, capacities, serialized objects, and
  managed/native views.
- Establish the order of validation, allocation, publication, sensitive use,
  rollback, save, reload, and teardown. Continue through exceptions and
  partial initialization.
- Look for compositions in which modest defects cross a trust or authority
  boundary together.
- Use version differentials to prioritize silent validation, ordering, and
  state-machine changes. A delta is a signal; reachability, guards, and the
  complete source-to-impact path remain required.
- Try to falsify a mature hypothesis and record contradictory evidence before
  promotion.

## Optional parallel work

Delegate only bounded, non-overlapping questions. Persist each task under
`analysis/` before starting a worker, including its artifact identity, owned
scope, novelty condition, known closures, expected output, stopping condition,
and budget. Long work must checkpoint to disk, and each usable result must be
persisted before it is consumed; chat transport alone is not durable evidence.

A worker result is a lead. The orchestrating agent reviews its logic, checks
that the cited evidence supports the path, and spot-checks decisive claims.
Repeat the underlying analysis only when the result is inconsistent, weakly
sourced, or about to support a high-impact final conclusion. Continue separate
useful work while workers run, and inspect existing job files after an
interruption before creating replacements.

## Security lead deliverable

When the research concerns a potential vulnerability, its lead record must
include the asset and version, SHA-256, trust boundary, complete path,
prerequisites, expected impact, minimal test, result, limits, cleanup, links to
evidence, and the exact condition for reopening a parked or dismissed path.
