# Reports and Evidence

- `potential-vulnerabilities/`: concrete static paths and bounded test plans.
- `runtime-validations/`: confirmed or disproved runtime results.
- `evidence/`: minimal, redacted evidence correlated with a specific test.

Use the stable filename stem defined in `../LEADS.md` across each phase. Final
submission drafts use `<LEAD-ID>-<short-kebab-case-title>-final.md` directly
under `reports/`. Evidence uses
`<LEAD-ID>-E<NN>-<short-description>.<extension>` and must be indexed in
`evidence/README.md`.

Do not store secrets, cookies, tokens, personal data, or sensitive raw
responses in these directories.
