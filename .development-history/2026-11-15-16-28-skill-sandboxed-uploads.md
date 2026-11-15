# Skill: uploads from sandboxed assistants

## Summary

The publishing skill now tells an assistant what to do when its sandbox refuses the PUT to `uploadUrl` after `create_media_upload` (Claude on claude.ai answered 403 from its egress proxy): follow the `next` field of the result instead of retrying, and do not try `upload_media_from_chat` outside ChatGPT.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: one paragraph under Media.
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.6.2.

## Decisions

- The skill does not name `uploadPageUrl`: it is behind flag `media_upload_page` (D-433) and is described by the `next` field only to accounts that have it.

## Verification

- Diff read; no build step for the skill.

## Follow-up

- Mention `uploadPageUrl` here once the flag reaches `everyone` (eksis-app/eksis-backend#392).
