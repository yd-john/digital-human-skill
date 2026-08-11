# Production planning

Read this file when writing the script, estimating duration, deciding presenter versus B-roll, or building the segment table.

## Production manifest

Maintain a compact file or equivalent project state:

```markdown
# Episode manifest
- Topic:
- Audience:
- Target duration:
- Platform / aspect ratio:
- Presenter master image:
- Logo:
- Voice provider / model / profile / reference audio:
- Script status:
- Prompt-table status:
- Video provider / CLI or API / model / project:
- Cost or credits before / spent / remaining:
- Screen recording and B-roll sources:
- ChatCut project / timeline:
- Export:
- Covers:
```

## Script rules

- Open with the result or promise in one or two sentences.
- Explain only the main workflow and decisions a viewer can reuse.
- Use short spoken sentences and natural connectors.
- Avoid repeating the title, production notes, visual instructions, or later user feedback inside narration.
- Say the providers actually used in the episode consistently. Do not claim Gemini TTS, ElevenLabs, Seedance, FLOVA, or 即梦 was used unless it was selected for that episode.
- Add punctuation or phonetic spacing when TTS misreads a term. Test difficult terms before batch generation.
- Default brisk pace: 48–55 Chinese characters per 10 seconds, approximately 72–82 per 15 seconds. Treat this only as planning; synthesized audio duration is authoritative.
- If the actual audio is too long, shorten or split the line. Avoid extreme speed-up that sounds mechanical.

## Segment table

Use this table for user review:

| # | Timeline | Duration | Visible picture | Spoken line | Video provider / model | Status |
|---|---|---:|---|---|---|---|
| 01 | 00:00–00:12 | 12s | Presenter | … | FLOVA / Seedance 2.0 | prompt review |
| 02 | 00:12–00:22 | 10s | Full-screen B-roll + moving circle | … | 即梦 / selected model | prompt review |

After the table, print every host prompt in segment order. Do not generate before the user approves the complete set.

## Presenter and B-roll decisions

Keep the presenter visible for approximately 55–65% of the finished video. Favor presenter footage for:

- hook and promise;
- transitions into major steps;
- personal judgment, warnings, and conclusions;
- final takeaway and call to action.

Favor B-roll for:

- image-generation iterations;
- the selected TTS interface or audio selections;
- script, prompt table, and CLI operations;
- the selected video provider's project or generation progress;
- ChatCut timeline, captions, effects, and final export.

Generate host footage under the whole narration anyway. This preserves a complete fallback track and consistent voice. Overlay B-roll only where it adds evidence or hides a defective visual.

## Screen-recording selection

The user may upload one long recording of the full conversation. Inspect it and cut by semantic match, not by fixed durations. Prefer ranges that clearly show a result changing or an action completing. Reframe to the useful area and add a gentle slow push rather than leaving a static full-screen capture.

Redact or crop:

- API keys and secrets;
- thread IDs and private URLs;
- local filesystem paths;
- email, account, or billing details;
- credit balance unless the user explicitly wants it public;
- unrelated chat and dead scrolling.

Use a moving circular presenter video when a face bubble is useful. Never substitute a still portrait.
