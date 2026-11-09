# Skill: songs on TikTok posts

## Summary

The eksis MCP server gained `search_tiktok_music` (server 1.11.0, eksis-app/eksis-backend#334). The skill now tells assistants how to find a song and attach it as `settings.music`, and the plugin moves to 1.6.0.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: popular list or search, pass the track unchanged, video with a song is always public, TikTok for Business must be connected from the composer
- `README.md`: song finding in the capability list; 59 tools, 29 read-only
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: 1.6.0

## Verification

- Tool counts computed from `MCP_TOOLS` with `mcpToolDocumented` in eksis-backend: 59 documented, 29 read-only, 30 write
- docs.eksis.io/en/mcp/tools lists `search_tiktok_music`
