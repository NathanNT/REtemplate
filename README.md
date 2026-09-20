# Vibe Reverse Engineering Template

This repository is a **starter template** for authorized reverse engineering,
debugging, and security research. It does not contain a target, product
artifact, credential, or confirmed vulnerability.

At the start of a project:

1. Define the exact target, authorization, environment, and operating limits.
2. Configure [`ACCESS.md`](ACCESS.md) locally without recording secrets in it.
3. Begin the component and trust-boundary map in [`MAPPING.md`](MAPPING.md).
4. Record every result in [`JOURNAL.md`](JOURNAL.md) and every hypothesis in
   [`LEADS.md`](LEADS.md).

If the project is governed by a bug bounty or vulnerability disclosure
program, also synchronize [`CONTRACT.md`](CONTRACT.md) with the live policy and
use [`DOCS.md`](DOCS.md) when preparing a submission. These two files are
optional modules and are not part of the default reverse-engineering workflow.

## Structure

| Path | Purpose |
| --- | --- |
| `CONTRACT.md` | Optional bug-bounty/VDP scope and rules |
| `ACCESS.md` | Generic IDA and SSH procedure, with no machines or secrets |
| `AGENTS.md` | Minimal research and validation workflow |
| `MAPPING.md` | Inventory of components, flows, and trust boundaries |
| `DOCS.md` | Optional bug-bounty/VDP report-writing guidance |
| `JOURNAL.md` | Factual research timeline |
| `LEADS.md` | Registry of hypotheses and their status |
| `analysis/` | Static notes and selected disassembly output |
| `extracts/` | Extracted artifacts, never executed directly |
| `reports/` | Lead records, minimal evidence, and final reports |
| `tools/` | Bounded, reproducible scripts with no embedded secrets |

Resume by reading the small canonical indexes and the latest journal handoff;
load access procedures, detailed analysis, and reporting guidance only when
the active task needs them.

This template grants no authorization by itself. Use the authorization and
operating boundaries recorded for the instantiated project. When an external
program governs the work, its current official policy takes precedence.
