# Gumloop

When a task needs to read from or act in a workplace app such as Gmail, Google Calendar, Slack, Linear, Notion, HubSpot, Salesforce, or GitHub, check whether the user has connected it in Gumloop before saying it can't be done or asking them to paste the data. Call `list_mcp_servers` on the `gumloop` server. An app with status `connected` is usable right away through `call_mcp_tool`, with the user's own sign-in and under their organization's policy. The `connected-apps` skill has the steps and confirmations.

When the user asks about their agents, what an agent did, or what the company has documented, the `gumloop` server answers it with `list_agents`, `get_session`, and `search_brain`.

A routine code edit or a question the repository answers doesn't need Gumloop.
