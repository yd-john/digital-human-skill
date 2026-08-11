# Digital Human Skill

一个可复用的 Codex Skill，用于完成单人主播 AI 数字人口播的整条生产流程。

## 能做什么

1. 生成并固定数字人主播图片
2. 使用 Gemini TTS、ElevenLabs 或其他 TTS 服务确定音色
3. 调研选题并撰写快节奏口播文稿
4. 将文稿拆成视频生成提示词与 B-roll 规划
5. 通过 FLOVA、即梦/Dreamina 或其他 CLI/API 后端生成视频
6. 整合数字人片段、录屏和 B-roll
7. 在 ChatCut 中完成音频、动效、中英字幕和成片封装
8. 生成 4:3、3:4 封面以及标题、简介和标签

## 核心原则

- 音色与视频生成后端均可替换，不锁死单一平台。
- 全部提示词先审核，再生成第一段试片。
- 第一段通过后才批量生成，避免浪费积分。
- 每批记录使用平台、模型、任务 ID、费用或积分。
- 主播圆形画中画必须使用动态视频，不使用静态头像。
- B-roll 必须匹配口播，并隐藏 API key、路径、账号和其他隐私。

## 安装

下载仓库根目录的 `single-host-digital-human.skill`，或将 `single-host-digital-human/` 目录复制到：

```text
~/.codex/skills/single-host-digital-human
```

## 使用

在 Codex 中调用：

```text
使用 \$single-host-digital-human，这期主题是……预计两分钟，先从文稿开始。
```

技能会检查现有素材并从已完成阶段继续，不会无故重新生成已经批准的图片、声音、文稿或片段。

## 目录

```text
single-host-digital-human/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── production-planning.md
    ├── video-generation.md
    └── chatcut-publishing.md
```

## 说明

本仓库只包含工作流与提示词规范，不包含人物图片、音频、Logo、API key、录屏或项目私有素材。
