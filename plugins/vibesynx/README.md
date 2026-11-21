# VibeSynx for Claude Code

Cinematic-grade original music, composed for your footage — from inside Claude
Code. Give Claude a clip or a few photos, say what you want, and get the video
back with a soundtrack written to fit it.

## Install

```bash
claude plugin marketplace add galaxyontech/vibesynx-claude
claude plugin install vibesynx@vibesynx
```

The first time a VibeSynx tool is used, Claude Code opens a sign-in page on the
VibeSynx console. Sign in with your phone number, approve the connection, and
you are done: a key named "Claude" is created on your account for it. Revoke
that key on the console's API keys page to disconnect.

New accounts get a small free credit to try it; after that, top up at
https://platform.vibesynx.com/console.

## What it does

The plugin connects to the VibeSynx MCP server at `https://mcp.vibesynx.com/mcp`
and adds these tools:

| Tool | What it does | Costs money |
|---|---|---|
| `get_account` | Balance, free credit, jobs allowed at once, prices | no |
| `estimate_cost` | Price of a job before starting it | no |
| `create_upload_link` | A one-hour link to upload a local video or photo | no |
| `get_upload` | Whether the upload has arrived | no |
| `create_video_music` | Compose music for a video and deliver the remixed video | **yes** |
| `create_slideshow_music` | Turn 3–10 photos into a music slideshow | **yes** |
| `get_job` | Progress and result links | no |
| `list_recent_jobs` | Your recent jobs | no |

Claude asks before either paid tool runs. A job takes a few minutes; a job that
fails is never billed. Result links expire about two hours after they are
fetched, so download what you want to keep.

Videos must be longer than 15 seconds and at most 150 seconds and 300 MB.

## What it sends where

- Your video or photos, your directions and your account's API key go to the
  VibeSynx service (`mcp.vibesynx.com`, `api.vibesynx.com`) and nowhere else.
- Sign-in happens on `platform.vibesynx.com`. The plugin never sees your
  password or phone number.
- Nothing is sent to any third party by this plugin.

## Support

https://platform.vibesynx.com/console

## License

MIT — see `LICENSE`.
