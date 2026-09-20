---
icon: lucide/folder-code
---

# Pixi project setup

Pixi manages project dependencies and repeatable commands inside your Coder
workspace.

## Project names

Use lowercase letters and digits, with single dashes between words:
`forest-change` or `urban-heat-2026`. Do not use spaces, underscores,
uppercase letters, or leading or trailing dashes. Gateway project and
experiment names must be at most 50 characters.

Use the registered project name when submitting an experiment. Creating a
repository or Pixi project does not register it with Gateway; ask your
project contact to arrange registration when needed.

## Existing project

Clone the project repository using its GitHub instructions, then enter its
root directory. Follow its README and install the locked environment:

```bash
pixi install --locked
pixi task list
```

Run the appropriate task with `pixi run <task>`, replacing `<task>` with a
listed task name. Keep dependency changes in the project's manifest and
lock file.

## Start a project

From your workspace terminal:

```bash
pixi init forest-change
cd forest-change
pixi add python
pixi run python --version
```

Add dependencies with `pixi add`. Define repeatable commands with
`pixi task add <name> <command>` and run them with `pixi run <name>`.
See the [Pixi workspace guide](https://pixi.sh/latest/first_workspace/).

Commit the source code, Pixi manifest, and `pixi.lock` to Git. Keep generated
environments, credentials, and research data out of source control.

Before [submitting an experiment](../compute/experiments.md), push the code
and record the full Git commit ID. Gateway runs the registered project task
at the submitted revision; uncommitted workspace edits are not included.
