# AI导演

AI导演（ai-director）是一个面向剧本、影像风格与AI视频创作的 Codex 插件，包含31位导演视角、导演协作编排，以及“分镜导演”技能。

## 分镜导演

安装插件后可使用：

```text
$ai-director:storyboard-director
```

用于将剧本或场景拆解为专业分镜表，检查轴线、景别、机位与构图，并生成适配 AI 视频工具的单镜提示词。

## 本地插件结构

```text
.codex-plugin/plugin.json
skills/
```

## AI视频提示词导演

```text
$ai-director:ai-video-prompt-director
```

将单镜动作或分镜简报扩写为制作级美式英语 AI 视频提示词，支持角色与场景锚点、动作物理、摄影灯光、一致性锁、T2V/I2V 分流和失败诊断。它可以与“分镜导演”协作：先拆镜，再逐镜生成提示词。
