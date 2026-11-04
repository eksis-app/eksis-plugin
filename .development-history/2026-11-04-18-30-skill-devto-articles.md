# Skill: DEV Community articles and required settings

## Summary

The publishing skill now tells the assistant how to write a DEV Community
article through the eksis MCP server 1.7.0 (PRD D-353, eksis-app/eksis-backend#303):
the required title, the optional summary and series, `get_devto_options` for
tag and series names, and why front matter stays out of the body.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: `requiredSettings` from `get_platform_capabilities`; a DEV paragraph
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: 1.3.0 to 1.4.0

## Verification

- Read the skill text against the tool descriptions in `eksis-backend/packages/shared/src/mcp.ts` and the devto settings schema

## Limitations

- The tool exists only after the backend commit is deployed; this commit should ship after it

## Follow-up

- none
