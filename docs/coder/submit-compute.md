---
icon: lucide/play
---

# Submit a compute run

Run these commands in the terminal of your **GSEL Workspace**, opened through
[the browser](open-in-browser.md) or [SSH](ssh.md). If `gsel-compute` is missing,
ask your support contact for the approved workspace version.

## Sign in as part of the command

Check the available tasks and resource choices:

```bash
gsel-compute capabilities
```

The command shows a sign-in link. Open it in your browser, sign in with your
GSEL account, and approve the request. If a code is shown separately, enter it
on that page. Return to the workspace terminal and wait for the command to
finish. You do not copy an access token or run a separate login command.

This terminal illustration shows where to act; the link and code come from
your own command:

```text
GSEL Workspace terminal
┌───────────────────────────────────────────────────────┐
│ $ gsel-compute capabilities                            │
│ Authorize the GSEL Compute Gateway in a browser:       │
│                                                       │
│   [Open the sign-in link shown here]                   │
│   code: [Enter the code if one is shown]               │
│                                                       │
│ Waiting for approval...                               │
└───────────────────────────────────────────────────────┘
           1. Open link → 2. Approve → 3. Return here
```

Each command asks for approval when needed by the sign-in flow. Credentials
stay in the command's memory and disappear when it exits; there is no saved
login file.

## Submit your request

Use a `SubmissionRequest@0.2` JSON request for an approved task and source commit.
Your project instructions provide its repository, task and supported settings.
Keep that request in `request.json` and run:

```bash
gsel-compute submit request.json
```

Approve the browser prompt. The terminal prints a request key before sending
and a run ID after acceptance:

```text
request_key: user-example
run_id: run-example
```

Save those two identifiers. They are not credentials. An accepted request is
not a completed run. Use the returned run ID to check progress and output:

```bash
gsel-compute status run-example
gsel-compute logs run-example
```

Replace `run-example` with your run ID. Read the output promptly after completion.

## Check a CPU smoke run

For a coordinated acceptance check, ask your support contact for the approved
CPU demo source commit. Set `CPU_DEMO_COMMIT` to that full commit, then run:

```bash
gsel-compute smoke --commit "$CPU_DEMO_COMMIT"
```

The command signs in, checks access, submits one CPU run, and waits for its
result. Success ends with:

```text
PASS: succeeded; source, checksum, CPU quota and memory limit match
```

## If a command stops

If sign-in is denied or expires before submission, start the command again.
If a request key was printed but no run ID arrived, keep that key and contact
support before submitting again. Do not create a second run to test whether the
first request arrived.

If a run ID was printed, check that run with `status`. Share the request key,
run ID and error verdict with support. Never share a credential or browser code.
