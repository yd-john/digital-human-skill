# ChatCut finishing and publishing

Read this file when assembling clips, placing B-roll, styling subtitles, repairing audio, verifying the cut, exporting, or producing covers and metadata.

## Assembly order

1. Put host clips in narration order and mute duplicate audio tracks.
2. Make speech continuous before adding visual decoration.
3. Add relevant B-roll over the baseline host track.
4. Add moving circular presenter video only where it improves continuity.
5. Add chapter cards and restrained motion.
6. Add Chinese and English captions.
7. Verify, then export.

## Audio

- Use the approved audio from the selected TTS provider where generated pronunciation is wrong.
- Apply light denoise and de-click only as needed; avoid metallic over-processing.
- Match segment loudness and tone.
- Use short audio fades or crossfades, normally about 80–150 ms, to remove clicks and abrupt joins.
- Check every seam with headphones.
- Use background music only when requested; keep it clearly below narration.

## B-roll and presenter bubble

- Cut screen recordings to the spoken step and reframe around the useful interface region.
- Add a gentle slow push to static-looking captures.
- Use clean cuts or subtle dissolves; avoid effect-heavy transitions.
- For a presenter bubble, crop the actual moving host video into a circle and place it in a safe corner. Keep the host moving; do not use a still image.
- Cover generated frames containing unwanted desk awards, reconstructed props, or severe mouth errors with B-roll when a clean source is unavailable.

## Technology-creator graphics

- Use a concise opening title and one chapter card per major step.
- Keep cards top-left, compact, translucent, and blue/cyan/purple.
- Use large two-digit chapter numbers, bold Chinese heading, and small uppercase English label.
- Animate with a short rise/fade and a restrained accent line. Do not obscure the face.

## Bilingual captions

For a 1920×1080 timeline, use this starting point and adjust after visual inspection:

- Chinese: HarmonyOS Sans or Noto Sans SC, about 46–50 px, 800 weight, white, subtle dark stroke/shadow, one line where possible.
- English: Inter, about 22–26 px, 500 weight, cool gray-blue, directly below Chinese, visibly smaller.
- Place both near the bottom safe area, centered, without covering the host's hands or face.
- On bright B-roll, add a narrow transparent-to-dark bottom gradient behind captions. Avoid a large opaque gray subtitle panel.
- Keep English concise and faithful; do not show duplicate caption sources.

## Visual verification

Inspect actual rendered pixels, not only timeline metadata. Sample:

- opening title;
- every chapter card after its entrance settles;
- several full-screen B-roll moments;
- every presenter-bubble section;
- host-only frames between B-roll spans;
- the final closing shot.

Confirm no gradient, chapter card, or bubble spills into unintended ranges. Check that captions remain readable and low enough without being cropped.

## Cover and metadata

Use GPT Image with the original approved presenter image as the identity reference. Generate separate compositions rather than cropping one cover:

- horizontal 4:3;
- vertical 3:4.

Default visual direction: premium blue-purple technology studio, confident friendly presenter, one natural hand gesture, laptop and wall mark secondary, clean dark negative space for copy. Keep text to:

```text
AI 数字人口播
从 0 到成片
```

Require exact text, no extra characters, no watermark, natural five-finger hands, and no medals on the desk.

Recommended title pattern:

```text
不用真人出镜：{文稿工具} + {TTS 提供方} + {视频模型或平台} 数字人口播全流程
```

Description pattern:

```text
这期完整演示一条可以重复使用的 AI 数字人口播流水线：确定主播形象、完成文稿并拆分提示词；使用 {实际 TTS 提供方} 确定声音；通过 {实际视频平台与模型} 生成数字人口播片段；最后加入 B-roll、科技动效和中英双语字幕，剪辑输出完整成片。主播形象和音色只需确定一次，以后每期主要更换选题、文稿和分段提示词，就能继续生产新内容。
```

Adapt the title and description to the actual episode rather than copying the example blindly.
