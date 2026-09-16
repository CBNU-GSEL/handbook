---
icon: lucide/plug
---

# Connect with SSH

`coder config-ssh` configures your standard SSH client to reach your Coder
workspaces, so you can use `ssh`, `scp`, or an editor's remote-SSH feature
directly, without the `coder` CLI in the loop.

## Prerequisites

Install the `coder` CLI and log in first; see [connect with the Coder
CLI](cli.md).

## Preview the change

```bash
coder config-ssh --dry-run
```

This prints the SSH configuration entries `config-ssh` would add, without
writing them.

## Configure your SSH client

```bash
coder config-ssh
```

This adds a host entry for each of your workspaces to your local SSH
configuration. Once configured, connect with a standard SSH client using the
host name it printed, for example:

```bash
ssh <workspace-host>
```

Re-run `coder config-ssh` after creating a new workspace to add its entry.
