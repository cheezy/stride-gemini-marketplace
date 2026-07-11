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
| [`stride-gemini`](https://github.com/cheezy/stride-gemini) | 1.34.1 | `gemini extensions install https://github.com/cheezy/stride-gemini` | Task lifecycle skills and custom agents for Stride kanban — the Gemini CLI extension. Claim, work, review, and complete Stride tasks and goals with workflow enforcement, hook execution, and five custom agents. |

The table above is kept in sync with the machine-readable index in [`extensions.json`](extensions.json).

## License

[MIT](LICENSE) © 2026 Jeff Morgan
