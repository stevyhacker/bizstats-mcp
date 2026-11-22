# BizStats.me MCP Server

[![BizStats.me MCP connector](https://glama.ai/mcp/connectors/me.bizstats/mcp/badges/score.svg)](https://glama.ai/mcp/connectors/me.bizstats/mcp)

Public, read-only remote [Model Context Protocol](https://modelcontextprotocol.io) server for Montenegro company financial statements, CRPS business registry records, public procurement tenders, and Ministry of Finance state treasury payments.

- **Endpoint:** `https://api.bizstats.me/mcp`
- **Transport:** Stateless Streamable HTTP (`POST` with JSON responses)
- **Authentication:** None (no account or API key required)
- **Official Registry ID:** `me.bizstats/mcp`
- **REST API & OpenAPI:** `https://bizstats.me/en/api/` · `https://api.bizstats.me/v1/openapi.json`
- **LLM Reference:** `https://bizstats.me/llms.txt` · `https://bizstats.me/llms-full.txt`

## Connect

### Claude Desktop / Cursor / Windsurf

```json
{
  "mcpServers": {
    "bizstats": {
      "type": "http",
      "url": "https://api.bizstats.me/mcp"
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http bizstats https://api.bizstats.me/mcp
```

### Codex CLI

```bash
codex mcp add bizstats --url https://api.bizstats.me/mcp
```

### Test with MCP Inspector

```bash
bunx @modelcontextprotocol/inspector --transport http --server-url https://api.bizstats.me/mcp
```

## Available tools (10)

| Tool | What it returns |
| --- | --- |
| `search_companies` | Search 50,000+ Montenegrin entities by name, PIB tax ID, municipality, or NACE activity code |
| `get_company` | Multi-year financial statements (revenue, net profit, assets, headcount), CRPS officers and owners, tax-debt and blocked-account flags, and linked tenders |
| `rank_companies` | Rank companies by revenue, net profit, profit margin, assets, or employees with year, sector, and municipality filters |
| `search_tenders` | Search Montenegro public procurement notices (CeJN) by keyword, buyer, supplier PIB, CPV code, status, or value |
| `get_tender` | Full details, lots, awards, and linked entities for a single public tender |
| `search_public_payments` | Search state treasury disbursements by recipient, PIB, ministry, or date window |
| `find_person` | Find founders, directors, and beneficial owners across Montenegrin companies |
| `get_person` | Full list of active and historical company roles for a person slug |
| `get_recent_changes` | Recent registry updates, newly filed statements, and account-blockade events |
| `get_dataset_status` | Coverage counts and last-updated timestamps across all ingested public datasets |

Every tool response includes source URLs, access date, and CC BY 4.0 attribution metadata so agents can cite each figure.

## Rate limits and data caveats

- **Limits:** 60 requests per minute per client, 1,200 requests per minute global.
- **Data scope:** Publicly available official records from Montenegro Tax Administration (IRMS), Central Registry of Business Entities (CRPS), Electronic Public Procurement (CeJN), Central Bank blocked-account lists (CBCG), and Ministry of Finance treasury exports.
- **Issues:** Open an issue in this repository if you spot a broken tool response, schema mismatch, or missing public field.
