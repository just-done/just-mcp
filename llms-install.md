# Installing Just. (for AI agents)

Just. is a remote MCP server with OAuth sign-in. There is nothing to download,
build or run locally, and no API key to paste.

1. Add this entry to the user's MCP settings file (for Cline:
   `cline_mcp_settings.json`):

   {
     "mcpServers": {
       "just": {
         "type": "streamableHttp",
         "url": "https://mcp.just-done.ai/"
       }
     }
   }

2. Connect. The server answers with an OAuth challenge and the client opens a
   sign-in window, where the user signs in with their Just account. The client
   registers itself, so leave any client id and secret fields empty.

3. Verify by listing tools. You should see these eight:
   - `search_domains`
   - `check_domain_transfer`
   - `check_trademark`
   - `deploy`
   - `list_sites`
   - `get_site_files`
   - `update_site_file`
   - `get_site_domain_status`

4. To find a domain, call `search_domains` with one or more names. It returns
   availability for each name, with a `checkout_url` for each name the user can
   register. The user opens that link and confirms and pays on justdomain.ai in
   a browser.

5. To publish, call `deploy` with the site files (`index.html` at the root is
   required). It returns the live address and a `site_id`. The site belongs to
   the signed-in account, so do not ask the user for an email address.

6. The website tools need the user's permission on justpublish.ai. If one
   answers `grant_required`, give the user its message and the link in it, and
   call again once they have allowed it in the browser.

7. To change a site later, find it with `list_sites` and read it with
   `get_site_files`. Then send the changed files with `update_site_file`.
