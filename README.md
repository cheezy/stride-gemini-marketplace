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
| [`stride-gemini`](https://github.com/cheezy/stride-gemini) | 1.40.1 | `gemini extensions install https://github.com/cheezy/stride-gemini` | Task lifecycle skills and custom agents for Stride kanban — the Gemini CLI extension. Claim, work, review, and complete Stride tasks and goals with workflow enforcement, hook execution, and five custom agents. Optionally integrates the stride-gemini-exploratory-testing and stride-gemini-security-review extensions for gated manual testing and a deep security-considerations review. |
| [`stride-gemini-exploratory-testing`](https://github.com/cheezy/stride-gemini-exploratory-testing) | 0.1.0 | `gemini extensions install https://github.com/cheezy/stride-gemini-exploratory-testing` | Skilled human-style exploratory testing for Stride kanban — the Gemini CLI extension. Charter, explore, and debrief time-boxed exploratory-testing sessions against a running app, using heuristics, oracles, and SBTM session discipline to discover the risks and bugs scripted checks miss. |
| [`stride-gemini-security-review`](https://github.com/cheezy/stride-gemini-security-review) | 0.1.1 | `gemini extensions install https://github.com/cheezy/stride-gemini-security-review` | AI-powered security review for code changes on Stride kanban — the Gemini CLI extension. Semantic-analysis vulnerability detection over a diff or the full tree, seven framework rule packs plus CI/CD and web defense-in-depth coverage, MAESTRO agentic-AI classification, SARIF output, severity gating, and a considerations mode that verifies a task's security_considerations were actually mitigated by the diff. |

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

### `v1.37.0` names the exploratory-testing add, so the 1.37.0 `stride-gemini` pin is tagged `v1.38.0`

The catalog tag `v1.37.0` does **not** pin `stride-gemini` 1.37.0 — it marks the commit that *registered* the `stride-gemini-exploratory-testing` extension while `stride-gemini` was still pinned at 1.36.0. That release borrowed the next number in the catalog's own sequence rather than mirroring a `stride-gemini` bump, so when `stride-gemini` genuinely reached 1.37.0 its pin could no longer take the matching tag.

**The 1.37.0 `stride-gemini` pin is therefore tagged `v1.38.0`, not `v1.37.0`.** This is a one-time break from the mirror convention, recorded here so the next release engineer does not read it as an error:

- **The catalog's tag sequence — not the extension version — is authoritative once a number is used.** `v1.37.0` is already a real, different release; the next sync simply takes the next free number (`v1.38.0`). The `version` field inside `extensions.json` still reads the true pinned extension version (`1.37.0`) — only the git tag diverges.
- **Nothing resolves through the tag**, so the divergence costs nothing at install time (see the convention note above) — it only touches the human-readable release record, which this note reconciles.
- **The mirror convention still holds going forward** wherever the number is free. Tag every sync; take the next free number only when the mirrored one is already used. (This section originally illustrated that rule with "a future `stride-gemini` `1.39.0` pin should be tagged `v1.39.0`" — that example has since been overtaken by events, as the next section records.)

### `v1.39.0`–`v1.41.0` were already spent, so the 1.39.0 `stride-gemini` pin is tagged `v1.42.0`

The divergence above was not one-time after all. By the time `stride-gemini` reached 1.39.0, the catalog's own sequence had run three numbers past it — and only one of the three was a `stride-gemini` sync:

- `v1.39.0` registered `stride-gemini-security-review` 0.1.0 (before the 1.38.0 pin, not between the two `stride-gemini` pins).
- `v1.40.0` **is** the `stride-gemini` 1.38.0 pin — it took the next free catalog number rather than its mirrored `v1.38.0`, which the preceding section had already spent.
- `v1.41.0` synced `stride-gemini-security-review` to 0.1.1. This is the only release that genuinely falls between the 1.38.0 and 1.39.0 `stride-gemini` pins.

**The 1.39.0 `stride-gemini` pin is therefore tagged `v1.42.0`, not `v1.39.0`** — the next free number, exactly as the governing rule prescribes:

- **The rule held; only the illustration failed.** The preceding section's rule ("take the next free number only when the mirrored one is already used") produced the right answer here. Its worked example did not, because it named a specific future number the catalog then spent. That example has been made version-neutral above.
- **The `version` field in `extensions.json` still reads the true pinned extension version** (`1.39.0`). Only the git tag diverges, and nothing resolves through the tag.
- **Expect the gap to widen, not close.** Every companion-extension release consumes a catalog number without a matching `stride-gemini` bump, so the catalog tag will keep drifting ahead. Read the tag as a catalog sequence number, and `extensions.json` as the record of what is pinned.

### The 1.40.1 `stride-gemini` pin is tagged `v1.44.0` — the mirrored number is free, but it is *behind* the sequence

The gap has now widened far enough to produce a case the notes above did not anticipate. `stride-gemini` 1.40.1 is a patch release, and its mirrored catalog tag would be `v1.40.1` — a number that is genuinely **free**, since the catalog has `v1.40.0` but never spent `v1.40.1`.

**The 1.40.1 pin is nevertheless tagged `v1.44.0`**, the next number after `v1.43.0` (the 1.40.0 pin):

- **"Next free" has always meant next free *going forward*.** Every episode above resolved to a number higher than the previous tag — `v1.38.0`, `v1.40.0`, `v1.42.0`. A `v1.40.1` tag created today would sit four releases behind `v1.43.0` in a sequence the notes above call authoritative, so a reader sorting tags would see the newest pin appear older than the one it supersedes. The rule's purpose is a legible release record; reusing a number from behind the head defeats it.
- **A free mirrored number is not sufficient on its own.** Read the governing rule as: mirror the extension version when that number is both free *and* ahead of the current head; otherwise take the next number after the head. The earlier sections never had to say the second half because the drift had not yet passed a patch-level number.
- **`extensions.json` still reads the true pinned extension version** (`1.40.1`). Only the git tag diverges, and nothing resolves through the tag.

## License

[MIT](LICENSE) © 2026 Jeff Morgan
