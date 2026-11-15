# Skill: Threads threads and resuming a stopped thread

## Summary

The publishing skill now tells an assistant how to post text longer than 500 characters to Threads with `settings.thread`, and that `retry_post` continues a thread that stopped partway (eksis-app/eksis-backend#399, MCP server 1.43.0).

## Changes

- `skills/publishing-with-eksis/SKILL.md`: one paragraph on `settings.thread`, two sentences on `thread.stopped` and `retry_post`.
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.6.3.

## Decisions

- The skill warns against sending the same words as both `firstComment` and a follow-up post, since a Threads first comment goes out as the first follow-up post.

## Verification

- Diff read; no build step for the skill.

## Follow-up

- none
