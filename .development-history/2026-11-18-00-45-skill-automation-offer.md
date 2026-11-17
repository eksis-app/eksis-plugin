# Skill: offer a comment automation after create_post

## Summary

`create_post` over MCP can now return `next` with an offer of a comment automation for the new post (eksis-app/eksis-backend#407, PRD D-449). The publishing skill tells an assistant how to handle it.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: one paragraph in the Automations section: offer once in the user's language, suggest the keyword from the caption, pass the post id as `scheduledPostIds`, create nothing without a yes.
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.7.1.

## Verification

- Diff read; no build step for the skill.

## Follow-up

- none
