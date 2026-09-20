# Research Journal

Keep the journal chronological and factual. Add an entry after every useful
action, including negative results and cleanup. Never place secrets, tokens,
cookies, player data, or sensitive response bodies in it.

Each entry records the date, asset and version, evidence type, bounded action,
result, limitation, and next step. Use these labels:

- **Observation**: a fact directly seen or measured.
- **Static**: a conclusion from an artifact identified by its SHA-256.
- **Inference**: an explicitly unconfirmed hypothesis.
- **Runtime**: the result of a controlled and reproducible test.

| Date | Type | Asset / version | Action and result | Limits / next step |
| --- | --- | --- | --- | --- |
| `<YYYY-MM-DD>` | Initialization | Research template | Created the documentation workflow; no testing performed | Record authorization and target, then begin mapping |

## Session closure rule

Before ending a session, record the state of processes, files, and temporary
objects, confirm cleanup, and update `LEADS.md` only for status changes that
the evidence genuinely supports.

End meaningful work with a compact handoff entry:

```markdown
## <YYYY-MM-DD HH:MM timezone> — Handoff

**Target:** <asset and build>
**Active lead:** <identifier or none>
**Confirmed:** <latest reliable result>
**Open question:** <single decisive question>
**Next:** <smallest useful action>
**Do not repeat:** <closed paths and reopening conditions>
**Evidence:** <project-relative paths>
```

On resumption, find the latest `Handoff` heading and read only that bounded
section plus its referenced records. Do not load the complete journal.
