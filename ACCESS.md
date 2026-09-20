# Research Access

This file describes available tools and environment-specific access
procedures. It must not contain real account names, passwords, private keys,
or other secrets.

Everything explicitly described as available or authorized in this file is
standing operator authorization for agents to access and use it within the
recorded scope, without requesting additional confirmation from the user.

## Secrets

Keep real connection settings in a secret manager or in a local file excluded
from version control. Load them into memory only when needed. Never display
them, copy them into a visible command, log them, or include them in evidence.

## Adding tools

The tools documented here are a starting point, not a closed list. Agents are
encouraged to propose, install, configure, or create a tool when it adds clear
value to the research workflow. Useful additions include tools that unlock a
missing analysis capability, automate a repeated operation, improve
reproducibility, preserve artifact identity, reduce manual error, accelerate a
bounded census or differential, or produce stronger evidence.

Prefer a maintained existing tool when it solves the need well. Add a small
project helper under `tools/` when target-specific orchestration, normalization,
evidence export, or another reproducible operation is the useful
part. Keep the implementation proportional to the research benefit; the
template does not require a new framework or integration layer.

Record a useful addition in this file so another agent can reuse it:

| Tool | Version / source | Location or command | Purpose | Usage notes |
| --- | --- | --- | --- | --- |
| To be added when useful |  |  |  |  |

For downloaded or installed tools, record the source and version when useful.
Keep credentials and private
configuration outside the repository. Update or remove a tool entry when it
is superseded so this file remains an accurate operational inventory.

## SSH

Prerequisites: explicit authorization, a target identified as a controlled
research environment, and a host key verified through an independent channel.

Generic form:

```text
ssh -p <PORT> <USER>@<AUTHORIZED_HOST>
```

Procedure:

1. Load the identity from the secret manager.
2. Compare the host key fingerprint with the approved value.
3. Open the session without passing the secret on the command line.
4. Limit commands to what the active lead requires.
5. Close the session and record only non-sensitive observations.

Never disable host key verification globally.

## IDA

Run IDA locally, in an isolated VM, or through a remote service according to
the target and execution risk. Use the IDA MCP server's supported import and
database-opening operations when available; the template does not assume a
separate upload helper.

Generic procedure:

1. Identify the artifact and import it through the configured MCP workflow.
2. Use a stable explicit name that includes the component and version so an
   existing database can be reused.
3. Open the file in IDA without executing it.
4. Export only the functions, references, and pseudocode needed for the work.

Record a digest when several builds could be confused, a transfer may have
altered the file, or a conclusion or deliverable depends on exact identity.
Reuse an identity already established for an unchanged artifact.

A first open may remain busy while IDA creates the database, performs automatic
analysis, initializes the decompiler, or builds search caches. If the MCP call
times out, inspect the existing sessions and analysis state before retrying;
do not start a duplicate import while the original worker may still be active.
Build optional caches only when the current question needs them.
