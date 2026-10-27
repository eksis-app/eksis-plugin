# eksis plugin for Claude, Cursor, and Grok Bot

Schedule, approve, and publish posts, answer comments and direct messages, run
comment and DM automations, and read analytics on Instagram, TikTok, YouTube,
LinkedIn, X, and more from your [eksis](https://eksis.io) workspace, without
leaving Claude, Cursor, or Grok Bot.

The plugin bundles the eksis remote MCP connector with a skill that teaches
the assistant how each platform behaves, so it checks a channel's rules before
drafting rather than after a post fails.

## What it can do

- Read the workspace: channels, connection health, plan, and quota
- Read what each network allows, whether or not a channel is connected, and look
  up Pinterest boards and the TikTok creator options a post needs
- Check a post against every channel's rules before saving it
- Draft, schedule, reschedule, replace, and delete posts, and read the calendar
- Label posts made with AI on the networks that ask for it, and invite
  collaborators to Instagram posts
- Read the team's saved snippets, and keep notes on the idea board
- Manage the time slots of the posting queue
- Approve posts that contributors wrote, or send them back with a note
- Publish immediately, or retry the channels that failed, on request
- Import media from a public URL, check a file's status, and delete files
- Read, answer, hide, like, and delete comments, and mark them done
- Read and answer direct messages (paid plans)
- List comment and DM automations, and switch them on or off
- Read analytics for any period, per channel and per post type, with Instagram
  audience insights (paid plans), and the recent posts on a channel
- List the workspace's webhook endpoints. Creating or changing them stays in the
  eksis app and the REST API, never in the assistant.

48 tools in total. 24 only read; 24 create, change, or send, and each of those
is marked as a write tool. Claude and Cursor ask before they run one. In Grok
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
