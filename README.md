<div align="center">

<img src="assets/logo.png" alt="PaperOffice AI" width="300" />

# PaperOffice MCP Server

**Give your AI assistant access to your documents — in plain language, in under 60 seconds.**

Search, read, OCR, classify, extract, sign and analyse documents straight from
Claude, Cursor, ChatGPT or Windsurf. No SDK, no boilerplate, no local install.

[![Model Context Protocol](https://img.shields.io/badge/Model_Context_Protocol-ready-2563eb)](https://paperoffice.ai/en/developer/mcp/)
[![MCP tools](https://img.shields.io/badge/MCP_tools-350%2B-7c3aed)](https://paperoffice.ai/en/developer/mcp/)
[![Hosting](https://img.shields.io/badge/Hosting-EU_Tier_III-009e60)](https://paperoffice.ai/en/company/security/)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.1_+_Bearer-ea580c)](https://paperoffice.ai/en/developer/mcp/)

**[Get started free →](https://app.paperoffice.ai)** · [Documentation](https://paperoffice.ai/en/developer/mcp/) · [Live Postman](https://api.paperoffice.ai/latest/docs/postman)

</div>

---

## Why this matters

Your documents live in a DMS. Your AI assistant lives in your IDE or chat window.
PaperOffice connects the two through the **Model Context Protocol** — so you can
just *ask*, and the model does the work across every authorized workspace.

```text
"List all unpaid invoices across my workspaces, with totals and overdue flags."
"OCR this scanned contract and extract the signing date and parties."
"Classify these 50 documents and file them by type."
```

No prompt engineering, no API code — the model picks the right PaperOffice tool and runs it.

---

## 60-second setup

### 1 · Get a token

Sign up free at **[app.paperoffice.ai](https://app.paperoffice.ai)** → **Settings → API → Generate token**.

### 2 · Paste one URL into your client

**Claude Desktop** (OAuth — no key needed) — [`configs/claude_desktop_config.json`](configs/claude_desktop_config.json)

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/claude"
    }
  }
}
```

**Cursor** — copy [`configs/cursor_mcp.json`](configs/cursor_mcp.json) to `.cursor/mcp.json`

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/cursor",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Windsurf** — same as Cursor, copy [`configs/windsurf_mcp_config.json`](configs/windsurf_mcp_config.json) to `~/.codeium/windsurf/mcp_config.json`.

**ChatGPT / OpenAI MCP** — [`configs/openai_mcp.json`](configs/openai_mcp.json) (`/openai`).

### 3 · Ask away

That's it — your AI now works with your documents.

---

## Which URL should I use?

Each client maps to a curated tool profile, so you only expose what you need.

| Your client | URL | Tools | Auth |
|-------------|-----|------:|------|
| **Claude Desktop** | `https://mcp.paperoffice.ai/claude` | 151 | OAuth 2.1 or Bearer |
| **Claude Code** | `https://mcp.paperoffice.ai/dms` | 151 | Bearer |
| **Cursor IDE** | `https://mcp.paperoffice.ai/cursor` | 37 | Bearer |
| **Windsurf** | `https://mcp.paperoffice.ai/cursor` | 37 | Bearer |
| **ChatGPT / OpenAI** | `https://mcp.paperoffice.ai/openai` | ~112 | Bearer or OAuth |
| **Read-only default** | `https://mcp.paperoffice.ai/mcp` | 37 | Bearer |
| **Power / full surface** | `https://mcp.paperoffice.ai/mcp-full` | 350+ | Bearer |
| **Strict tool budget** | `https://mcp.paperoffice.ai/mcp-fast` | 25 | Bearer |

**Module paths** for explicit scopes:
`https://mcp.paperoffice.ai/mcp-document-ai` (~95 tools) ·
`https://mcp.paperoffice.ai/mcp-workflow-ai` (~56 tools)

Ready-made config files for every profile are in [`configs/`](configs/).

---

## What you can do

| Area | Examples |
|------|----------|
| **Document AI / IDP** | Zero-shot extraction, classification, document chat, PII redaction |
| **OCR** | 120+ languages, layout-aware, searchable PDF & Markdown output |
| **Headless DMS** | Search, read, upload, move, version, tag, sign |
| **Workflow AI** | Tasks, human-in-the-loop approvals, process automation |
| **Intelligence** | Knowledge graph, entities, analytics, BI dashboards |

---

## Why PaperOffice

- **EU-sovereign** — own Tier III data centres in Spain & Germany. GDPR-aligned, no mandatory US cloud.
- **Zero-shot IDP** — extraction without template training, powered by specialized LLMs.
- **Pay-per-use** — transparent credits, no per-seat lock-in.
- **API-first** — 357+ REST endpoints behind the same Bearer token (see [Postman](https://api.paperoffice.ai/latest/docs/postman)).
- **24+ years** — document management since 2002.

---

## Prefer plain REST?

Paste this into any AI assistant for the full API — it reads the docs and writes the code:

```text
https://api.paperoffice.ai/latest/docs/postman
```

Machine-readable context: [paperoffice.ai/llms.txt](https://paperoffice.ai/llms.txt) ·
[api.paperoffice.ai/latest/docs/llms.txt](https://api.paperoffice.ai/latest/docs/llms.txt)

---

## Technical notes

- **Transport:** Streamable HTTP (remote MCP) — no stdio, no local process
- **Base host:** `mcp.paperoffice.ai`
- **Auth:** `Authorization: Bearer <token>`, or OAuth 2.1 for Claude Desktop
- **357+ REST endpoints** and **350+ MCP tools** are counted separately — the full MCP surface is `/mcp-full`

---

## Resources

- [MCP documentation](https://paperoffice.ai/en/developer/mcp/)
- [Live Postman collection](https://api.paperoffice.ai/latest/docs/postman)
- [AI Cookbook — recipes & prompts](https://paperoffice.ai/en/developer/cookbook/)
- [REST API](https://api.paperoffice.ai)

---

## License

Config files in this repository are [MIT](LICENSE). The PaperOffice AI platform and API
are proprietary — see [paperoffice.ai](https://paperoffice.ai) for terms.
