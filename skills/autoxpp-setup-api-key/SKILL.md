---
name: autoxpp-setup-api-key
description: Configure your AutoXPP API key and MCP connection for premium skill access in Codex.
---

# AutoXPP API Key Setup (Codex)

## Step 1: Check if MCP is already connected

First, try to call the `autoxpp` MCP tool `validate_license`.

- **If the call succeeds**: Display the following banner, then report the user's tier and available skills. Done — no further setup needed.

```
  >_  AutoXPP™  · D365 F&O AI Dev Engine · by xplusplus.ai
```
- **If the MCP tool is not available**: Continue to Step 2.

## Step 2: Get the API key

If the user provided a key as an argument (e.g. `$autoxpp-setup-api-key ak_xxxxxxxx`), use that.

Otherwise, ask the user for their key. It should start with `ak_` (e.g. `ak_ZVrTR-3R_fu8vLUjlgjHTjxiLRP9gTiaK`). If they don't have one, direct them to https://xplusplus.ai/autoxpp.html to subscribe and get a key.

## Step 3: Configure the MCP server in Codex

Codex stores MCP configuration in a single global file — `config.toml` in the Codex home directory (`~/.codex/config.toml`, or `$CODEX_HOME/config.toml` if set). The same config is shared by the Codex CLI, the ChatGPT desktop app (Codex/Work), and the IDE extension, so this is a one-time setup that works everywhere.

Add (or merge) the following block into `~/.codex/config.toml`, replacing `<API_KEY>` with the actual key:

```toml
[mcp_servers.autoxpp]
url = "https://autoxpp.xplusplus.ai/mcp"
http_headers = { Authorization = "Bearer <API_KEY>" }
```

**If an `[mcp_servers.autoxpp]` block already exists**, update its `http_headers` in place. Do NOT remove or overwrite other `[mcp_servers.*]` entries.

Alternatively, keep the key out of the config file by storing it in an environment variable and referencing it:

```toml
[mcp_servers.autoxpp]
url = "https://autoxpp.xplusplus.ai/mcp"
bearer_token_env_var = "AUTOXPP_API_KEY"
```

Then set `AUTOXPP_API_KEY=<API_KEY>` in the environment before launching Codex.

## Step 4: Reconnect and validate

After saving `config.toml`, tell the user:
1. Restart Codex (or start a new session) for the MCP server to connect.
2. Run `$autoxpp-setup-api-key` again to validate the connection.

## Notes

- Free skills (browser-v2, azure-devops, sql-jit, ude-switch) work without an API key or MCP connection.
- The plugin handles skill distribution. This skill handles MCP server configuration only.
- `config.toml` is global (per Codex home), not per-project. There is no per-workspace `.mcp.json` in Codex — one entry serves every repo.
- `config.toml` contains your API key if you use the inline `http_headers` form — keep the file readable only by your user account, or use the `bearer_token_env_var` form instead.
