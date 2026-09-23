---
name: publishing-with-eksis
description: Use when scheduling, drafting, or publishing social media posts through eksis, or answering comments on connected channels - covers picking channels, respecting per-platform rules, and the difference between scheduling and publishing now
---

# Publishing with eksis

eksis reaches twelve social networks through one workspace. The tools are the
same API the eksis web app uses, so a post created here appears in the user's
calendar and is published by the same worker.

## Start by looking, not guessing

Call `get_workspace` first. It names the workspace, its time zone, the plan, the
role you act with, and the daily request quota. Every time you talk about a
schedule, use the workspace time zone, never your own.

Then call `list_channels`. Each channel carries the rules of its own platform:
which content types it can publish, caption and media limits, whether text-only
posts are allowed or media is required, and which comment actions exist. Use the
channel id from there as the target of a post.

For a network the workspace has not connected yet, call
`get_platform_capabilities`. It answers the same questions without a channel, so
you can tell the user what connecting would make possible.

## Rules worth knowing before you draft

Platforms differ in ways that break a post silently if you ignore them:

- YouTube and TikTok publish video only. There is no text-only post.
- Instagram needs an image or a video. A caption alone is not a post.
- Caption limits differ by an order of magnitude between networks. Read the
  limit from the channel rather than assuming.
- Not every platform exposes comments, DMs, or metrics.

When one caption is going to several channels, check the shortest limit first,
and say so rather than quietly truncating the user's words.

## Scheduling is the default, publishing now is not

`create_post` saves a draft unless `mode` says otherwise, and a draft does not
go out even when it carries `scheduledAt`. To schedule, send `mode: "schedule"`
with `scheduledAt` as ISO-8601 with an offset. `mode: "queue"` takes the next
free slot in the channel queue instead. The user can still edit or delete a
scheduled or queued post.

`create_post` with `mode: "now"`, and `publish_post`, send the post to the
platform immediately, and **eksis cannot take that back**. Treat those two as
one-way doors: confirm with the user before calling them, and never publish now
because it seemed faster. Publishing runs in the background, so call `get_post`
afterwards and tell the user how each channel ended up.

`delete_post` only removes posts that have not gone out yet.

## Media

`upload_media_from_url` imports a file from a public URL into the workspace
library, which is how you attach media you did not upload by hand. It does not
change anything outside eksis. Attach media by the ids from `list_media` or
from the import itself: an id eksis does not know is refused, not skipped.

## Comments

`list_comments` reads comments on published posts, and `reply_to_comment` answers
one. A reply is public and immediate. Draft it, show it to the user, then send.

## When something fails

Tool errors carry a `code`, a `hint`, and `details`. Read the hint before
retrying: most failures are a rule you can satisfy, such as a missing image or a
caption over the limit, not an outage.
