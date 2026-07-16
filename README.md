# Stride Gemini Marketplace

A discovery catalog of [Stride](https://www.stridelikeaboss.com) extensions for the **Gemini CLI** — a task management platform designed for AI agents.

> **Gemini CLI has no native, self-hosted marketplace.** Extensions are installed individually from a GitHub URL with `gemini extensions install <url>`, and the only first-party catalog is Google's own [geminicli.com/extensions](https://geminicli.com/extensions). This repository is therefore a **discovery index** — a human-readable table plus a machine-readable [`extensions.json`](extensions.json) — that points you at each Stride extension and its install URL. Gemini does **not** consume this catalog directly.

## Installing an extension

Install any extension below directly from its GitHub repository using the Gemini CLI:

```bash
gemini extensions install https://github.com/cheezy/stride-gemini
```

### Managing extensions

```bash
gemini extensions list                  # View installed extensions
gemini extensions update stride-gemini  # Pull the latest from the source repo
gemini extensions uninstall stride-gemini
```

## Extensions

| Extension | Version | Install | Description |
|-----------|---------|---------|-------------|
| [`stride-gemini`](https://github.com/cheezy/stride-gemini) | 1.36.0 | `gemini extensions install https://github.com/cheezy/stride-gemini` | Task lifecycle skills and custom agents for Stride kanban — the Gemini CLI extension. Claim, work, review, and complete Stride tasks and goals with workflow enforcement, hook execution, and five custom agents. |

The table above is kept in sync with the machine-readable index in [`extensions.json`](extensions.json).

## Releases and tagging

**Every sync commit gets a tag and a GitHub release, named for the extension version it pins.** The catalog tag mirrors the extension: the commit that pins `stride-gemini` `1.36.0` is tagged `v1.36.0`. That is the convention — `v1.32.0`, `v1.33.0`, `v1.34.0`, `v1.34.1` and `v1.36.0` each sit on their matching `Sync stride-gemini to X` commit.

**These tags are a release record, not a resolution mechanism.** Nothing installs *through* them. `extensions.json` pins each extension by a bare repository URL with no version, tag, or ref — and, as noted at the top of this file, Gemini CLI does not consume this catalog at all. An install resolves to the extension repo's default branch; the catalog's `version` field and this repo's tags exist so a human can see what was pinned when.

### The missing `v1.35.0` — an omission we're accepting, not a lost release

The tag line jumps from `v1.34.1` to `v1.36.0`. The commit that pins `1.35.0` (`098af16`, "Sync stride-gemini to 1.35.0") was committed and pushed during the D144/W1667 cycle but never tagged or released. **That gap is accepted and will not be backfilled.** It is recorded here so the next release engineer does not have to rediscover it:

- **Nothing was affected.** Because the tags resolve no installs, the missing tag cost nothing at the time and costs nothing now. Anyone who installed while `1.35.0` was pinned got the extension's default branch, exactly as they would have with the tag present.
- **Backfilling would be worse than the gap.** A retroactive `v1.35.0` would be dated today against a commit from 2026-07-14, and would point at a pin state that `v1.36.0` has already superseded — manufacturing a release record for a state no user ever resolved through, and misrepresenting the history it claims to document.
- **The convention itself is unchanged.** `v1.35.0` is an omission from one cycle, not a policy. Tag every sync.

The `stride-gemini` extension repo's own `v1.35.0` tag and GitHub release are correct and present — only this catalog's record has the hole.

## License

[MIT](LICENSE) © 2026 Jeff Morgan
