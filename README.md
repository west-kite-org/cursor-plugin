# West Kite

Cursor plugin that connects agents to [West Kite](https://westkite.com) through its remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

West Kite has sourced public records on 141 million US properties in all 50 states and Washington, DC: owners and the people behind LLCs, sales and comparables, mortgages and CMBS loans, assessments, permits, zoning, site risks, and the power, businesses and people nearby. Every fact cites the record it came from.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **West Kite**.
3. Click **Install**, then sign in to West Kite when Cursor asks.

Or run `/add-plugin west-kite` in chat.

## MCP

```json
{
  "mcpServers": {
    "west-kite": {
      "type": "http",
      "url": "https://app.westkite.com/mcp"
    }
  }
}
```

Sign-in is OAuth against West Kite. Cursor opens the West Kite sign-in page when the plugin connects. There is no API key or client ID to configure.

## Before you connect

You need a West Kite account. It's free to start, with no card needed. Some reads and owner research use plan credit.

## What agents can do

| Task | Tools |
| --- | --- |
| Find a property by address, APN, building, place or owner | `search` |
| Read owner, sales, assessments, loans, zoning, permits and planning | `get`, `fetch` |
| List properties, sales, permits, loans, tax notices, listings and businesses in a market | `find` |
| Count matches and rank the biggest owners | `find` with `count` or `group_by` |
| Comparable sales and similar properties | `find` near a property, `similar` |
| Export a whole result set as a CSV with its total and sources | `export` |
| Screen a site for flood, wildfire, contamination, incentives and buildability | `report` (site) |
| Demographics for a county, city, ZIP code or radius | `report` (demographics) |
| Substations, rail, highways, water and more at or near a place | `lookup`, `catalog` |
| Check what each state and county publishes | `coverage` |
| Find the people behind an LLC | `research` |

The hosted server is the source of truth for tool names and schemas.

The plugin also includes a skill, `west-kite-property-research`, that tells the agent which tool to use and how to cite answers.

## Notes

- Every tool reads data, except `research`, which starts owner research when you ask.
- When a county doesn't publish a field, West Kite says so instead of guessing or showing zero.
- Tool calls run as the West Kite member who signed in.
- West Kite hosts the server; this plugin doesn't run anything locally.
- Disconnect at any time from Cursor's MCP settings or your West Kite account.

## Example prompts

- Who owns 550 Madison Avenue in New York, what did they pay, and what loans are recorded on it?
- Find industrial land over 20 acres in Maricopa County, then list the substations near the largest sites.
- Screen this site for flood risk, contamination and Opportunity Zones.
- Who are the largest industrial owners in Dallas County, Texas?
- Export every retail property sold in the last 5 years in Fulton County, Georgia.

## Docs

- West Kite MCP: https://westkite.com/mcp
- Support: hello@westkite.com
- Privacy: https://westkite.com/privacy
- Server URL: https://app.westkite.com/mcp

## License

MIT
