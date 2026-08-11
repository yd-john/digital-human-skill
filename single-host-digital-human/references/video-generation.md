# Video-generation adapters

Read this file when choosing a video provider, converting approved narration into prompts, or generating clips through a CLI/API.

## Select providers instead of hard-coding them

Choose the voice and video providers per project. Valid examples include:

- voice: Gemini TTS, ElevenLabs, or another accessible TTS CLI/API;
- video: FLOVA with Seedance, 即梦/Dreamina CLI, or another accessible image-to-video/talking-head backend.

Honor an explicit user choice. Otherwise compare providers by:

- Chinese naturalness and pronunciation;
- identity and lip-sync stability;
- reference-image and reference-audio support;
- maximum duration and aspect ratios;
- queue speed, retry behavior, and output download support;
- cost, credit balance, and whether usage can be reported;
- available local skill, CLI, connector, or documented API.

Do not silently switch providers after approval. If the selected provider is unavailable, show the constraint and propose the closest available fallback.

## Normalize each generation job

Track these fields regardless of backend:

```text
segment_id:
voice_provider / voice_model / voice_profile:
video_provider / video_model:
presenter_image:
reference_audio or narration_audio:
prompt:
duration_seconds:
aspect_ratio:
provider_project / job_id:
output_path:
cost_or_credits:
status:
```

This normalized record allows the workflow to replace FLOVA with 即梦, or Gemini TTS with ElevenLabs, without rewriting the editorial plan.

## Segmentation

- Match clip duration to measured narration and the selected model's real limit.
- Split at complete semantic beats and keep one key idea per clip.
- Do not assign every clip the maximum duration mechanically.
- For Seedance 2.0, default to 6–15 seconds.
- For a model supporting 30 seconds, use the longer duration only when it improves continuity.
- Generate a presenter clip for every narration segment even when B-roll will later cover part of it.

## Provider-neutral presenter prompt

Do not add timestamps inside the prompt. Adapt field labels only when a provider requires another syntax.

```text
【风格】真实科技 YouTube 主播口播（Tech Creator Talking Head, Photorealistic, Naturalistic Cinematography），16:9 横版，真实摄影质感；年轻、灵动、轻松带笑，保留自然皮肤微纹理、真实牙齿和口腔深度。

【时长】{X 秒}

【场景】严格保持参考图片中的同一主播、发型、眼镜、黑色高领服装、笔记本电脑、墙面 Logo、空间结构和蓝紫灯光。禁止重构背景或增加奖牌、桌面物件。

【角色与参考】科技内容主播；图片使用 {主持人参考图}；声音使用 {固定音色参考音频或本段旁白音频}。

【数字人口播台词】「{本段完整台词}」

【表演】直视镜头，语速轻快连贯；自然眨眼、轻微头部和肩颈联动，表情随语义变化；安排一到两个克制自然的手势，手势结束后自然回落。口型、下颌、脸颊与眼神共同参与发音，避免只有嘴唇局部运动。

【镜头】{指定起始景别和最多一次切镜，例如：正面中景起势，在语义转折处干净切到略侧面的面部近景；不要随机频繁切镜。}

【声音连续性】仅保留已批准的中文人声；台词连续，无背景音乐、无额外音效、无强化环境音。

【约束】身份、脸型、发型、眼镜、服装、灯光、电脑和 Logo 保持稳定；自然眨眼；五指清晰、比例自然。禁止身份漂移、塑料皮肤、贴嘴感、延迟口型、双重嘴型、机械匀速、背景融化、电脑变形、Logo 重绘、随机奖牌、B-roll、录屏、字幕、标题、水印、极端嘴唇微距、人物离场和场景重构。
```

## Adapter notes

### FLOVA / Seedance

- Read the installed FLOVA skill before using the released CLI.
- Upload or reuse the approved image and reference audio.
- Respect the selected Seedance model's duration limit.
- Poll the job rather than assuming immediate completion.
- Record FLOVA credits before and after each batch.

### 即梦 / Dreamina

- Read the installed Dreamina CLI skill before login, upload, submit, poll, or download operations.
- Confirm whether the chosen model accepts both image and audio references. If it accepts only image plus text, generate narration separately and plan lip-sync or B-roll coverage accordingly.
- Record the model, job ID, output path, and any provider-visible usage.

### Other provider

- Use an available local skill, connector, official CLI, or documented API.
- Map its required fields into the normalized job record.
- Verify reference support, duration, cost, and polling before submitting a paid job.
- Do not invent unsupported parameters.

## Shot variation

Vary the start and one optional cut across adjacent segments:

- front medium → front close;
- slight side medium → front close;
- front close → desk-above medium with one gesture;
- stable medium with no cut for pronunciation-sensitive lines.

Specify the pattern. Do not ask the model to decide every cut freely; uncontrolled cuts often rebuild the set or jump axis. For 10–15 seconds, request roughly two or three natural blinks without robotic regularity. Avoid a mouth-only close-up.

## Pronunciation and repair

Test every product name and Chinese phrase that the selected TTS may misread. If a word is wrong:

1. adjust punctuation, spacing, phonetic spelling, or the TTS provider's pronunciation controls;
2. regenerate only that audio or clip when the cost is reasonable;
3. otherwise mute the generated clip and replace it with the approved TTS audio;
4. cover visible mismatch with relevant B-roll and use a moving presenter bubble only when credible.

## Generation gate and reporting

Before submitting any job, confirm:

- voice provider/profile and video provider/model are approved;
- image and audio references are uploaded or mapped correctly;
- prompt and requested duration match the reviewed table;
- project, aspect ratio, cost mode, and current balance are recorded when available.

Generate the first clip only. Inspect it before the batch. Report every batch as:

```text
Provider / model: {value}
Generated: {segment IDs}
Estimated cost or credits spent: {amount or not exposed}
Balance remaining: {amount or not exposed}
Failed or regenerated: {segment IDs and reason}
```

Do not hide a provider failure or silently retry a credit-consuming request.
