# eksis plugin for Claude

Schedule, approve, and publish posts, answer comments and direct messages, and
read analytics across twelve social networks from your [eksis](https://eksis.io)
workspace, without leaving Claude.

The plugin bundles the eksis remote MCP connector with a skill that teaches
Claude how each platform behaves, so it checks a channel's rules before drafting
rather than after a post fails.

## What it can do

- Read the workspace: channels, connection health, plan, and quota
- Read what each network allows, whether or not a channel is connected, and look
  up Pinterest boards and the TikTok creator options a post needs
- Check a post against every channel's rules before saving it
- Draft, schedule, reschedule, replace, and delete posts, and read the calendar
- Manage the time slots of the posting queue
- Approve posts that contributors wrote, or send them back with a note
- Publish immediately, or retry the channels that failed, on request
- Import media from a public URL, check a file's status, and delete files
- Read, answer, hide, like, and delete comments, and mark them done
- Read and answer direct messages (paid plans)
- Read analytics (paid plans) and the recent posts on a channel
- List the workspace's webhook endpoints. Creating or changing them stays in the
  eksis app and the REST API, never in Claude.

38 tools in total. 19 only read; 19 create, change, or send, and Claude asks
before it runs any of those.

## Install

```
/plugin install eksis
```

The first tool call opens the eksis consent screen in your browser. You sign in,
pick **one workspace**, and choose whether Claude may write as well as read. The
connection then appears on the API page inside that workspace and can be
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
  request counts. eksis receives only the tool requests Claude makes, for example
  the caption it drafted for you, not the rest of your conversation.
- **How it is used.** To run the service you asked for: scheduling, publishing,
  reading comments and direct messages, and reporting analytics. The contents of your posts, comments, and messages are not
  used to train AI models.
- **Third-party sharing.** What Claude reads travels to Anthropic and is covered
  by Anthropic's privacy policy. eksis also passes content to the social platform
  you publish to, and uses named infrastructure providers listed in the policy.
  eksis does not sell personal data.
- **Retention.** Content lives as long as the workspace does. Closing the account
  deletes it. Per-record retention windows are listed in the policy, and
  <https://eksis.io/data-deletion> explains how to request deletion.
- **About this connection.** eksis stores which assistant is connected, the
  workspace and permissions granted, who granted them, when it was last used, and
  how many requests it has made.
- **Contact.** admin@eksis.io

## Support

- Documentation: <https://docs.eksis.io/en/mcp>
- Support: <https://eksis.io/support>
- Email: admin@eksis.io

## License

MIT. See [LICENSE](LICENSE).
