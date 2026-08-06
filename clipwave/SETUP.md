---
name: setup
description: Connect the Clipwave MCP server after installing the plugin. Use when Clipwave tools return 401, when the user says Clipwave is not connected, or right after a fresh install.
---

# Connecting Clipwave

The plugin ships a remote MCP server at `https://clipwave.io/api/mcp`. It needs
authentication before any tool works. There are two paths — pick by client.

## Path A — OAuth (Claude Code, Claude Desktop, claude.ai)

The server advertises OAuth 2.0 with dynamic client registration and PKCE, so the
client handles everything itself:

1. Run `/mcp` in Claude Code (or open Settings → Connectors elsewhere).
2. Select **clipwave** and choose **Authenticate**.
3. A browser opens on the Clipwave consent screen. Sign in and approve.
4. Return to the client. Tools are live.

Nothing to paste, no key to store. Tokens refresh automatically.

## Path B — API key (headless agents, CI, servers)

For non-interactive environments where no browser is available:

1. Send the user to <https://clipwave.io/dashboard/api-keys> to create a key.
2. Keys look like `cw_live_…`.
3. Configure the server with an `Authorization: Bearer cw_live_…` header.

Never print a key back into the transcript, and never commit one.

## Verifying

Call `list_models` — it is read-only, costs nothing, and needs no arguments. A
model catalogue means you are connected. A 401 means authentication did not
complete; retry Path A.

## An account is required

Generation spends credits from the signed-in Clipwave account. A user with no
account or no remaining credits will get an explicit error from the tool rather
than a silent failure. Point them at <https://clipwave.io> to sign up or top up.
Read-only tools (`list_models`, `job_status`, the `video_editor_get_*` and
`video_editor_list_*` family) never spend credits.
