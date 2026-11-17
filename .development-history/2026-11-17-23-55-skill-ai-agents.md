# Skill: AI agents

## Summary

The publishing skill now explains the AI Agent tools, which became part of the documented MCP catalog once the `ai_agent` flag reached everyone (eksis-app/eksis-backend#341).

## Changes

- `skills/publishing-with-eksis/SKILL.md`: an "AI agents" section (create from a template, attach knowledge and a personality, test before switching on, Needs attention), plus a trigger phrase in the description.
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.7.0 and a description that mentions AI agents.

## Decisions

- The skill tells an assistant to run `test_ai_agent` and show the reply before `set_ai_agent_status`, because an active agent writes to customers in the workspace's name.

## Verification

- Diff read; no build step for the skill.

## Follow-up

- none
