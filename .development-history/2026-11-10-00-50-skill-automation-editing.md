# Skill: create and change automations

## Summary

A user reported that MCP only listed automations and switched them on or off. The tools to create and change
them existed behind the flag `mcp_automation_edit`, which the owner released to everyone on 10 Nov 2026
(PRD D-365, eksis-app/eksis-backend#331). The skill still said automations are built only in the builder, so
an assistant reading it would have refused. It now teaches `get_automation`, `create_automation`, and
`update_automation`.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: description and the Automations section
- `README.md`: automations bullet; tool count 58 (28 read, 30 write), matching `x-mcp` of MCP server 1.10.0
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: 1.4.0 to 1.5.0

## Verification

- Read the skill text against the tool descriptions in `eksis-backend/packages/shared/src/mcp.ts`
- Tool count computed from `MCP_TOOLS` with `mcpToolDocumented`

## Limitations

- `generate_image` is open to everyone but not announced yet, so it is not in the count

## Follow-up

- none
