# Clipwave for Claude

**Give Claude a real video editor.** Generate shots, cut them on a multi-track
timeline, burn in captions, and export an MP4 — without leaving the chat.

Most media integrations stop at "here is a generated clip." Clipwave keeps going:
projects, a shared asset library, per-video timelines with video/voice/sfx/music
tracks, trims, transitions, subtitles, and a real export.

```
/plugin marketplace add clipwave/clipwave-plugins
/plugin install clipwave@clipwave
```

Then run `/mcp`, pick **clipwave**, and authenticate. That is the whole setup —
the server speaks OAuth 2.0 with dynamic client registration, so there is no key
to copy or config file to hand-edit.

## What you get

| | |
|---|---|
| **2 skills** | `video-generation` (model choice, submit, poll) and `video-editing` (timeline, captions, export) |
| **2 commands** | `/clipwave-video` to generate a shot, `/clipwave-edit` to work a timeline |
| **1 connector** | The hosted Clipwave MCP server — ~20 tools |
| **1 setup skill** | Walks Claude through connecting, including the headless API-key path |

## Example

> Generate three 5-second shots of a ceramic mug on a windowsill — wide, then a
> slow push-in, then a top-down. Cut them together with 0.4s fades, add the
> voiceover from `vo.mp3`, subtitle it TikTok-style, and export vertical.

Claude reads the model catalogue, picks the right text-to-video id, submits and
polls three jobs, creates a project, places six clips across two tracks, sets the
transitions, burns the captions, and hands back an MP4 URL.

## Requirements

A [Clipwave](https://clipwave.io) account. Generation spends credits; every
read-only tool (`list_models`, `job_status`, and the `get_*` / `list_*` family)
is free, and so are the deterministic timeline operations — placing, removing,
reordering, transitions and captions.

## Headless use

For CI or server agents with no browser, create a key at
[clipwave.io/dashboard/api-keys](https://clipwave.io/dashboard/api-keys) and send
`Authorization: Bearer cw_live_…`. There is also a stdio package,
[`@clipwave/mcp`](https://www.npmjs.com/package/@clipwave/mcp), for clients that
cannot reach a remote server.

## Also works with

Cursor, Windsurf, and any MCP-compatible client — the server is plain streamable
HTTP at `https://clipwave.io/api/mcp`. See [clipwave.io/mcp](https://clipwave.io/mcp)
for the full tool catalogue.

## Links

- [Tool catalogue and live docs](https://clipwave.io/mcp)
- [REST API docs](https://clipwave.io/docs/api)
- [Privacy policy](https://clipwave.io/privacy) · [Terms](https://clipwave.io/terms)
- Issues and support: open an issue here, or contact us via the site.

## License

MIT — see [LICENSE](LICENSE). Clipwave is an independent product; it is not
affiliated with or endorsed by Anthropic.
