---
name: run-agents
description: Runs a Gumloop agent, continues its session, checks a session, answers its approval requests, and fetches files it produced. Use when the user names one of their Gumloop agents, says "ask my agent" or "run the X agent", asks what an agent did or whether a run finished, or needs an agent's output file.
---

# Run agents

## Find the agent

`list_agents` with `search`. On several matches, ask. `get_agent` shows the model, system prompt, skills, and connected apps; use it to say what the agent will do before running it.

## Sessions

| Do | Tool | Note |
| --- | --- | --- |
| Start | `create_agent_session` (`agent_id`, `message`) | Returns the finished response. `input` carries structured inputs the agent declares. |
| Follow up | `send_session_message` (`session_id`, `message`) | |
| Check | `get_session` (`session_id`) | After a timeout, or for a session started in Gumloop, Slack, or by a trigger. |
| Stop | `cancel_session` | Ask first. |
| Rename | `rename_session` | |
| Browse | `list_agent_sessions` (`agent_id`) | `state` is one of `idle`, `queued`, `processing`, `approval_required`, `completed`, `failed`. |

Use sessions, not `start_agent` and `get_agent_status`.

## Approvals

State `approval_required` means the agent is waiting on a person. `get_session` lists the asks under `pending_approvals`. Show each ask (what, to whom) and wait for the user's answer. Then `resolve_session_approvals` with one entry per `action_request_id`: `action` `accept` or `reject`, `reason` on a rejection, `response.values` when the agent asked a question. Never accept for the user.

## Files

`list_agent_artifacts` (`agent_id`, optional `session_id`, `search_query`), then `download_artifact` (`artifact_id`) for a signed URL. Give the URL; don't fetch the file.

## Reply

The agent's answer, the session state, and artifact names with URLs.
