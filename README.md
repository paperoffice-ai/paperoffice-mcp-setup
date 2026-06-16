<div align="center">

<img src="assets/logo.png" alt="PaperOffice AI" width="300" />

# PaperOffice MCP Server

**Give your AI assistant access to your documents — in plain language, in under 60 seconds.**

Search, read, OCR, classify, extract, sign and analyse documents straight from
Claude, Claude Cowork, Cursor, ChatGPT or Windsurf. No SDK, no boilerplate, no local install.

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

**Full DMS power** (recommended for Claude, Claude Cowork, Claude Code) — [`configs/dms_mcp.json`](configs/dms_mcp.json)

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/dms",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude Desktop with OAuth** (no key in file) — [`configs/claude_desktop_config.json`](configs/claude_desktop_config.json) uses `/claude`, an alias of `/dms`.

**Everything** (all 350+ tools across every module) — [`configs/mcp_full.json`](configs/mcp_full.json) → `/mcp-full`.

### 3 · Ask away

That's it — your AI now works with your documents.

---

## Choose your scope — you decide, not your client

**Any client can use any URL.** The paths below are convenience profiles, not limits:
go full from day one, or narrow the surface for tool-limited clients or read-safety.

| I want… | URL | Tools | Good for |
|---------|-----|------:|----------|
| **Everything** | `https://mcp.paperoffice.ai/mcp-full` | 350+ | Power users, agents, migration |
| **Full headless DMS** | `https://mcp.paperoffice.ai/dms` | 151 | Claude, Claude Cowork, Claude Code |
| **Document AI + Workflow** | `https://mcp.paperoffice.ai/openai` | ~112 | ChatGPT / OpenAI MCP |
| **Read-safe (no deletes)** | `https://mcp.paperoffice.ai/cursor` | 37 | Cursor / Windsurf while coding |
| **Minimal budget** | `https://mcp.paperoffice.ai/mcp-fast` | 25 | Clients with a hard tool cap |

**Aliases & modules:**
`https://mcp.paperoffice.ai/claude` = alias of `/dms` (OAuth-friendly for Claude Desktop) ·
`https://mcp.paperoffice.ai/mcp` = same read-safe scope as `/cursor` ·
`https://mcp.paperoffice.ai/mcp-document-ai` (~95) ·
`https://mcp.paperoffice.ai/mcp-workflow-ai` (~56) for explicit single-module scopes.

> **Why scopes at all?** Fewer tools = faster, more accurate tool-selection by the model,
> and some clients enforce a tool-count cap. A read-safe profile (`/cursor`) prevents
> accidental deletes while coding. None of this limits what PaperOffice can do — switch
> to `/dms` or `/mcp-full` anytime for the full surface.

Ready-made config files for every profile are in [`configs/`](configs/).

---

## Per-client quick reference

| Client | Suggested start | Want more? |
|--------|-----------------|-----------|
| **Claude Desktop** | `/claude` (OAuth, 151) | `/mcp-full` for all 350+ |
| **Claude Cowork / Claude Code** | `/dms` (151, full DMS) | `/mcp-full` for all modules |
| **Cursor / Windsurf** | `/cursor` (37, read-safe) | `/dms` or `/mcp-full` for write + everything |
| **ChatGPT / OpenAI MCP** | `/openai` (~112) | `/mcp-full` for all 350+ |

These are starting points — change the URL whenever your task needs a different scope.

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
