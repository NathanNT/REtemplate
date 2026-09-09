# Research Access

This file describes procedures only. It must not contain machine addresses,
real account names, passwords, or private keys.

## Secrets

Keep real connection settings in a secret manager or in a local file excluded
from version control. Load them into memory only when needed. Never display
them, copy them into a visible command, log them, or include them in evidence.

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

IDA must run in a dedicated analysis VM with no access to production secrets.
Transfer only a copy of an artifact whose SHA-256 has been calculated locally.

Generic procedure:

1. Calculate and record the local SHA-256.
2. Transfer the artifact to the VM through the approved automated channel.
3. Use an explicit remote name that includes the component and version.
4. Open the file in IDA without executing it.
5. Recalculate or verify the SHA-256 in the VM.
6. Draw conclusions only when the hashes match.
7. Export only the functions, references, and pseudocode needed for the work.

If a compatible helper is added under `tools/`, its expected form is:

```text
.\tools\upload-to-ida-vm.ps1 -Path <LOCAL_FILE> -RemoteName <EXPLICIT_NAME> -OpenInGui
```

The VM address, credentials, and keys belong in the helper's local
configuration, never in this document.
