---
icon: lucide/id-card
---

# GitHub account

GSEL work happens on GitHub. Set up your account before requesting GSEL sign-in.

## Create or update your account

- Use your university email address for the account.
- Set your GitHub profile name to your English name.
- Verify the university email address in **Settings > Emails**.

## Copilot data setting

If you use an individual Copilot plan, disable model training on your data:

**Settings > Copilot > Allow GitHub to use my data for AI model training > Disabled**

## VS Code telemetry

Set telemetry to off in VS Code. In `settings.json`:

```json
{
  "telemetry.telemetryLevel": "off"
}
```

You can also set this from the Command Palette: run **Preferences: Open User
Settings**, search for `telemetry.telemetryLevel`, and set it to `off`.
