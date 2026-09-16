---
icon: lucide/plug
---

# Connect with SSH

`coder config-ssh` configures your standard SSH client to reach your Coder
workspaces. You can then use `ssh`, `scp`, or an editor's remote-SSH
feature. Standard SSH clients connect through the generated `ProxyCommand`,
which invokes your installed and authenticated Coder CLI.

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

By default, this adds a single wildcard host entry that covers all of your
workspaces, including ones you create later — you do not need to rerun the
command for each new workspace. Connect with a standard SSH client using the
workspace host name, for example:

```bash
ssh <workspace-host>
```

Use `coder config-ssh --no-wildcard` to write a separate host entry per
workspace instead. This suits SSH clients or tools that enumerate
configured hosts rather than matching a wildcard pattern; rerun the command
after creating a workspace to add its entry.
