---
name: single-host-digital-human
description: "Orchestrate a complete single-host AI digital-human talking-head production from topic to publishable deliverables: lock a presenter image, establish a reusable voice with Gemini TTS, ElevenLabs, or another TTS provider, write a fast Chinese script, segment it into video prompts, generate through FLOVA, Dreamina, or another CLI/API backend, align uploaded B-roll, finish bilingual tech-creator editing in ChatCut, and create covers, title, and description. Use for 单人主播数字人、数字人口播、AI 主播教程、从选题到成片, multi-provider TTS/video workflows, or when resuming any stage of this production pipeline."
---

# Single-host digital-human production

Build one reusable presenter identity and voice, then turn each topic into a fast, polished technology-creator video. Treat presenter image and voice as persistent assets; change the topic, script, prompts, and B-roll per episode.

## Operating contract

- Resume from completed artifacts. Never regenerate an approved image, voice, script, prompt, or clip without a reason.
- Work one approval gate at a time. Do not spend credits or start paid generation before the user approves all prompts.
- After prompt approval, generate only the first host clip as a pilot. Continue the remaining batch only after the pilot passes.
- After every generation batch, report the provider, estimated cost or credits spent, and the current balance when the provider exposes one.
- Keep production notes out of the spoken script. The script contains only audience-facing narration.
- Keep the pace concise and useful. Remove setup chatter, repeated explanations, and tool details that do not help the viewer.
- Use the original approved presenter reference for new image generations. Avoid iterative editing from an already regenerated image because identity and sharpness drift.
- Never expose API keys, thread URIs, local file paths, private account data, or credit balances inside public B-roll.
- Never create a static circular avatar when the user asks for a small presenter bubble. Use a moving presenter video cropped into a circle.

## Start or resume

Inspect the current project before acting. Record or recover:

- topic, audience, target duration, platform, aspect ratio;
- approved presenter image and logo;
- approved TTS provider, model, voice/reference audio, speed, and pronunciation notes;
- approved script and segment table;
- selected video provider, CLI/API, model, generated host clips, uploaded screen recordings/B-roll, and current provider balance;
- ChatCut project/timeline and current export status.

Create a compact production manifest when no equivalent exists. Use the template in [production-planning.md](references/production-planning.md). Mark every artifact `draft`, `approved`, `generated`, `needs-fix`, or `final`.

## Workflow

### 1. Lock the presenter image

Use the image-generation skill with the user's character reference and logo. Default to a photorealistic 16:9 technology studio with restrained blue, cyan, and purple lighting, a premium laptop, and an integrated wall logo. Keep the person dominant; props and logo stay secondary. Generate one candidate, show it, and wait for approval.

Preserve the approved image as the master reference. Do not replace it during later video generation.

### 2. Choose and lock the voice

Choose an available TTS provider that fits the episode. Gemini TTS, ElevenLabs, and other CLI/API-accessible services are valid; do not require voice cloning. Compare natural Chinese delivery, speed control, consistency, cost, and whether the resulting audio can be reused as a reference. Generate a short audition in a young, lively, friendly, natural presenter style. Prefer brisk connected delivery over dramatic pauses.

Save the provider, model, voice ID/name, style instruction, speed, reference audio, and pronunciations as reusable assets. If a fixed voice already exists, reuse it. Never switch providers or voices after approval without telling the user and running a comparison sample.

### 3. Write and approve the script

Research only when the topic requires current or factual support. Write for the viewer, not for the production team. Default to a two-minute, fast tutorial unless the user gives another duration.

Target roughly 48–55 Chinese characters per 10 seconds, then measure the synthesized audio and adjust from real duration. Do not force dense text into an unnaturally fast read. Keep the hook short, make each step concrete, and end with one clear takeaway.

Present the complete script first. Do not split prompts until the user approves the wording, tone, and pace. Read [production-planning.md](references/production-planning.md) for pacing and table rules.

### 4. Build the segment and B-roll plan

Convert the approved script into a timestamped table. Default visible screen time is 55–65% presenter and 35–45% B-roll, but generate a presenter clip for every narration segment so the voice and identity remain continuous. During editing, cover selected portions with B-roll and optionally keep the moving presenter in a circular picture-in-picture.

Choose clip lengths from the selected video model's actual limits. For Seedance 2.0, default to 6–15 seconds and split lines that exceed 15 seconds. Use longer-capability models only when a longer uninterrupted performance materially helps and the user allows it.

Write all video prompts and show the complete table for approval before generation. Use [video-generation.md](references/video-generation.md) to select a provider adapter. Do not import an overly cinematic director template for ordinary talking-head segments.

### 5. Generate through the selected backend

Use any available backend that can satisfy the approved job: FLOVA CLI with Seedance, 即梦/Dreamina CLI, or another user-approved CLI/API service. Read the installed provider skill or official local instructions before operating it. Create or reuse one project, upload the approved presenter image and voice reference when supported, and map each segment to its approved duration and prompt.

Normalize each backend job to the same fields: provider, model, image reference, audio reference or narration, prompt, duration, aspect ratio, job ID, output path, and cost. Generate the first segment only. Check identity, pronunciation, lip sync, blinking, hands, background continuity, and camera changes. After approval, generate the remaining host segments. Do not silently regenerate failed clips; report the defect, likely cause, expected cost, and proposed correction first.

### 6. Assemble host clips and B-roll

Place all generated host clips in narration order. Accept one long user screen recording when convenient; inspect it and select only the ranges matching the spoken step. Hide dead scrolling, unrelated chat, private data, temporary paths, keys, and balances.

If a host clip reconstructs or introduces background objects that are not present in the approved reference, cover that interval with relevant B-roll or a reframed crop. When the original generated pronunciation is wrong, mute it and replace it with the approved TTS audio; conceal visible lip mismatch with B-roll while keeping a small moving presenter bubble only when it still looks credible.

### 7. Finish in ChatCut

Use ChatCut for ordering, B-roll, moving presenter bubbles, audio smoothing, motion graphics, bilingual subtitles, and export. Apply restrained technology-creator styling rather than effects on every cut. Read [chatcut-publishing.md](references/chatcut-publishing.md) before editing or exporting.

Repair audible joins with light denoise, loudness matching, and short audio crossfades. Keep Chinese captions dominant and English smaller underneath, both close to the bottom safe area. Add a subtle dark gradient behind captions on bright B-roll, not a large low-quality subtitle box.

Verify representative host, B-roll, chapter-card, and transition frames before reporting completion.

### 8. Create publishing assets

Use the original approved presenter reference with GPT Image to create:

- one 4:3 horizontal cover;
- one 3:4 vertical cover;
- one concise high-intent title;
- one platform-ready description and a short relevant hashtag set.

Keep cover text to one strong headline plus one short subline. Preserve identity and the established blue-purple studio. Save the final files in the project, not only in a temporary generation directory.

## Completion gate

Finish only when all of the following are true:

- approved master image and voice are recorded;
- final script and every segment prompt are approved;
- voice and video providers are recorded, all required host clips exist, and generation usage is reported;
- B-roll is aligned and private data is hidden;
- audio joins are smooth and pronunciation errors are repaired;
- bilingual captions and motion graphics are visually verified;
- the final video is exported or the user confirms they exported it;
- both cover ratios, title, and description are delivered.

Do not package or substantially rewrite this skill during an active episode unless the user explicitly asks to update the workflow.
