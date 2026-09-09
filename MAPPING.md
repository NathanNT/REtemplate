# Initial Mapping

## Objective

Build a verifiable view of the components under review, their inputs,
privileges, and trust boundaries before attempting any vulnerability
validation.

## Quick start

1. List the authorized artifacts: native applications, managed applications,
   servers, launchers, web properties, APIs, plugins, or update packages.
2. For each artifact, record its provenance, version, date, size, format,
   architecture, and SHA-256.
3. Inventory entry points: files, archives, manifests, IPC, sockets, HTTP,
   WebSocket, QUIC, RPC, serialization, plugins, and updates.
4. Identify identities and privileges: local user, application account,
   untrusted peer, official service, privileged process, and backend.
5. Trace flows from a controllable input through parsing, authentication or
   authorization guards, consumers, and storage.
6. Label every assertion as an observation, static analysis, inference, or
   runtime result.
7. Link every lead to the mapping entry that supports its reachability.

## Inventory

| Component | Version / build | Provenance | SHA-256 | Role | Analysis status |
| --- | --- | --- | --- | --- | --- |
| To be completed |  |  |  |  | Not started |

## Surfaces and boundaries

| Surface | Controllable input | Expected guard | Consumer | Sensitive data or privilege | Evidence |
| --- | --- | --- | --- | --- | --- |
| To be completed |  |  |  |  |  |

## Typical flow

```text
Low-privileged caller
  -> authorized entry point
  -> parsing and normalization
  -> authentication
  -> object-level authorization
  -> privileged consumer
  -> sensitive effect or data
```

Do not infer that a component is exposed merely because it is present in an
artifact. Confirm that it is active and reachable in an authorized environment
before promoting a lead.
