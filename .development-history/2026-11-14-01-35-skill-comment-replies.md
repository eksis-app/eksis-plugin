# Skill: safe comment replies

## Summary

The eksis MCP server (1.29.0, eksis-app/eksis-backend#370) added `idempotencyKey` to `reply_to_comment`, `since` to `list_comments`, and made the `get_comment` thread the whole conversation. A customer replying to about 100 Threads comments saw 29 of 35 calls time out while the replies went out, and checked every thread by hand to avoid double replies. The skill now tells assistants to retry with the same key instead, and the plugin moves to 1.6.1.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: `status: open` for unanswered comments, `since`, whole-conversation thread, one `idempotencyKey` per reply
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: 1.6.1

## Verification

- Tool names and parameters match `apps/api/src/mcp/server.ts` in eksis-backend; tool count unchanged (README untouched)

## Limitations

- the skill text depends on the backend deploy of eksis-backend#370
