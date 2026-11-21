# eksis plugin for Claude, Cursor, Grok Bot, and Hermes Agent

Schedule, approve, and publish posts, answer comments and direct messages, run
comment and DM automations, and read analytics on Instagram, TikTok, YouTube,
LinkedIn, X, and more from your [eksis](https://eksis.io) workspace, without
leaving Claude, Cursor, Grok Bot, or Hermes Agent.

The plugin bundles the eksis remote MCP connector with a skill that teaches
the assistant how each platform behaves, so it checks a channel's rules before
drafting rather than after a post fails.

## What it can do

- Read the workspace: channels, connection health, plan, and quota
- Read what each network allows, whether or not a channel is connected, and look
  up Pinterest boards and the TikTok creator options a post needs
- Find a song for a TikTok post, from the popular list or across all of TikTok
- Check a post against every channel's rules before saving it
- Draft, schedule, reschedule, replace, and delete posts, and read the calendar
- Label posts made with AI on the networks that ask for it, and invite
  collaborators to Instagram posts
- Read the team's saved snippets, and keep notes on the idea board
- Manage the time slots of the posting queue
- Approve posts that contributors wrote, or send them back with a note
- Publish immediately, or retry the channels that failed, on request
- Import media from a public URL, upload a file from your computer when the
  assistant can run commands, check a file's status, and delete files
- Read, answer, hide, like, and delete comments, and mark them done
- Read and answer direct messages (paid plans)
- Create, read, and change comment and DM automations, and switch them on or off
- Read analytics for any period, per channel and per post type, with Instagram
  audience insights (paid plans), and the recent posts on a channel
- List the workspace's webhook endpoints. Creating or changing them stays in the
  eksis app and the REST API, never in the assistant.

59 tools in total. 29 only read; 30 create, change, or send, and each of those
is marked as a write tool. Claude and Cursor ask before they run one, and so
does Hermes Agent, because the package marks the eksis server untrusted. In Grok
Bot, add an **Ask first** rule for them under **Settings**, **General**,
**Auto-review**.

## Install

### Claude Code

```
/plugin install eksis
```

### Cursor and Grok Bot

Both load this repository as a Cursor plugin: `.cursor-plugin/plugin.json`
declares it, `mcp.json` adds the eksis server, and `skills/` carries the same
skill. Grok Bot installs plugins from **Connect apps**, and an installed plugin
is available to every Bot on the account.

Without the plugin, Grok Bot can still add the server when you ask in chat:

```text
Add a custom MCP server called eksis at https://api.eksis.io/mcp
```

### Hermes Agent

eksis is listed in the Hermes Marketplace:
<https://hermes-agent.nousresearch.com/marketplace/eksis>.

The repository root is also a portable Agent Plugins package: `plugin.json`,
`mcp.json`, and the same `skills/` folder. Hermes installs it switched off, so
enable it after installing:

```bash
hermes plugins install eksis
hermes plugins enable eksis
```

`hermes plugins install eksis` takes the pinned release from the Hermes plugin
catalog; `hermes plugins install eksis-app/eksis-plugin` takes this repository
directly. The catalog entry ships with Hermes 0.23.3: an older Hermes answers
that eksis is not in the catalog, so run `hermes update` first or install from
this repository.

The package's `mcp.json` cannot run the sign-in on its own, so add the server to
`~/.hermes/config.yaml` with OAuth. Keep `trust: untrusted`: an entry in
`config.yaml` replaces the package's, including its trust setting, and an entry
without `trust` runs every tool without asking. If `hermes mcp add` already
wrote an `eksis` entry, run `hermes config set mcp_servers.eksis.trust untrusted`
instead of adding a second one.

```yaml
mcp_servers:
  eksis:
    url: https://api.eksis.io/mcp
    auth: oauth
    trust: untrusted
```

Then sign in and check the connection:

```bash
hermes mcp login eksis
hermes mcp test eksis
```

Start a new session, or run `/reload-mcp`, to load the tools. To use an API key
instead of OAuth, follow <https://docs.eksis.io/en/mcp/clients/hermes>.

What the package does once it is enabled:

- It has no local code. It adds a skill and one remote MCP server,
  `https://api.eksis.io/mcp`, and Hermes stores and refreshes the OAuth tokens.
- Every tool call goes to api.eksis.io with what the call carries, such as a
  caption or a reply. What the tools return (channels, posts, comments, direct
  messages, analytics) reaches your model provider through the session.
- Write tools publish to the social accounts connected in the workspace, send
  comment replies and direct messages, and change automations and AI agents.
  Hermes asks before each one; read-only tools run without asking.
- To upload a file from your computer, the skill has the assistant send it with
  the `curl` command that `create_media_upload` returns, through the terminal
  tool. That is the only shell command it asks for.
- The tool list comes from the eksis server at run time, so a pinned commit of
  this package does not fix it.
- No background process, no telemetry, no self-update.

Steps for every supported client are at <https://docs.eksis.io/en/mcp>.

### Signing in

Connecting opens the eksis consent screen in your browser. You sign in, pick
**one workspace**, and choose whether the assistant may write as well as read.
The connection then appears on the API page inside that workspace and can be
disconnected there at any time.

## What you need

An eksis account, on any plan. The connector works on the Free plan through this
sign-in flow; the plan decides how many requests a day the workspace gets and how
many posts it can schedule a month. See [eksis.io/pricing](https://eksis.io/pricing).

## Privacy Policy

The full policy is at **<https://eksis.io/privacy>**, and the section that covers
this plugin is **[AI assistants you connect](https://eksis.io/privacy#ai-assistants)**.

In short:

- **What is collected.** Your eksis account details, the social accounts you
  connect, the content you create in eksis, and operational records such as
  request counts. eksis receives only the tool requests the assistant makes, for example
  the caption it drafted for you, not the rest of your conversation.
- **How it is used.** To run the service you asked for: scheduling, publishing,
  reading comments and direct messages, and reporting analytics. The contents of your posts, comments, and messages are not
  used to train AI models.
- **Third-party sharing.** What the assistant reads travels to the company that
  runs it, such as Anthropic for Claude, and is covered by that company's privacy
  policy. eksis also passes content to the social platform
  you publish to, and uses named infrastructure providers listed in the policy.
  eksis does not sell personal data.
- **Retention.** Content lives as long as the workspace does. Closing the account
  deletes it. Per-record retention windows are listed in the policy, and
  <https://eksis.io/data-deletion> explains how to request deletion.
- **About this connection.** eksis stores which assistant is connected, the
  workspace and permissions granted, who granted them, when it was last used, and
  how many requests it has made.
- **Contact.** support@eksis.io

## Support

- Documentation: <https://docs.eksis.io/en/mcp>
- Support: <https://eksis.io/support>
- Email: support@eksis.io

## License

MIT. See [LICENSE](LICENSE).
