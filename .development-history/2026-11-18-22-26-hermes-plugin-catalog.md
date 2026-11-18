# Package eksis for the Hermes Agent plugin catalog

## Summary

The repository root is now a portable Agent Plugins v1 package as well, so Hermes Agent (Nous Research) can install it and the Hermes plugin catalog can list it. Issue eksis-app/eksis-plugin#3.

## Changes

- `plugin.json` (new): Agent Plugins v1 manifest, version 1.8.0, with the Hermes extension `servers.eksis.trust: untrusted` so Hermes asks before every tool without `readOnlyHint`.
- `mcp.json`: Agent Plugins v1 shape (`$schema`, `type: streamable-http`). Cursor documents support for this shape in a root `mcp.json`.
- `README.md`: Hermes install, OAuth sign-in through `config.yaml`, and the disclosure list the catalog asks for (rule 13).
- `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`: version 1.8.0.

## Decisions

- Plugin catalog, not `optional-mcps/`: maintainers stopped taking new `optional-mcps` entries (PR #113889 closed with a pointer to the catalog). Comparable listings: postroom, slaide, remoet.
- One package at the repository root instead of a `hermes/` subfolder, so the skill is not copied and cannot drift.
- Agent Plugins v1 defines no OAuth field, so sign-in goes through a `config.yaml` entry with `auth: oauth` and `trust: untrusted`, the same known issue slaide and remoet list.

## Verification

- `hermes plugins validate .` (Hermes 0.22.2): passed; trust untrusted, security scan safe, portable.
- Skill frontmatter checked against the upstream adapter rules (name matches folder, description 533 of 1024 characters).

## Limitations

- Not run end to end in Hermes (install, OAuth, a tool call).
- Grok Bot reading the new `mcp.json` shape was not checked.

## Follow-up

- Catalog PR to NousResearch/hermes-agent pinning this commit; merge is the maintainers' call.
