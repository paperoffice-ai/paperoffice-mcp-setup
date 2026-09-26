<div align="center">

<img src="assets/logo.png" alt="PaperOffice AI" width="300" />

# PaperOffice MCP Server

**Give your AI assistant access to your documents — in plain language, in under 60 seconds.**

Search, read, OCR, classify, extract, sign and analyse documents straight from
Claude, Claude Cowork, Cursor, ChatGPT, Grok or Windsurf. No SDK, no boilerplate, no local install.

[![Model Context Protocol](https://img.shields.io/badge/Model_Context_Protocol-ready-2563eb)](https://paperoffice.ai/en/developer/mcp/)
[![MCP tools](https://img.shields.io/badge/MCP_tools-300%2B-7c3aed)](https://paperoffice.ai/en/developer/mcp/)
[![Hosting](https://img.shields.io/badge/Hosting-EU_Tier_III-009e60)](https://paperoffice.ai/en/company/security/)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.1_+_po_ut_-ea580c)](https://paperoffice.ai/en/developer/mcp/)

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

## See it in action

<div align="center">

<a href="https://paperoffice.ai/en/ai-blog-insights-document-automation/claude-fable-5-paperoffice-mcp-dms-agentic/">
  <img src="https://paperoffice.ai/images/blog/mcp-fable5-hero.gif" alt="Claude Fable 5 + PaperOffice MCP DMS — agentic document work" width="720" />
</a>

*Claude Fable 5 + PaperOffice MCP DMS — agentic document work. [Watch the full guide →](https://paperoffice.ai/en/ai-blog-insights-document-automation/claude-fable-5-paperoffice-mcp-dms-agentic/)*

</div>

Four real workflows with Claude — under 30 seconds each. Click a card for the deep-dive with prompts and tool lists:

| | Use case | Watch & read |
|---|----------|--------------|
| 📊 | **Month-end invoices** — open items across every workspace, with totals and overdue flags | [![Month-end invoices](https://paperoffice.ai/images/blog/mcp-invoice-month-end.webp)](https://paperoffice.ai/en/ai-blog-insights-document-automation/mcp-month-end-invoices-claude-paperoffice/) |
| 📥 | **Overnight inbox** — capture, classify, flag duplicates and expiring contracts before you wake up | [![Overnight inbox](https://paperoffice.ai/images/blog/mcp-inbox-automation.webp)](https://paperoffice.ai/en/ai-blog-insights-document-automation/mcp-inbox-automation-overnight-claude/) |
| 📱 | **Mobile contract lookup** — signed date, terms, page reference from your phone in seconds | [![Mobile contract lookup](https://paperoffice.ai/images/blog/mcp-mobile-contract-search.webp)](https://paperoffice.ai/en/ai-blog-insights-document-automation/mcp-mobile-contract-search-claude-dms/) |
| 📈 | **Spend dashboard** — from 300 invoices to a board-ready dashboard in one prompt | [![Spend dashboard](https://paperoffice.ai/images/blog/mcp-spending-dashboard.webp)](https://paperoffice.ai/en/ai-blog-insights-document-automation/mcp-spending-dashboard-invoices-claude/) |

---

## 60-second setup

### 1 · Auth

You need a PaperOffice account — the free plan is enough to try everything here. No account yet? Create one at **[app.paperoffice.ai/en/register/](https://app.paperoffice.ai/en/register/)** (no credit card).

Claude, ChatGPT and Grok start with **OAuth 2.1**: the client opens the PaperOffice sign-in, you approve, no token in any file. For Cursor, DMS, or as an alternative: sign in at [app.paperoffice.ai](https://app.paperoffice.ai), open **Account → API** and create a **User token** (`po_ut_`) or a **Group token** (`po_gt_`, limited to the workspaces of one group). `po_sk_` and `po_pk_` are blocked for MCP.

Questions or something not working: [Help & FAQ](https://help.paperoffice.ai/) · [Support](https://paperoffice.ai/en/support/) · [Issues](https://github.com/paperoffice-ai/paperoffice-mcp-setup/issues).

### 2 · Paste one URL into your client

**Claude Desktop / Anthropic Directory** (OAuth 2.1, no key in file) — [`configs/claude_desktop_config.json`](configs/claude_desktop_config.json)

```json
{
  "mcpServers": {
    "paperoffice": {
      "url": "https://mcp.paperoffice.ai/claude"
    }
  }
}
```

`/dms`, `/cursor` and `/grok` share the **Documents Operations** catalog (including TTS). `/claude` is Directory without TTS. `/chatgpt` (alias `/openai`) is the ChatGPT connector (Directory without TTS, OTP/unlock).

**Full headless DMS** (`po_ut_` / `po_gt_`) — [`configs/dms_mcp.json`](configs/dms_mcp.json) → `/dms`. Same catalog as `/cursor` and `/grok`.

**ChatGPT / Grok** (OAuth 2.1, no key in file) — `/chatgpt` (alias `/openai`) or `/grok` ([`configs/openai_mcp.json`](configs/openai_mcp.json), [`configs/grok_mcp.json`](configs/grok_mcp.json)). `po_ut_` / `po_gt_` remains an alternative for `/chatgpt`.

**Everything** (300+ MCP tools across every module) — [`configs/mcp_full.json`](configs/mcp_full.json) → `/mcp-full`.

### 3 · Ask away

That's it — your AI now works with your documents.

---

## Choose your scope — you decide, not your client

**Any client can use any URL.** The paths below are convenience profiles, not limits:
go full from day one, or pick Directory / ChatGPT policy surfaces when a catalog requires it.

| I want… | URL | Surface | Good for |
|---------|-----|---------|----------|
| **Everything** | `https://mcp.paperoffice.ai/mcp-full` | **300+** | Power users, agents, migration |
| **Documents Operations** | `https://mcp.paperoffice.ai/dms` | **300+** | Canonical DMS URL |
| **Cursor / Windsurf** | `https://mcp.paperoffice.ai/cursor` | same as `/dms` | IDE — full Documents Operations including TTS |
| **Grok** | `https://mcp.paperoffice.ai/grok` | same as `/dms` | Grok custom connector |
| **Claude Directory URL** | `https://mcp.paperoffice.ai/claude` | Directory without TTS | Claude Desktop / Anthropic Directory |
| **ChatGPT** | `https://mcp.paperoffice.ai/chatgpt` | Directory without TTS, OTP/unlock | ChatGPT Apps SDK |
| **ChatGPT alias** | `https://mcp.paperoffice.ai/openai` | same as `/chatgpt` | Legacy ChatGPT URL |
| **Slim IDE subset** | `https://mcp.paperoffice.ai/mcp` | subset of 300+ | Read-safe default for tool-limited IDEs |

**Client shortcuts:**
`https://mcp.paperoffice.ai/cursor` = same Documents Operations catalog as `/dms` ·
`https://mcp.paperoffice.ai/grok` = same Documents Operations catalog as `/dms` ·
`https://mcp.paperoffice.ai/claude` = Directory without TTS ·
`https://mcp.paperoffice.ai/chatgpt` = ChatGPT connector (alias `https://mcp.paperoffice.ai/openai`) ·
`https://mcp.paperoffice.ai/mcp` = slim IDE subset.

> **Why scopes at all?** Fewer tools = faster, more accurate tool-selection by the model,
> and some clients enforce a tool-count cap. `/mcp` is the slim IDE subset.
> None of this limits what PaperOffice can do — switch to `/mcp-full` anytime for media, CRM and telephony.

Ready-made config files for every profile are in [`configs/`](configs/).

---

## Per-client quick reference

| Client | Suggested start | Want more? |
|--------|-----------------|-----------|
| **Claude Desktop** | `/claude` (OAuth, Directory without TTS) | `/mcp-full` for media/CRM |
| **Claude Cowork / Claude Code** | `/dms` (Documents Operations, `po_ut_` / `po_gt_`) | `/mcp-full` for all modules |
| **Cursor / Windsurf** | `/cursor` (same catalog as `/dms`) | `/mcp-full` for media/CRM |
| **ChatGPT** | `/chatgpt` (OAuth, alias `/openai`) | `/mcp-full` for all 300+ |
| **Grok** | `/grok` (OAuth, same catalog as `/dms`) | `/mcp-full` for all 300+ |

These are starting points — change the URL whenever your task needs a different scope.

### Marketplace plugins

Prefer a one-click install? The same server is packaged as a plugin for two marketplaces:

| Marketplace | Repository | Endpoint |
|-------------|------------|----------|
| **Cursor Marketplace** | [paperoffice-ai/paperoffice-cursor-plugin](https://github.com/paperoffice-ai/paperoffice-cursor-plugin) | `/cursor` — token set as a plugin variable, never in the repo |
| **xAI Plugin Marketplace (Grok Build)** | [paperoffice-ai/paperoffice-grok-plugin](https://github.com/paperoffice-ai/paperoffice-grok-plugin) | `/grok` — OAuth 2.1 on first connection |

ChatGPT and Claude do not need a repository: connect the `/chatgpt` or `/claude` URL directly, or install PaperOffice from their app directories once listed.

### Official MCP Registry

PaperOffice is published in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=paperoffice) as **`io.github.paperoffice-ai/paperoffice-mcp`** — the manifest is [`server.json`](server.json) in this repository. Clients and directories that read the registry (VS Code, Glama, PulseMCP and others) find the six lanes there without any manual entry.

```bash
# Claude Code
claude mcp add --transport http paperoffice https://mcp.paperoffice.ai/dms
```

### Agent Skills

The MCP server supplies the tools; [paperoffice-ai/paperoffice-skills](https://github.com/paperoffice-ai/paperoffice-skills) supplies the procedures — five `SKILL.md` files (API integration, invoice extraction, OCR, documents, tool discovery) that load as a Claude Code plugin, a claude.ai skill upload, or inside the Cursor plugin.

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
- **API-first** — 300+ API/MCP-Tools via REST or MCP. MCP uses OAuth 2.1 or a User token (po_ut_ / po_gt_) — see [Postman](https://api.paperoffice.ai/latest/docs/postman).
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
- **Auth:** OAuth 2.1 first for Claude / ChatGPT / Grok (no token in the file). Bearer (`po_ut_` / `po_gt_`) for Cursor, DMS, and as an alternative. `po_sk_` and `po_pk_` are blocked for MCP.
- **Public claim:** **300+ API/MCP-Tools** (unified REST + MCP). Do not cite 250/260/350/357/500 or drifting profile integers.
- **Claude.ai network allowlist:** `mcp.paperoffice.ai` and `api.paperoffice.ai` (two **f**s — never `paperofice`)

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
