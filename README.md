# chart.surf Claude plugin

Connect Claude to [chart.surf](https://chart.surf): explore your database schema
and AI catalog, run read-only SQL, and publish live hosted charts and
dashboards — from Slack (Claude in Slack / Claude Tag), Claude Code, or any
MCP client.

The plugin declares chart.surf's remote MCP server (`https://api.chart.surf/mcp`).
Authentication is a Bearer API token you create at
[chart.surf/tokens](https://chart.surf/tokens).

## Use from Slack (Claude in Slack / Claude Tag)

Requires a Claude **Team or Enterprise** plan with Claude Tag enabled. Setup is
done by a claude.ai org owner at
[claude.ai/admin-settings/claude-tag](https://claude.ai/admin-settings/claude-tag):

1. Create an API token at [chart.surf/tokens](https://chart.surf/tokens) (name it
   e.g. "Slack") and copy it.
2. Open your **Access bundle** → **Credentials** tab → **Connect another
   tool**. Choose the **Bearer** credential type, paste the token, and set
   **Allowed websites** to `api.chart.surf`.
3. Register this repository as an organization plugin source (plugin
   marketplace), then on the bundle's **Plugins** tab add the `chartsurf` plugin.
4. In a covered channel, try: `@Claude list my chart.surf connections`

## Use from Claude Code

```sh
claude mcp add --transport http chartsurf https://api.chart.surf/mcp \
  --header "Authorization: Bearer cs_..."
```

## Use from claude.ai (also covers Slack DMs)

Slack DMs run on your personal claude.ai account, so add chartsurf there as a
custom connector: claude.ai → **Settings** → **Connectors** → add
`https://api.chart.surf/mcp`. It connects via OAuth — no manual token needed.

## What Claude can do once connected

- `list_connections`, `get_schema`, `get_catalog`, `suggest_insights` —
  explore your data and its AI-generated semantic catalog
- `run_query` — read-only SQL (enforced server-side)
- `import_csv` — load a CSV into your hosted workspace
- `create_chart`, `update_chart`, `create_dashboard`, … — publish live charts
  and dashboards hosted at unguessable URLs
