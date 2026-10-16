# Package the plugin for Cursor and Grok Bot

## Summary

Grok Bot (xAI's cloud agent) installs connectors as plugins from the Cursor plugin library, and the same repository now loads as a Cursor plugin next to the Claude one. Issue eksis-app/eksis-plugin#1.

## Changes

- `.cursor-plugin/plugin.json`: Cursor manifest, same name, version, and metadata as the Claude manifest, logo at `assets/logo.png`.
- `mcp.json`: Cursor-format server entry (`url` only, OAuth), auto-discovered by Cursor. `.mcp.json` stays for Claude Code.
- `assets/logo.png`: copy of `eksis-docs/eksis_logo_bg_white.png` (1024x1024), the logo meant for third-party listings.
- `README.md`: covers Claude Code, Cursor, and Grok Bot install, the chat fallback (`Add a custom MCP server called eksis at ...`), Auto-review advice for Grok Bot, and assistant-neutral privacy wording.

## Decisions

- No backend change: discovery, DCR, PKCE, and `validateRedirectUri` already accept Grok Bot's `https://cursor.com/{agents,bot}/mcp/oauth/callback` registrations.
- Not submitted to the Cursor Marketplace; that is the owner's call (PRD §15 no. 77).

## Verification

- Manifest checked against the cursor.com/docs/reference/plugins checklist (kebab-case name, relative logo path that exists, no `${VAR}` to declare).
- `claude plugin validate --strict .`: passed; its README marketplace-line warning is identical on HEAD.
- Production read-only probe: protected-resource and authorization-server metadata, 401 `WWW-Authenticate` challenge, `tools/list` = 38 tools (19 `readOnlyHint: true`).

## Limitations

- Not loaded in Cursor or Grok Bot, and the Grok Bot OAuth flow was not run end to end.

## Follow-up

- With the owner's approval: one Grok Bot connection against a test workspace, then a Marketplace submission.
