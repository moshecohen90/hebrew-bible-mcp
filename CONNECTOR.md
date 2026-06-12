# Hebrew Bible (Tanakh) - Connector Documentation

Documentation for adding the **Hebrew Bible (Tanakh)** MCP server as a connector in
Claude, ChatGPT, and other MCP-compatible clients.

- **Server URL:** `https://hebrewbible.app/mcp`
- **Transport:** Streamable HTTP (JSON-RPC 2.0)
- **Authentication:** none (public, read-only)
- **Privacy policy:** [PRIVACY.md](./PRIVACY.md)
- **Source / metadata:** https://github.com/moshecohen90/hebrew-bible-mcp

## What it does

Reads and cites the Hebrew Bible (Tanakh) - Torah, Nevi'im, and Ketuvim - in Hebrew
(with vowel points and cantillation) and 10 languages, and lets you browse guided
study plans and articles. Every result links back to the canonical page on
hebrewbible.app so answers can be cited.

## Tools

| Tool | Arguments | Returns |
| --- | --- | --- |
| `list_books` | `language?` | Every book with its English + localized name and a link. |
| `get_chapter` | `book`, `chapter`, `language?` | The full text of a chapter (every verse). |
| `get_verse` | `book`, `chapter`, `verse`, `language?` | One specific verse. |
| `list_subjects` | `language?` | Browseable subjects (Parsha, Holidays, Tehillim, Stories, ...). |
| `browse_subject` | `subject`, `language?`, `cursor?` | Study plans + articles for a subject, paginated. |
| `get_plan` | `plan`, `language?` | A plan's title, description, and day-by-day schedule. |

Languages: English, Hebrew, French, Spanish, Portuguese, Russian, German, Italian,
Polish, Korean. Book names and languages are provided as enums in `tools/list`, so the
client always offers valid values.

## How to connect

**Claude (Desktop / claude.ai):** add a custom connector with the URL
`https://hebrewbible.app/mcp`.

**Cursor / VS Code / Cline / other MCP clients:**

```json
{
  "mcpServers": {
    "hebrew-bible": { "url": "https://hebrewbible.app/mcp" }
  }
}
```

## Example

> "What does Psalm 23 say, in Hebrew?"

The assistant calls `get_chapter(book="Psalms", chapter=23, language="he")` and cites
`https://hebrewbible.app/he/texts/Psalms.23`.

## Support

See <https://hebrewbible.app> or contact **[your support email]**.

## Sister servers

- Mishnah - `https://mishnah.app/mcp`
- Talmud Bavli - `https://talmudbavli.app/mcp`
- Talmud Yerushalmi (Jerusalem) - `https://talmudjerusalem.app/mcp`
