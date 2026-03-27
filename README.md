<div align="center">

<img src="https://paperoffice.ai/images/logos/paperoffice_ai_logo.svg" alt="PaperOffice AI" width="120">

# PaperOffice MCP Setup

**Connect 357+ AI Tools to your IDE in 30 seconds**

Claude Desktop · Cursor · Windsurf · any MCP client

</div>

---

## What is this?

[PaperOffice AI](https://paperoffice.ai) provides a remote MCP (Model Context Protocol) server with **357+ AI-powered tools** for document processing, OCR, IDP, e-signatures, knowledge graphs, and more.

This repo contains **ready-to-use config files** for all major MCP clients. No local installation needed — just copy, paste, connect.

## Setup

### Claude Desktop

Copy `configs/claude_desktop_config.json` into your Claude Desktop settings, or add this to your existing config:

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/mcp"
    }
  }
}
```

Claude Desktop uses **automatic OAuth 2.1** — no API key needed. You will be prompted to authorize on first use.

### Cursor

Copy `configs/cursor_mcp.json` to `.cursor/mcp.json` in your project root:

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Replace `YOUR_API_KEY` with your Bearer token from [app.paperoffice.ai](https://app.paperoffice.ai).

### Windsurf

Copy `configs/windsurf_mcp_config.json` to `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Same config format as Cursor. Replace `YOUR_API_KEY` with your token.

### Other MCP Clients

Any MCP-compatible client can connect to:

```
https://mcp.paperoffice.ai/mcp
```

- **Auth**: Bearer token (header `Authorization: Bearer YOUR_API_KEY`)
- **Transport**: Streamable HTTP
- **Protocol**: MCP v3.0

## Alternative: Paste Postman URL into AI

Don't need MCP? Just paste this URL into any AI assistant and start coding:

```
https://api.paperoffice.ai/dev/docs/postman
```

The AI reads the full API documentation and writes the code for you. Zero SDKs needed.

## Get Your API Key

1. Go to [app.paperoffice.ai](https://app.paperoffice.ai)
2. Create a free account
3. Generate a Bearer token in the API settings

## What can you do?

Once connected, ask your AI assistant things like:

- *"Extract all data from this invoice"*
- *"OCR this scanned document"*
- *"Classify these 50 documents"*
- *"Split this 200-page PDF by document type"*
- *"Search my knowledge base for GDPR policies"*

357+ tools across Document AI, OCR, IDP, Automation, Agents, Security, Analytics, and more.

## Resources

- [Full MCP Documentation](https://paperoffice.ai/en/developer/mcp/)
- [Postman Collection — paste into AI](https://api.paperoffice.ai/dev/docs/postman)
- [AI Cookbook — Recipes & Prompts](https://paperoffice.ai/en/developer/cookbook/)
- [REST API](https://api.paperoffice.ai)

## License

Configuration files in this repository are provided under [MIT License](LICENSE). The PaperOffice AI platform and API are proprietary — see [paperoffice.ai](https://paperoffice.ai) for terms.
