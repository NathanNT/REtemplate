# Agent Workflow

## Resume order

Read these files in order:

1. `README.md`
2. `CONTRACT.md`
3. `ACCESS.md`
4. `MAPPING.md`
5. `DOCS.md`
6. `JOURNAL.md`
7. `LEADS.md`

Read `CONTRACT.md` again before every new network or runtime phase. Read
`ACCESS.md` again before any SSH or IDA access.

## Minimal workflow

1. Identify the exact asset and confirm that it is currently in scope.
2. Acquire the artifact from a legitimate source and record its version,
   provenance, size, and SHA-256.
3. Map formats, processes, protocols, inputs, and trust boundaries before
   looking for an exploitable primitive.
4. Explicitly distinguish observations, static analysis, inferences, and
   runtime validation.
5. Create a lead only when a caller, input, guard, consumer, and plausible
   impact can be connected.
6. Prepare the smallest test that can confirm or disprove the hypothesis.
7. Perform runtime testing only when it complies with the contract, scope, and
   the operator's explicit limits.
8. Retain only necessary evidence, clean up temporary objects, and update the
   journal, map, and leads.

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
cleanup, and links to evidence.
