# Skill scheduling guidance and `.mcp.json` type

## Summary

Part of the public API and MCP audit (eksis-app/eksis-backend#62). The skill told the model that `create_post` with a scheduled time queues the post, but `mode` defaults to `draft`, so a model following it saved drafts. `.mcp.json` also lacked the `type` that Claude Code needs for a remote server.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: scheduling needs `mode: "schedule"` plus `scheduledAt`; `queue` takes the next free slot; after `mode: "now"` or `publish_post`, read `get_post`; unknown media ids are refused.
- `.mcp.json`: `"type": "http"` added, the form the Claude Code MCP docs give for remote servers.
- `.claude-plugin/plugin.json`: version 1.0.1.

## Decisions

- The MCP tool catalogue itself was not touched (frozen by the OpenAI directory review, D-62); the fix lives in the skill text.

## Verification

- `claude plugin validate --strict .`: passed.

## Limitations

- No real `/plugin install` plus OAuth run was done in this change.

## Follow-up

- Resubmit or refresh the Claude directory listing if the reviewed version must match 1.0.1.
