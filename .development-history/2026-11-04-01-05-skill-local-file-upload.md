# Skill for MCP server 1.5.0: local file upload and one target per channel

## Summary

An MCP user in Claude Code could not attach a file from their laptop: the server only imported from a public URL
or from ChatGPT attachments. The server gains `create_media_upload` and `complete_media_upload`
(eksis-app/eksis-backend#296), and refuses a channel listed twice in `targets` (eksis-app/eksis-backend#295).

## Changes

- `skills/publishing-with-eksis/SKILL.md`: the presigned upload flow for local files, and one entry per channel
  in `targets` (feed and story on one account are two posts)
- `README.md`: local file upload in the capability list, 51 tools (24 read-only)
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.3.0

## Decisions

- The skill names the upload tools only for assistants that can run commands; others keep the URL import

## Verification

- `claude plugin validate --strict .`: passed (one existing README warning about the marketplace install line)

## Limitations

- Push only after the backend change (#296) is deployed, so the skill never describes tools the server lacks

## Follow-up

- After the backend deploy: push, then resubmit the plugin bundle where it is listed
