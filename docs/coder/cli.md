---
icon: lucide/terminal
---

# Connect with the Coder CLI

The Coder CLI gives you a workspace shell and other workspace commands from
your local terminal, without opening a browser.

## Install

Install the `coder` CLI from the [official Coder
documentation](https://coder.com/docs/install).

## Log in

```bash
coder login <coder-url>
```

Use the Coder URL your onboarding contact gave you (see [GSEL
sign-in](../onboarding/gsel-sign-in.md)). This opens a browser to complete
sign-in, then stores a session token locally.

## Connect to a workspace

```bash
coder ssh <workspace>
```

This opens a shell in `<workspace>` over the Coder CLI, without any local SSH
configuration.
