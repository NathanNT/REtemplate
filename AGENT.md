# Agent Workflow

## Resume order

Read these files completely, in order:

1. `README.md`
2. `CONTRACT.md`
3. `MAPPING.md`
4. `LEADS.md`

Locate the latest `Handoff` entry in `JOURNAL.md`, then read only that bounded
entry and the records it references. Read `ACCESS.md` before SSH, IDA, staging,
or other environment-specific access. Read `DOCS.md` only while creating or
revising a report. Recheck `CONTRACT.md` before every network or runtime phase.

## Minimal workflow

1. Identify the exact asset and confirm that it is currently in scope.
2. Acquire the artifact from a legitimate source and record its version,
   provenance, size, and SHA-256.
3. Search the map, leads, and targeted journal entries for the same boundary,
   identifiers, and path.
4. State the novelty condition: a new caller, consumer, version delta, state
   transition, guard bypass, representation mismatch, or composition. Reuse
   the existing conclusion when no novelty condition exists.
5. Map formats, processes, protocols, inputs, and trust boundaries before
   looking for an exploitable primitive.
6. Explicitly distinguish observations, static analysis, inferences, and
   runtime validation.
7. Create a lead only when a caller, input, guard, consumer, and plausible
   impact can be connected.
8. Prepare the smallest test that can confirm or disprove the hypothesis.
9. Perform runtime testing only when it complies with the contract, scope, and
   the operator's explicit limits.
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

A worker result is a lead. The orchestrating agent independently verifies the
decisive bytes, instructions, types, references, hashes, reachability, and
guards before changing the map, a lead verdict, or a report. Continue separate
useful work while workers run, and inspect existing job files after an
interruption before creating replacements.

## Standing rules

- Use only your own accounts and test data.
- Never access another person's account or data.
- Do not perform denial-of-service testing, brute force, credential stuffing,
  or account enumeration.
- Stop before any post-exploitation, data modification, or destruction and
  prepare the report.
- Never execute an extracted binary. Any legitimate execution must use a
  controlled, isolated, and explicitly authorized installation.
- Never expose a secret, cookie, token, key, sensitive response body, or player
  data in a command, evidence file, or report.
- Verify the SHA-256 of every artifact loaded into IDA before drawing a
  conclusion.
- Never describe a hypothesis as a vulnerability without runtime evidence when
  that evidence is required to support the claimed impact.

## Lead deliverable

A lead record must include the asset and version, SHA-256, trust boundary,
complete path, prerequisites, expected impact, minimal test, result, limits,
cleanup, links to evidence, and the exact condition for reopening a parked or
dismissed path.
