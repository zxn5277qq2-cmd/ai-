---
name: ai-video-prompt-director
description: Use when users need AI视频提示词、Seedance提示词、Higgsfield提示词、动作扩写、镜头提示词、图生视频动作、T2V/I2V、角色一致性、物理运动、生成失败诊断，或需要把单镜需求、参考图、场景节拍及storyboard-director分镜转换为美式英语视频提示词。
---

# AI视频提示词导演

把故事意图转换为可观察、可生成、可迭代的单镜视频指令。优先保持叙事清晰、角色一致和物理可信；不要用形容词堆叠代替导演决策。

## 工作分流

1. 单镜且动作明确：直接生成快速单镜提示词。
2. 单镜但表演、参考图或连续性复杂：生成制作级分块提示词。
3. 多镜剧情：先使用 `$ai-director:storyboard-director`，再按镜头交接格式逐镜处理。
4. 用户报告生成失败：先按症状诊断，只修改一个导致失败的模块。

仅在缺少信息会明显改变结果时询问一个问题。独立单镜缺少时长时询问时长；若用户要求立即给出，提供 8 秒版本并明确这是工作假设。

## 镜头交接格式

接收或建立这些字段：Shot ID、Duration、Narrative Beat、Character Anchors、Setting Anchors、Action Beats、Camera、Lighting、Continuity。

## 构造顺序

1. 把模型、画幅、时长等平台参数放在正文之外。
2. Identity Block：只写角色静态外观、服装、材质、比例和固定配件。
3. Setting / GEO Block：写空间、道具、光源位置；连续多镜复用同一空间地图。
4. Motion Block：写初态、一个主要动作、最多两个简单次要动作和最终状态。
5. Physics Block：写重心、接触面、惯性、呼吸、衣料、绒毛、液体和饰品反馈。
6. Camera Block：写景别、视场角或焦段、机位、构图和一种主要运镜及终点。
7. Look Block：写光源、色温、阴影、材质和画面质感。
8. Positive Locks：用正向描述锁定身份、服装、空间和首尾状态。

## T2V 与 I2V

- T2V：完整描述主体、环境、动作、摄影和画面质感。
- I2V：输入图已经定义身份和静态构图，只写发生变化的动作、表情、环境运动和摄影机运动。
- 多参考图：明确 Character、Environment、Prop、Start Frame、End Frame 的角色，不继承无关构图。

## 表演与物理

- 把抽象情绪拆成眼神、面部肌肉、呼吸、姿态、手部和停顿。
- 动作遵循预备、发展、峰值、收尾；连续情绪崩溃保持为一个表演弧。
- 毛绒角色写明软体压缩、绒毛惯性、耳朵和配件的滞后、回弹与逐渐静止。
- 多角色明确画面位置、身体分离、动作主次和各自最终状态。

## 输出模式

### 快速单镜

输出参数行、一个可直接复制的美式英语提示词和一行中文时间轴。

### 制作级单镜

依次输出镜头简报、Identity Block、Setting/GEO Block、Motion Block、Physics Block、Camera Block、Look Block、Positive Locks、参数和失败时的首个修复变量。

### 多镜协作

保留分镜编号；每镜自包含必要锚点；全局风格和场景 GEO Block 原文复用；逐镜提示词不依赖上一条隐含信息。

## 交付前检查

- 时长能容纳所有动作，且只有一个主要动作。
- 情绪已经物理化，没有只写 sad、angry、epic、beautiful 或 cinematic。
- 摄影机只有一种主要运动并有明确终点。
- I2V 没有重复描述输入图中的静态外观。
- 多角色身体分离，空间方向和出入画方向明确。
- 使用正向一致性锁，不在正文堆叠负面提示。
- 输出为美式英语；中文仅作说明。

需要模板、GEO 空间锁和失败诊断时，读取 [references/prompt-patterns.md](references/prompt-patterns.md)。

