# GSEL Handbook

Documentation site for the CBNU GSEL research group, built with
[Zensical](https://zensical.org/) and managed locally with
[Pixi](https://pixi.sh/).

Published site: <https://cbnu-gsel.github.io/handbook/>

## Local development

Install [Pixi](https://pixi.sh/latest/#installation), then from the
repository root:

```bash
pixi install --locked
pixi run docs-serve
```

`docs-serve` builds the site and serves it locally with live reload.

## Building and checking

```bash
pixi run docs-build
```

`docs-build` produces a static site in `site/` (untracked).

```bash
pixi run docs-check
```

`docs-check` runs prose style (Vale), spelling (typos), and link
(lychee) checks, then performs a clean build. Run this before opening
a pull request; running `docs-build` separately first is not required.

## Repository layout

- `docs/` — page source (Markdown).
- `zensical.toml` — site configuration and navigation.
- `pixi.toml` / `pixi.lock` — local environment and task definitions.

See [CONTRIBUTING.md](CONTRIBUTING.md) for content guidelines.
