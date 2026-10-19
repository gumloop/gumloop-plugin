# Gumloop

[Gumloop](https://www.gumloop.com) is where teams build and run AI agents for work. This plugin connects Claude, ChatGPT, Codex, and Cursor to your Gumloop account through Gumloop's hosted MCP server, with skills that teach the assistant how to use it.

## What you can do

- **Run agents.** Find an agent by name, start a session, follow up, answer its approval requests, and fetch the files it produced.
- **Build agents.** Create or change an agent's model, prompt, skills, connected apps, and evaluation settings.
- **Use connected apps.** Read from or act in the apps your team has connected in Gumloop (Gmail, Google Calendar, Slack, Linear, Notion, HubSpot, Salesforce, GitHub, and 100+ more) with the sign-in you already completed there, under your organization's access policy. No per-app setup in the assistant.
- **Search Company Brain.** Ask what the company has documented or decided across Notion, Google Drive, Slack, GitHub, Confluence, and uploaded files.

Try: "Which apps are connected to my Gumloop account?", "Ask my Research Assistant agent to summarize the latest quarterly report", "Search my Company Brain for our refund policy".

## Install

| Client | How |
| --- | --- |
| Claude (claude.ai, Cowork, Claude Code) | Add it from the plugin directory, or in Claude Code: `/plugin install gumloop --marketplace gumloop/gumloop-plugin`. Connect the `gumloop` connector on the plugin's Connectors tab. |
| ChatGPT and Codex | Install from the plugin directory, or `codex plugin marketplace add gumloop/gumloop-plugin`. |
| Cursor | Cursor Settings > Plugins > search "Gumloop" > Install, or `/add-plugin gumloop` in chat. |
| Devin (cloud, CLI, Desktop) | Customize > Plugins > Browse marketplace > Gumloop, or `devin plugins install gumloop/gumloop-plugin`. Connect the `gumloop` MCP when prompted. |

The first tool call opens Gumloop's sign-in in your browser. The plugin never asks for an API key.

## What's included

| Path | Purpose |
| --- | --- |
| `skills/` | `gumloop` (shared conventions), `get-started`, `run-agents`, `build-agents`, `connected-apps`, `company-brain` |
| `rules/` | Cursor rule that reminds the assistant to check your Gumloop connections when a task needs another app |
| `plugin.json`, `mcp.json` | Portable Agent Plugins manifest and MCP config, read by ChatGPT and Codex |
| `.claude-plugin/`, `.mcp.json` | Claude manifest, marketplace entry, and MCP config |
| `.cursor-plugin/plugin.json` | Cursor manifest, pointing at `.mcp.json` |
| `.devin-plugin/plugin.json`, `AGENTS.md` | Devin manifest, pointing at `skills/` and `.mcp.json`, and the same connected-apps rule as an always-on Devin rule |

## Data

Every tool call goes to `https://mcp.gumloop.com/gumloop/mcp` over HTTPS with the OAuth token your client obtained from Gumloop. The plugin sends the arguments of each call (agent names and IDs, messages to agents, search queries, and the arguments for a connected-app tool) and receives the results. It contains no scripts, hooks, or local servers, stores nothing itself, and reaches no other host. Calls to connected apps run inside Gumloop with your own connection; the plugin never handles those credentials. Gumloop's [privacy policy](https://www.gumloop.com/privacy-policy) and [terms](https://www.gumloop.com/tos) apply.

## Terminal

The `gumloop` CLI reaches the same account from a shell, with `--json` on every command, and ships its own `gumloop-cli` skill for coding agents. Install and sign-in steps are in the [CLI docs](https://docs.gumloop.com/cli/overview).

## Links

- [Docs](https://docs.gumloop.com) and [MCP server reference](https://docs.gumloop.com/mcp-server/overview)
- [Help center](https://docs.gumloop.com/help) or support@gumloop.com
