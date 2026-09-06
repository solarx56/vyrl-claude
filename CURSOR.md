# Connect Vyrl to Cursor

Use a scoped Vyrl MCP token from [Vyrl profile settings](https://vyrl.pro/profile). Set `VYRL_MCP_TOKEN` securely in the environment that launches Cursor, then restart Cursor if needed. Do not paste the token into chat or commit it to a repository.

[Add Vyrl to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=vyrl&config=eyJ1cmwiOiJodHRwczovL3Z5cmwucHJvL2FwaS9tY3AiLCJoZWFkZXJzIjp7IkF1dGhvcml6YXRpb24iOiJCZWFyZXIgJHtlbnY6VllSTF9NQ1BfVE9LRU59In19)

The install link contains configuration only, with an environment-variable placeholder. It contains no token. Review and approve the configuration in Cursor. Installation is not proof of a successful authenticated connection.

If your browser does not open the install link, merge this entry into your existing `~/.cursor/mcp.json` without replacing other servers:

```json
{
  "mcpServers": {
    "vyrl": {
      "url": "https://vyrl.pro/api/mcp",
      "headers": {
        "Authorization": "Bearer ${env:VYRL_MCP_TOKEN}"
      }
    }
  }
}
```

Open Cursor’s MCP settings and verify that Vyrl connects. Try inspecting the Canvas node catalog first. Reads, edits and runs depend on token permissions. Edits commit immediately; generation may consume credits and permanent deletion requires explicit confirmation.

This is a direct installation guide, not a Cursor Marketplace listing. See [Cursor configuration documentation](https://cursor.com/docs/mcp) and [installation links](https://prod.cursor.com/docs/mcp/install-links).
