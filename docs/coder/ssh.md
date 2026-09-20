---
icon: lucide/plug
---

# Connect with SSH and a desktop editor

[Install the Coder CLI and sign in](cli.md) on your local computer.
`coder config-ssh` configures your SSH client to reach your workspaces through
the Coder CLI using `ProxyCommand`.

## Configure SSH

Preview the configuration change, then apply it:

```bash
coder config-ssh --dry-run
coder config-ssh
```

The default wildcard entry covers your workspaces, including those created
later. Connect using the workspace alias shown by Coder:

```bash
ssh <workspace-host>
```

Replace `<workspace-host>` with that alias. For editors that list individual
SSH entries, generate one entry per workspace:

```bash
coder config-ssh --no-wildcard
```

Rerun that command after creating another workspace. See the
[Coder SSH configuration reference](https://coder.com/docs/reference/cli/config-ssh)
for options.

## Open in a desktop editor

1. Install [Remote - SSH for VS Code](https://code.visualstudio.com/docs/remote/ssh)
   on your local computer.
2. Run **Remote-SSH: Connect to Host** from the Command Palette and select or
   enter the workspace alias.
3. Open your project folder in the remote window.

Keep the local Coder CLI installed and signed in. Terminals in the remote
window run inside your workspace. Use the same
[Pixi project](../projects/pixi.md) and [workspace tools](tools.md) as you
would in the browser.
