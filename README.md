# PaperOffice MCP Setup

**Connect 350+ MCP tools to Claude, Cursor, ChatGPT or Windsurf in under 60 seconds.**

Marketing / copy-paste configs only — the live MCP server runs at [mcp.paperoffice.ai](https://mcp.paperoffice.ai).  
Canonical product docs: [paperoffice.ai/en/developer/mcp/](https://paperoffice.ai/en/developer/mcp/)

---

## What is this?

[PaperOffice AI](https://paperoffice.ai) provides a **remote** MCP (Model Context Protocol) server — no npm, no Docker, no local install.

| Metric | Count | Notes |
|--------|------:|-------|
| **MCP tools (full profile)** | **350+** | `/mcp-full` — all MCP-enabled tools |
| **Headless DMS profile** | **151** | `/dms` and `/claude` (alias) |
| **REST API endpoints** | **357+** | Separate from MCP — use [Postman](https://api.paperoffice.ai/latest/docs/postman) |
| **Cursor / read-only** | **37** | `/cursor` or `/mcp` |
| **ChatGPT profile** | **~112** | `/openai` — Document AI + Workflow AI |
| **Fast profile** | **25** | `/mcp-fast` — minimal tool budget |

This repository contains **ready-to-use JSON configs** for major MCP clients.

---

## Quick pick — which URL?

| Your client | Recommended URL | Tools | Auth |
|-------------|-----------------|------:|------|
| **Claude Desktop** | `https://mcp.paperoffice.ai/claude` | 151 | OAuth 2.1 (no key in config) or Bearer |
| **Claude Code** | `https://mcp.paperoffice.ai/dms` | 151 | Bearer token |
| **Cursor IDE** | `https://mcp.paperoffice.ai/cursor` | 37 | Bearer token |
| **Windsurf** | `https://mcp.paperoffice.ai/cursor` | 37 | Bearer token |
| **ChatGPT / OpenAI MCP** | `https://mcp.paperoffice.ai/openai` | ~112 | Bearer or OAuth |
| **Read-only default** | `https://mcp.paperoffice.ai/mcp` | 37 | Bearer token |
| **Power / migration** | `https://mcp.paperoffice.ai/mcp-full` | 350+ | Bearer token |
| **Strict tool budget** | `https://mcp.paperoffice.ai/mcp-fast` | 25 | Bearer token |

**Module paths (explicit scopes):**

- `https://mcp.paperoffice.ai/mcp-document-ai` — lighter Document AI (~95 tools)
- `https://mcp.paperoffice.ai/mcp-workflow-ai` — Workflow AI (~56 tools)

---

## Setup

### 1. Get a Bearer token

1. Sign up at [app.paperoffice.ai](https://app.paperoffice.ai)
2. **Settings → API → Generate token** (`po_ut_*` or session token)

### 2. Claude Desktop (OAuth — recommended)

Copy [`configs/claude_desktop_config.json`](configs/claude_desktop_config.json) into Claude Desktop MCP settings:

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/claude"
    }
  }
}
```

Claude Desktop uses **automatic OAuth 2.1** — you authorize in the browser on first connect. No API key in the file.

For **Claude Code** with Bearer token, use [`configs/claude_code_bearer.json`](configs/claude_code_bearer.json) (`/dms`).

### 3. Cursor

Copy [`configs/cursor_mcp.json`](configs/cursor_mcp.json) to `.cursor/mcp.json` in your project (or global Cursor MCP settings):

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/cursor",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Replace `YOUR_API_KEY` with your token from [app.paperoffice.ai](https://app.paperoffice.ai).

### 4. Windsurf

Copy [`configs/windsurf_mcp_config.json`](configs/windsurf_mcp_config.json) to `~/.codeium/windsurf/mcp_config.json` — same format as Cursor (`/cursor`).

### 5. ChatGPT / OpenAI MCP

Use [`configs/openai_mcp.json`](configs/openai_mcp.json) — URL `https://mcp.paperoffice.ai/openai`.

### 6. Additional profiles

| File | Purpose |
|------|---------|
| [`dms_mcp.json`](configs/dms_mcp.json) | Canonical headless DMS (`/dms`, 151 tools) |
| [`mcp_readonly.json`](configs/mcp_readonly.json) | Read-only `/mcp` (37 tools, same scope as `/cursor`) |
| [`mcp_fast.json`](configs/mcp_fast.json) | Minimal `/mcp-fast` (25 tools) |
| [`mcp_full.json`](configs/mcp_full.json) | Full surface `/mcp-full` (350+ tools) |
| [`advanced_modules.json`](configs/advanced_modules.json) | Split Document AI + Workflow AI + full |
| [`toolsets_combined.json`](configs/toolsets_combined.json) | Custom toolsets via `X-MCP-Toolsets` header |

---

## Transport & protocol

- **Transport:** Streamable HTTP (remote MCP)
- **Base host:** `mcp.paperoffice.ai`
- **Auth:** Bearer `Authorization: Bearer <token>` or OAuth 2.1 (Claude Desktop)
- **EU hosting:** GDPR-aligned processing in own Tier III data centres (ES + DE)

---

## Alternative: REST without MCP

Paste this URL into any AI assistant for full REST API docs:

```
https://api.paperoffice.ai/latest/docs/postman
```

Or use the LLM corpora:

- Marketing: [paperoffice.ai/llms.txt](https://paperoffice.ai/llms.txt)
- API: [api.paperoffice.ai/latest/docs/llms.txt](https://api.paperoffice.ai/latest/docs/llms.txt)

---

## What can you ask?

Once connected, try:

- *"Extract all data from this invoice"*
- *"OCR this scanned document"*
- *"Classify these 50 documents"*
- *"List unpaid invoices across all workspaces"*
- *"Search my knowledge base for GDPR policies"*

---

## Migrating older setups

| Legacy | Use instead |
|--------|-------------|
| `https://mcp.paperoffice.ai/mcp` as only URL | `/claude` or `/dms` for full DMS; `/cursor` for IDE |
| `/mcp-headless` | `/mcp-document-ai` (lighter) or `/dms` (full) |
| `/sse` endpoints | `/claude`, `/cursor`, `/dms` — Streamable HTTP |
| Expecting 357 MCP tools | **357+ = REST API**; **350+ = MCP** at `/mcp-full` |

---

## MCP Registry (draft)

[`server.json`](server.json) is prepared for the [Official MCP Registry](https://registry.modelcontextprotocol.io/) — **publish at product launch**, not before public signup is ready.

---

## Resources

- [Full MCP documentation](https://paperoffice.ai/en/developer/mcp/)
- [Postman collection (live)](https://api.paperoffice.ai/latest/docs/postman)
- [AI Cookbook](https://paperoffice.ai/en/developer/cookbook/)
- [REST API](https://api.paperoffice.ai)

---

## License

Configuration files in this repository are [MIT](LICENSE). The PaperOffice AI platform and API are proprietary — see [paperoffice.ai](https://paperoffice.ai) for terms.
