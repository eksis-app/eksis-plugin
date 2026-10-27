# Skill and README for MCP server 1.3.0

## Summary

The eksis MCP server gains automations, saved snippets, and fuller analytics (eksis-app/eksis-backend#241,
PRD D-320). The plugin is updated to match before it is submitted to the Claude directory.

## Changes

- `skills/publishing-with-eksis/SKILL.md`: AI-content labels per platform, Instagram collaborators, snippets,
  the idea board (missing since the ideas tools shipped), automations, and the new analytics inputs
- `README.md`: capability list, 48 tools (24 read-only), contact `support@eksis.io`
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.2.0, description, author email

## Decisions

- The skill asks for confirmation before switching an automation on; pausing needs none

## Verification

- `claude plugin validate --strict .`: passed

## Limitations

- Pushed only after the backend change is deployed, so the README never lists tools the server lacks

## Follow-up

- Submit the plugin bundle through claude.ai/directory/manage after the MCP connector submission
