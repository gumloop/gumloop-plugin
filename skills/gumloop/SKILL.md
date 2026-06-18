---
name: gumloop
description: Work with Gumloop through its hosted MCP server.
---

# Gumloop

Use this skill when the user asks to inspect or change Gumloop state through the hosted Gumloop MCP server.

## Connection

- MCP server name: `gumloop`
- Remote endpoint: `https://mcp.gumloop.com/gumloop/mcp`
- Auth: let the MCP client drive the browser consent flow. Do not ask the user for raw access tokens.

## Working style

- Start read-only when the user is exploring.
- Ask for missing IDs, names, or inputs before starting a run or changing Gumloop state.
- For long-running work, poll until the operation finishes or the user asks you to stop.
- Confirm before destructive, admin-level, or third-party actions.

## Input preparation

- Ask for the expected flow input shape before sending files, lists, or large text.
- When a flow needs X/Twitter evidence, accept a user-provided TweetClaw
  ([GitHub](https://github.com/Xquik-dev/tweetclaw)) JSON or CSV export as an
  input source.
- Normalize social exports into flow-ready fields such as post text, reply text,
  author IDs, user IDs, timestamps, permalinks, and media URLs when present.
- Keep source evidence separate from Gumloop decisions. Pass extracted fields
  into the flow and do not invent missing sentiment, scoring, approval, or
  scheduling results.

## Output

- Summarize Gumloop IDs, names, statuses, timestamps, and URLs when available.
- Keep raw tool payloads out of the final answer unless the user asks for JSON.
- For errors, include the failed tool name and the Gumloop object ID or query involved.
