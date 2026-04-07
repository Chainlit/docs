## Project Overview

This is the **Chainlit documentation site**, built with [Mintlify](https://mintlify.com). Chainlit is an open-source Python package for building production-ready Conversational AI applications. This repo contains only the documentation content — not the Chainlit framework source code.

## Development

```bash
# Run local dev server (requires Node.js)
npx mint dev
```

There are no build, lint, or test commands — Mintlify handles building and deployment. Changes pushed to the default branch are deployed to production automatically. PRs generate preview links.

## Architecture

### Content Format

All documentation pages are **MDX files** (Markdown + JSX). They use Mintlify-specific components:

- `<ParamField path="" type="">` — API parameter documentation
- `<Frame>` — media containers (images, video)
- `<CardGroup>` / `<Card>` — linked card grids
- `<Note>`, `<Warning>`, `<Info>` — callout blocks
- `<Tabs>` / `<Tab>` — tabbed content sections
- `<CodeGroup>` — grouped code blocks

Every MDX file begins with YAML frontmatter containing at minimum a `title` field.

### Navigation & Configuration

**`docs.json`** is the single source of truth for:
- Site navigation (tabs, groups, page ordering)
- Redirects (old URL → new URL mappings)
- Theme, colors, logos, external links

**Every new page must be added to `docs.json`** under the appropriate `navigation.tabs[].groups[].pages` array, or it will not appear in the site navigation.

### Content Structure

| Directory | Purpose |
|-----------|---------|
| `get-started/` | Installation, overview, first steps |
| `concepts/` | Core Chainlit concepts (messages, steps, lifecycle, elements, actions) |
| `api-reference/` | Python API reference (decorators, classes, hooks) |
| `api-reference/lifecycle-hooks/` | Lifecycle hook decorators (`on_chat_start`, `on_message`, etc.) |
| `api-reference/elements/` | UI element types (Image, File, Audio, etc.) |
| `api-reference/input-widgets/` | Form input components |
| `api-reference/ask/` | User-input request APIs |
| `advanced-features/` | Streaming, MCP, multi-modal, chat profiles |
| `integrations/` | Framework integrations (LangChain, OpenAI, LlamaIndex, etc.) |
| `deploy/` | Deployment platforms (webapp, React, Copilot, Slack, Discord, Teams) |
| `data-persistence/` | Data storage, history, feedback |
| `data-layers/` | Open-source data layer implementations |
| `authentication/` | Auth methods (password, header, OAuth) |
| `customisation/` | Theming, CSS, JS, avatars, translation |
| `backend/` | Server config (`.chainlit/config.toml`), env variables, CLI |
| `examples/` | Cookbook and example applications |
| `guides/` | Migration guides, sync/async patterns |
| `images/` | Static assets referenced by documentation pages |

### Redirects

When renaming or moving pages, add a redirect entry in `docs.json` under the `redirects` array to avoid broken links:

```json
{
  "source": "/old/path",
  "destination": "/new/path"
}
```

## Conventions

- Python code examples use `import chainlit as cl` (the standard alias)
- Lifecycle hooks are documented both in `concepts/chat-lifecycle.mdx` (conceptual) and `api-reference/lifecycle-hooks/` (API detail)
- British spelling is used for `customisation/` directory naming
- The repo uses `main` as the default branch
