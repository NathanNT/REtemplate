# Vibe Reverse Engineering Template

This repository is a **starter template** for authorized security research and
reverse engineering. It does not contain a qualified target, product artifact,
credential, or confirmed vulnerability.

Before any network or dynamic action:

1. Fetch the live bug bounty policy and populate [`CONTRACT.md`](CONTRACT.md).
2. Define the exact authorized asset, accounts, environment, and test limits.
3. Configure [`ACCESS.md`](ACCESS.md) locally without recording secrets in it.
4. Begin the component and trust-boundary map in [`MAPPING.md`](MAPPING.md).
5. Record every result in [`JOURNAL.md`](JOURNAL.md) and every hypothesis in
   [`LEADS.md`](LEADS.md).

## Structure

| Path | Purpose |
| --- | --- |
| `CONTRACT.md` | Working copy of the live official scope and rules |
| `ACCESS.md` | Generic IDA and SSH procedure, with no machines or secrets |
| `AGENT.md` | Minimal research and validation workflow |
| `MAPPING.md` | Inventory of components, flows, and trust boundaries |
| `DOCS.md` | Guidance for writing evidence-backed vulnerability reports |
| `JOURNAL.md` | Factual research timeline |
| `LEADS.md` | Registry of hypotheses and their status |
| `analysis/` | Static notes and selected disassembly output |
| `extracts/` | Extracted artifacts, never executed directly |
| `reports/` | Lead records, minimal evidence, and final reports |
| `tools/` | Bounded, reproducible scripts with no embedded secrets |

This template grants no authorization by itself. The current official policy
and the operator's explicit instructions always take precedence.
