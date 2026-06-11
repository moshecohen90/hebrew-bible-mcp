# Hebrew Bible (Tanakh) MCP Server

A public, no-auth **Model Context Protocol (MCP)** server for reading and citing the
**Hebrew Bible (Tanakh)** - Torah, Nevi'im, and Ketuvim - in Hebrew and 10 languages,
and for browsing guided study plans. Served by [hebrewbible.app](https://hebrewbible.app).

- **Endpoint:** `https://hebrewbible.app/mcp` (Streamable HTTP, JSON-RPC, no authentication)
- **Server card:** https://hebrewbible.app/.well-known/mcp/server-card.json
- **Agent skill:** https://hebrewbible.app/.well-known/agent-skills/index.json
- **Languages:** English, Hebrew (with nikud + cantillation), French, Spanish, Portuguese, Russian, German, Italian, Polish, Korean

## Tools

| Tool | Description |
| --- | --- |
| `list_books` | List every book of the Tanakh with its English and localized name. |
| `get_chapter` | Return the full text of a chapter (every verse) in any supported language. |
| `get_verse` | Return one specific verse (e.g. Genesis 1:1) in any supported language. |
| `list_subjects` | List browseable subjects (Weekly Torah Portion, Holidays, Tehillim, Bible Stories, ...). |
| `browse_subject` | List study plans and articles for a subject or topic, paginated. |
| `get_plan` | Get a study plan's title, description, and day-by-day schedule. |

Every result links back to the canonical page on hebrewbible.app so answers can be cited.

## Connect

**Claude Desktop / Claude.ai** - add a custom connector with the URL `https://hebrewbible.app/mcp`.

**Cursor / VS Code / Cline** - add to your MCP config:

```json
{
  "mcpServers": {
    "hebrew-bible": {
      "url": "https://hebrewbible.app/mcp"
    }
  }
}
```

**Any MCP client** - point it at `https://hebrewbible.app/mcp` (Streamable HTTP transport).

## Example

> "What does Psalm 23 say, in Hebrew?"

The assistant calls `get_chapter(book="Psalms", chapter=23, language="he")` and cites
`https://hebrewbible.app/he/texts/Psalms.23`.

## Sister servers

The same MCP serves the other corpora on their own domains:

- Mishnah - `https://mishnah.app/mcp`
- Talmud Bavli - `https://talmudbavli.app/mcp`
- Talmud Yerushalmi (Jerusalem) - `https://talmudjerusalem.app/mcp`

## About

Free to read; the biblical text and classical commentaries are in the public domain.
This repository contains only public metadata and documentation for the hosted MCP
server - there is no proprietary code here.

Keywords: Hebrew Bible, Tanakh, Tanach, Torah, Nevi'im, Ketuvim, Bible, scripture,
verses, chapters, Psalms, Tehillim, parsha, study plans, Jewish, MCP server,
Model Context Protocol, AI agent, Claude, ChatGPT.
