# Contributing

Thanks for improving the GSEL Handbook. This repository is public, so keep
the following in mind before opening a pull request.

## Language

Write in US English. `pixi run docs-check` runs Vale and typos to catch
spelling and common style issues; fix anything it flags before requesting
review.

## Page purpose

Each page should have a clear, single purpose that matches its place in the
navigation (see `zensical.toml`). Prefer short, focused pages over long
pages that mix several topics. If a page grows unfocused, split it.

## Public-safe content

This repository is public. Do not add:

- Private repository content, or links to private repositories.
- Internal or non-public URLs.
- Node names, hostnames, IP addresses, or other hardware/infrastructure
  identifiers.
- Kubernetes topology, cluster layout, or other operational detail.
- Operator-only instructions or credentials.

If a page needs to reference internal systems, describe the concept at a
level safe for a public audience and point readers to the appropriate
internal or private documentation instead of duplicating it here.

## Comments and prose

- Write prose for readers, not for a future editor: avoid comments-in-prose
  like "TODO" or "fix me" in published pages.
- Use [Mermaid](https://zensical.org/docs/authoring/diagrams/) for diagrams
  instead of images where practical, since diagrams stay text-diffable.
- Keep formatting close to Zensical defaults; avoid custom CSS, JavaScript,
  or animation.

## Before opening a pull request

```bash
pixi install --locked
pixi run docs-check
```

`docs-check` must pass locally before requesting review; the same checks
run in CI on every pull request.
