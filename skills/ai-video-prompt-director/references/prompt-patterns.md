# AI视频提示词模式参考

## MCSLA 映射

MCSLA 表示 Model、Camera、Subject、Look、Action。平台参数单列；提示词正文优先按 Subject → Action → Camera → Look 排列，把最重要的主体与动作放在前部。

## 快速单镜模板

参数：平台、时长、画幅、生成模式。

正文：`[Identity anchor]. [Initial state and primary action]. [Visible performance beats]. [Physical consequences]. [Camera and endpoint]. [Lighting and texture]. [Positive continuity locks].`

## 制作级分块模板

```text
IDENTITY BLOCK
SETTING / GEO BLOCK
MOTION BLOCK
PHYSICS BLOCK
CAMERA BLOCK
LOOK BLOCK
POSITIVE LOCKS
```

## GEO SPATIAL LAYOUT

多镜头场景先写纯空间地图：固定地标、左右关系、距离、180度轴线、摄影机允许区域和主光方向。不要在 GEO Block 中写动作；同一场景逐镜原文复用。

## 时长与复杂度

- 4–8 秒：一个主要动作。
- 8–12 秒：一个主要动作加一次揭示或情绪峰值。
- 12–15 秒：两至三个简单节拍。
- 超过两个强动作、两种运镜、三个重要角色或一个复杂特效时拆镜。
- 连续悲伤或崩溃表演不应被机械拆碎。

## 三小毛 8 秒结构示例

- 0–2秒：憋哭；下唇颤抖、眨眼、呼吸卡住。
- 2–5秒：情绪爆发；肩膀随抽泣起伏，泪水沿脸颊移动。
- 5–8秒：坐地蹬腿；软体服装受压，耳朵因惯性摆动并逐渐停止。
- 摄影：平视中全景，单一缓慢推进，终点为近景。
- Positive Locks：脸部、比例、服装、配件、背景与光线保持稳定。

## 失败诊断

| 症状 | 首个修复变量 |
|---|---|
| 漂浮或无重量 | 重心、接触面、惯性、落地反馈 |
| 变脸或服装漂移 | Identity Block 与参考图角色 |
| 多角色融合 | 画面坐标、身体分离、动作主次 |
| 运镜失控 | 只保留一种主要运镜并写终点 |
| 塑料感 | 自然主光、阴影深度、材质微细节、克制颗粒 |
| 动作未完成 | 减少动作节点或增加时长 |
| 空间跳变 | GEO Block、轴线与摄影机起点 |
| 审核失败 | 改写为原创主体和中性、可观察的场景语言 |

## 迭代纪律

每次只修改一个变量并记录结果。相同结构迭代 10–15 次仍不收敛时，不再润色措辞；拆镜、删动作、换机位或修正参考资产。失败视频先逐帧检查并保留可用片段。

## 来源说明

通用方法参考 OSideMedia 的公开仓库 `higgsfield-ai-prompt-skill`：https://github.com/OSideMedia/higgsfield-ai-prompt-skill 。该仓库采用 MIT License，Copyright (c) 2026 O-Side Media。本文件重新组织和概括通用制作方法，不复制其完整技能、平台执行接口或模型数据库。

