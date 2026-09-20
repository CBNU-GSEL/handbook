---
icon: lucide/box
---

# Create a workspace

Create a personal workspace from the approved **Scratch** template. Use it
for editing, dependency setup, and small local checks.

## From the browser

1. [Sign in to Coder](../onboarding/gsel-sign-in.md).
2. Go to **Templates** and select **Scratch**.
3. Select **Create Workspace**.
4. Choose a workspace name, such as `research-dev`, and submit.
5. Wait for startup to complete, then [open the workspace](open-in-browser.md).

## From the CLI

[Install the Coder CLI and sign in](cli.md), then run:

```bash
coder create research-dev --template Scratch
coder ssh research-dev
```

Replace `research-dev` with your workspace name. Complete any template
prompts shown by the CLI.

A workspace name identifies your development environment. The
[project name](../projects/pixi.md#project-names) identifies the research
project submitted to Gateway.

Stop the workspace from its Coder page when you finish. Save and commit work
before stopping or deleting it; follow the member guide for file retention.
