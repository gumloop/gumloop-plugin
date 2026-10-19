# Changelog

## 1.1.0

- Add a Devin manifest at `.devin-plugin/plugin.json` pointing at the shared `skills/` directory and `.mcp.json`, so the plugin installs in Devin cloud sessions, the Devin CLI, and Devin Desktop.
- Add `AGENTS.md` at the plugin root with the connected-apps rule, which Devin loads as an always-on rule. The Cursor copy stays in `rules/`.
- Add Devin install steps to the README.

## 1.0.0

- Replace the single `gumloop` skill with six: `gumloop` (shared conventions), `get-started`, `run-agents`, `build-agents`, `connected-apps`, `company-brain`. Each names the Gumloop MCP tools it uses and how to handle `unauthenticated` and `blocked` apps. Flow tools are left out.
- Add a Cursor rule that checks the user's Gumloop connections when a task needs another app.
- Add a portable Agent Plugins manifest at `plugin.json` with the OpenAI listing, onboarding skill, and review metadata, and `mcp.json` in the Agent Plugins MCP format. Remove `.codex-plugin/plugin.json`, which the root manifest replaces.
- Point the Cursor manifest at `.mcp.json` so one MCP config serves Claude, Codex, and Cursor.
- Rename the Codex package from `gumloop-plugin` to `gumloop` to match the Claude and Cursor manifests.
- Rewrite the README for the Claude directory: what the plugin does, how to install it per client, and what data it sends.
- Point agents at the `gumloop` CLI for shell work, and give the `gumloop` skill the connectors, help center, support, status, and trust links to hand to users.

## 0.2.0

- Require Cursor 3.13.0+ so the plugin only installs on clients that support hosted MCP servers with the browser-based connect flow.
- Add `repository` and `tags` metadata for the Cursor Marketplace.
- Refresh all descriptions to match Gumloop's agent platform positioning: agents, skills, sessions, runs, and Company Brain.

## 0.1.0

- Initial release: hosted Gumloop MCP server (`https://mcp.gumloop.com/gumloop/mcp`) with OAuth handled by the MCP client, plus the `gumloop` skill.
