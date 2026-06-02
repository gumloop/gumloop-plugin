# Gumloop plugin

Hosted Gumloop MCP support for Codex, Cursor, and Claude Code.

MCP endpoint:

```text
https://mcp.gumloop.com/gumloop/mcp
```

Authentication is handled by the MCP client. No local server or API key setup is required.

## What is included

```text
gumloop-plugin/
|-- .codex-plugin/plugin.json       # Codex plugin metadata
|-- .claude-plugin/plugin.json      # Claude Code plugin metadata
|-- .cursor-plugin/plugin.json      # Cursor plugin metadata
|-- .mcp.json                       # Codex and Claude Code MCP config
|-- mcp.json                        # Cursor MCP config
|-- LICENSE                         # MIT license
|-- skills/gumloop/SKILL.md         # Agent guidance for Gumloop tasks
`-- assets/                         # Gumloop logo assets
```

## Local use

### Claude Code

```bash
claude --plugin-dir ./gumloop-plugin
```

### Cursor

Cursor loads `.cursor-plugin/plugin.json`, which points at `mcp.json`.

### Codex

The Codex files are `.codex-plugin/plugin.json`, `.mcp.json`, and `skills/gumloop/SKILL.md`.
