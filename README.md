# eksis plugin for Claude

Schedule, publish, and answer comments across twelve social networks from your
[eksis](https://eksis.io) workspace, without leaving Claude.

The plugin bundles the eksis remote MCP connector with a skill that teaches
Claude how each platform behaves, so it checks a channel's rules before drafting
rather than after a post fails.

## What it can do

- Read the workspace: channels, connection health, plan, and quota
- Read what each network allows, whether or not a channel is connected
- Draft, schedule, replace, and delete posts
- Publish immediately, on request
- Import media from a public URL into the workspace library
- Read and answer comments on published posts

Thirteen tools in total. Seven only read; six create, change, or send, and Claude
asks before it runs any of those.

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
  reading comments. The contents of your posts, comments, and messages are not
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
