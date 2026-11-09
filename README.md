# Remotejobb for AI assistants

Search remote and hybrid jobs in Sweden from [Remotejobb.se](https://remotejobb.se) in Claude, ChatGPT, Cursor, VS Code and other MCP clients. Ask in plain language, for example "find remote frontend jobs posted this week" or "which hybrid jobs in Gothenburg pay at least 45,000 SEK a month?", and the assistant searches current listings, reads them in full and gives you the apply links.

This repository contains the Claude plugin (an MCP server configuration and a job search skill) and the metadata for the MCP Registry. The MCP server itself is hosted by Remotejobb at `https://remotejobb.se/mcp`. It is free to use and needs no account or API key.

## What's included

- **MCP server** (`.mcp.json`): connects to `https://remotejobb.se/mcp` over Streamable HTTP. Its tools are read-only:
  - `search_jobs`: search open jobs by keywords, remote or hybrid, where applicants may live, city, category, company, employment type, minimum salary and publish date.
  - `get_job`: read one job in full, with salary, apply link and expiry.
  - `list_search_filters`: list the categories and cities that currently have open jobs.
- **Skill** (`skills/remotejobb-job-search`): guidance for the assistant on running a good job search with these tools.
- **Registry metadata** (`server.json`): the server's entry in the official MCP Registry, as `se.remotejobb/jobs`.

## Install

**Claude Code**

```bash
claude plugin marketplace add remotejobb-se/remotejobb-mcp
claude plugin install remotejobb@remotejobb
```

Or add only the MCP server:

```bash
claude mcp add --transport http remotejobb https://remotejobb.se/mcp
```

**Claude (web, desktop and mobile)**: Settings → Connectors → Add custom connector, and enter `https://remotejobb.se/mcp`.

**ChatGPT**: Settings → Apps. If Remotejobb isn't listed, turn on developer mode under Advanced settings and create an app with the URL `https://remotejobb.se/mcp`.

**Cursor**: add to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "remotejobb": { "url": "https://remotejobb.se/mcp" } } }
```

**VS Code**: add to `.vscode/mcp.json`:

```json
{ "servers": { "remotejobb": { "type": "http", "url": "https://remotejobb.se/mcp" } } }
```

## Data

The plugin connects only to `https://remotejobb.se/mcp`. Each tool call sends that server the arguments the assistant chooses, such as search keywords, filters and job ids, together with information about which assistant app is calling. The skill contains instructions only and runs no code. How Remotejobb processes this data is described in the [privacy policy](https://remotejobb.se/en/privacy), and use of the service is subject to the [terms of use](https://remotejobb.se/en/terms).

## Support

Questions and problems: [hej@remotejobb.se](mailto:hej@remotejobb.se). More about the server: [remotejobb.se/en/ai](https://remotejobb.se/en/ai).

## License

The contents of this repository are licensed under the [MIT License](LICENSE). The Remotejobb service and its listings are not covered by this license; see the terms of use.
