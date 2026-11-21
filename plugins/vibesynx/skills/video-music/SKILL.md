---
name: video-music
description: Compose original music for a video or build a music slideshow from photos with VibeSynx. Use when the user wants a soundtrack, background music, or music for a clip, reel, slideshow or photo set.
---

# Music for a video with VibeSynx

The `vibesynx` MCP server does the work. Jobs cost money or free credit, so the
user decides before anything is started.

## Steps

1. **Check the account** with `get_account`. Note the balance, the free credit
   status and how many jobs may run at once. If the server is not connected,
   Claude Code opens the sign-in; the user signs in on the VibeSynx console
   with their phone number and approves the connection.

2. **Get the video in.**
   - A public link (`https://...`): pass it as `video_url`.
   - A local file: call `create_upload_link` with `kind: "video"`, then run
     `curl -F video=@/path/to/file <url>` from the terminal, or give the user
     the link to open on their phone. Call `get_upload` until it reports
     `uploaded`. Use the `upload_id`.
   - Limits: longer than 15 s, at most 150 s and 300 MB.
   - For a slideshow: 3–10 photos (JPEG, PNG or WebP, at least 300 px on each
     side), as `image_urls` or one upload link per photo with `kind: "image"`.

3. **State the price and ask.** Call `estimate_cost` with the video's length
   (from `get_upload`, or ask). It prices all three qualities (`basic`,
   `enhanced`, `studio`); they are not ordered by price, so quote the one the
   user wants and whether the balance covers it. Start nothing until the user
   agrees.

4. **Start the job** with `create_video_music` (or `create_slideshow_music`).
   Put the user's wishes in `direction`: mood, genre, tempo, instruments,
   moments to hit. Keep the original audio under the music with
   `keep_original_audio: true` when there is speech worth keeping.

5. **Wait** with `get_job` and `wait_seconds: 200`. A job takes two to four
   minutes; call again while it is still running. One job runs at a time on a
   new account, so do not start a second one before the first finishes.

6. **Hand over the result**: the video link, and the music on its own. The
   links expire about two hours after `get_job` fetched them; a later `get_job`
   gives fresh ones. Suggest the user download what they want to keep.

## When something is refused

- **Not enough free credit / balance used up**: run `estimate_cost` and offer
  the cheapest quality or a shorter clip, or point to
  https://platform.vibesynx.com/console to top up.
- **Already running a job**: wait for it with `get_job`, then try again.
- **Video too short, too long or too large**: trim or compress it first; the
  limits are above.
- **Temporarily unavailable**: wait a moment and retry the same call.

A failed job is never billed.
