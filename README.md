# Just. MCP Server

**Domains and websites for businesses built with AI**

Just. The business side of building with AI. Ask for a domain name for your business and the assistant checks whether it is available, then opens checkout on justdomain.ai, where you confirm and pay. Ask it to put your website online and it publishes the files at a public address; ask again and it changes a page. When your site is ready for your own domain, it hands you a link to finish in your browser. You sign in once with your Just account.

- **Website:** https://just-done.ai
- **MCP endpoint:** `https://mcp.just-done.ai/`
- **Registry name:** `ai.just-done/just`
- **Transport:** Streamable HTTP (remote, nothing to install)
- **Authorization:** OAuth 2.1 with dynamic client registration. Every
  call is signed in; the client opens a sign-in window the first time.

## Connecting

Add the endpoint to your client's MCP servers and sign in when it asks:

```json
{
  "mcpServers": {
    "just": {
      "type": "streamable-http",
      "url": "https://mcp.just-done.ai/"
    }
  }
}
```

The client discovers the authorization server from the endpoint, so there is
no API key, client id or secret to paste.

| Client | Address |
| --- | --- |
| Any MCP client | `https://mcp.just-done.ai/` |
| Claude | `https://mcp.just-done.ai/claude` |
| ChatGPT | `https://mcp.just-done.ai/chatgpt` |

In Claude Code:

```bash
claude mcp add --transport http just https://mcp.just-done.ai/claude
```

## Tools

| Tool | What it does |
| --- | --- |
| `search_domains` | Search domain availability |
| `check_domain_transfer` | Check whether a domain can transfer to Just Domain |
| `check_trademark` | Check a name against trademark registers |
| `deploy` | Publish a website |
| `list_sites` | List your published websites |
| `get_site_files` | Read a published site's files |
| `update_site_file` | Edit specific files of a published site |
| `get_site_domain_status` | Check your site's domain |

## Good to know

- **Every call is signed in, and publishing needs the user's permission on justpublish.ai.**
- **Payment.** The assistant opens checkout on justdomain.ai; you confirm and
  pay there, in your browser.
- **Static sites only.** A site is plain files with `index.html` at the
  root; there is no build step and no server code.

## Support

Write to support@just-done.ai.

## About this repository

This repository holds the public metadata and the registry listing of the
server: `server.json`, `.mcp.json`, `llms-install.md` and this README. The
server runs at the endpoint above and is operated by Just Done LLC; its source
is not part of this repository.

## License

Released under the MIT License, see [LICENSE](./LICENSE).
