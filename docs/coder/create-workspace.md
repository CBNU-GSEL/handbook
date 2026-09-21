---
icon: lucide/box
---

# Create a workspace

Coder workspaces are built from templates. The approved template for GSEL
workspaces is **GSEL Workspace** (CLI identifier `Scratch`).

## From the browser

1. Sign in to Coder (see [GSEL sign-in](../onboarding/gsel-sign-in.md)).
2. Go to **Templates** and select **GSEL Workspace**.
3. Select **Create Workspace**.
4. Name the workspace and submit.

## From the CLI

```bash
coder create <workspace> --template Scratch
```

Replace `<workspace>` with a name for your workspace. The CLI prompts for any
remaining template options.
