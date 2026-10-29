# Splendorize MCP Server

Connect Splendorize to Claude, Codex, Cursor or any MCP client. Your assistant sees what works on your landing pages, builds the evidence, drafts improvements and experiments, and checks previews before you ship. Every write needs an explicit OAuth scope.

- **Endpoint:** `https://mcp.splendorize.com/mcp` (Streamable HTTP)
- **Auth:** OAuth, sign in with your Splendorize account
- **Website:** https://splendorize.com/mcp
- **Official MCP Registry:** `com.splendorize/mcp`

## What you can do

- Read site intelligence: page-type opportunities, next moves, signal status, landing performance and SEO.
- Build evidence packs and generate improvement suggestions.
- Draft experiments from suggestions and move them through review.
- Scan a preview URL and validate instrumentation before you ship.
- Set up and configure sites, and manage recommendations, experiments, implementation runs and integrations (GitHub, search, revenue).

Customer-facing changes ask for your confirmation in the client. A paid Splendorize plan is required.

## Connect

The server uses OAuth. Your client opens a browser window, you sign in with your Splendorize account and approve access. You do not copy an API key.

### Claude (claude.ai and Claude Desktop)

Open **Settings → Connectors → Add custom connector**, enter `https://mcp.splendorize.com/mcp` and select **Connect**.

### Claude Code

```bash
claude mcp add --transport http splendorize https://mcp.splendorize.com/mcp
```

Then run `/mcp` in Claude Code and authenticate `splendorize`.

### Codex CLI

```bash
codex mcp add splendorize --url https://mcp.splendorize.com/mcp
codex mcp login splendorize
```

### Cursor

Add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "splendorize": { "url": "https://mcp.splendorize.com/mcp" }
  }
}
```

### VS Code

```bash
code --add-mcp '{"name":"splendorize","type":"http","url":"https://mcp.splendorize.com/mcp"}'
```

### Gemini CLI

```bash
gemini mcp add --transport http splendorize https://mcp.splendorize.com/mcp
```

### ChatGPT and other clients

Add a custom connector (in ChatGPT, developer mode) with the URL `https://mcp.splendorize.com/mcp`. Any client that supports Streamable HTTP and MCP OAuth works.

## Tools

Your client always gets the current list and schemas from `tools/list`.

- **Intelligence:** `rank_page_type_opportunities`, `build_evidence_pack`, `generate_suggestion`
- **Drafts and experiments:** `draft_experiment_from_suggestion`, `transition_suggestion`, `manage_experiment`, `manage_recommendation`
- **Preview and checks:** `scan_preview_url`, `validate_instrumentation`, `verify_site_install`
- **Sites and integrations:** `create_site`, `configure_site`, `manage_implementation`, `manage_github_integration`, `manage_search_integration`, `manage_revenue_settings`

Prompts: `draft_landing_page_improvement_brief`, `implement_this_change_safely`, `site_strategy_brief`, `review_preview_against_evidence`. Resources expose sites, dashboards, landing performance, SEO, next moves, recommended changes, evidence, suggestions, experiments and journeys.

## Authentication and account

OAuth 2.1 with PKCE and dynamic client registration. You choose the sites and scopes on the consent screen. Scopes: `read:intelligence`, `read:revenue_aggregate`, `write:drafts`, `write:sites`, `write:recommendations`, `write:experiments`, `write:implementation`, `write:integrations`.

You need a Splendorize account on a paid plan.

## Links

- Website: https://splendorize.com
- MCP setup page: https://splendorize.com/mcp
- Privacy policy: https://splendorize.com/privacy

## About this repository

This repository is the public home of the hosted Splendorize MCP server. It holds this setup guide and the registry metadata (`server.json` for the official MCP Registry, `glama.json` for Glama). The server runs as a hosted service at `https://mcp.splendorize.com/mcp`. Its source code is not in this repository.

Found a problem or have a question? Open an issue.

## License

The contents of this repository are available under the [MIT License](LICENSE).
