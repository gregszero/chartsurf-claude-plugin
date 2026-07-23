# aliahlp Claude plugin

Connect Claude to [aliahlp](https://alia.help): explore your database schema
and AI catalog, run read-only SQL, and publish live hosted charts and
dashboards — from Slack (Claude in Slack / Claude Tag), Claude Code, or any
MCP client.

The plugin declares aliahlp's remote MCP server (`https://api.alia.help/mcp`).
Authentication is a Bearer API token you create at
[alia.help/tokens](https://alia.help/tokens).

## Use from Slack (Claude in Slack / Claude Tag)

Requires a Claude **Team or Enterprise** plan with Claude Tag enabled. Setup is
done by a claude.ai org owner at
[claude.ai/admin-settings/claude-tag](https://claude.ai/admin-settings/claude-tag):

1. Create an API token at [alia.help/tokens](https://alia.help/tokens) (name it
   e.g. "Slack") and copy it.
2. Open your **Access bundle** → **Credentials** tab → **Connect another
   tool**. Choose the **Bearer** credential type, paste the token, and set
   **Allowed websites** to `api.alia.help`.
3. Register this repository as an organization plugin source (plugin
   marketplace), then on the bundle's **Plugins** tab add the `aliahlp` plugin.
4. In a covered channel, try: `@Claude list my aliahlp connections`

## Use from Claude Code

```sh
claude mcp add --transport http aliahlp https://api.alia.help/mcp \
  --header "Authorization: Bearer alh_..."
```

## Use from claude.ai (also covers Slack DMs)

Slack DMs run on your personal claude.ai account, so add aliahlp there as a
custom connector: claude.ai → **Settings** → **Connectors** → add
`https://api.alia.help/mcp`. It connects via OAuth — no manual token needed.

## What Claude can do once connected

- `list_connections`, `get_schema`, `get_catalog`, `suggest_insights` —
  explore your data and its AI-generated semantic catalog
- `run_query` — read-only SQL (enforced server-side)
- `import_csv` — load a CSV into your hosted workspace
- `create_chart`, `update_chart`, `create_dashboard`, … — publish live charts
  and dashboards hosted at unguessable URLs
