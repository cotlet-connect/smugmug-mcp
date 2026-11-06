# How to connect SmugMug to Claude Code, ChatGPT and any AI agent

**Yes, Claude, ChatGPT and other AI agents can work in your SmugMug account.** SmugMug's API v2 needs an API key, OAuth and a developer. Cotlet.dev connects your own signed-in SmugMug account to any AI agent with no code, so you manage galleries in plain words.

## What you can ask

> Create a gallery "Smith Wedding 2026", make it private and share the link with the client.

> Which galleries got no visits in the last 6 months?

> Rename the photos in my latest gallery by date and location.

> Set the price list for the new portrait galleries to my standard one.

> List every gallery that is still public but marked client-only in its title.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install smugmug-mcp        # or run it once: uvx smugmug-mcp connect
smugmug-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 smugmug_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 smugmug_agent.py status    # is SmugMug ready in your Cotlet.dev account
python3 smugmug_agent.py guide     # SmugMug screens and sign-in link
python3 smugmug_agent.py read      # open SmugMug, read the page, close the browser
python3 smugmug_agent.py tools     # list Cotlet.dev tools
```

## Questions from SmugMug users

**Does SmugMug have an API?**

Yes, SmugMug has API v2, but it needs an API key, OAuth and code. Cotlet.dev gives your AI agent the same work in your own SmugMug account with no API key and no developer.

**How do I connect SmugMug to ChatGPT?**

Add Cotlet.dev as an app in ChatGPT (Settings → Apps, connector URL `https://cotlet.dev/mcp/v1`), sign in to SmugMug once in your Cotlet.dev Cloud Browser, and ask ChatGPT in plain words. No code and no SmugMug API key.

**Is there a way to use Claude with SmugMug?**

Yes. In Claude Code run the one-line `claude mcp add` command above; in the Claude app add `https://cotlet.dev/mcp/v1` as a custom connector. Claude then works in your own SmugMug account.

**Is there a SmugMug MCP server?**

SmugMug has no official MCP server. Cotlet.dev is a hosted MCP server that works in SmugMug for you, 24/7, with Claude, ChatGPT, Cursor, Codex, n8n, Make and Zapier.

## Also works with

- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/smugmug-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=smugmug

Start free: https://cotlet.dev/signup?app=smugmug&utm_source=github&utm_medium=readme&utm_campaign=smugmug
