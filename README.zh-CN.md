# Y2K Pixel Doodle

[English](README.md) | 简体中文

将照片转成白底手绘像素涂鸦，重现早期电脑画图软件的随性笔触。保留主体可以辨认的姿态与表情，同时用略歪的鼠标线条、松散涂色和微型彩色贴图，画出低清又有手作感的画面。

适用于人物、宠物、物件、建筑和风景。你可以直接要求生成插画，也可以只获取可复用的生图提示词。

## 生成示例

每组对照图都是一张完整图片：左边是原图，右边是对应的生成插画。

### 动物

![动物对照：左侧猫咪原图，右侧生成的像素插画](examples/cat-comparison.png)

### 建筑

![建筑对照：左侧庭院原图，右侧生成的像素插画](examples/courtyard-comparison.png)

## 风格特点

- **全图共用一支像素笔。** 五官、主体轮廓、背景结构线和装饰使用一致的像素尺度、线条粗细与手绘抖动，避免面部过于精细。
- **保留人物或动物的神态。** 根据视线、眼睛开合、眉毛和嘴角重绘表情，同时保留主体姿态、辨识特征与空间关系。
- **保留手绘失误。** 轮廓略歪，有少量断笔、回描和错位；色块允许露白或稍稍涂出边界，画面不追求精确描摹。
- **根据画面调整背景。** 人物、宠物或物件图只用少量弯曲的结构线交代环境；纯风景则保留重要轮廓和空间层次。
- **点缀微型涂鸦。** 默认在留白处加入少量彩色爱心、星星、圈线等小装饰，大小和位置略有变化。
- **参考原图构图。** 默认沿用画面比例、主体位置和裁切，并尽量保留原图像素尺寸；具体生成和导出能力取决于可用工具。

你的明确要求优先于默认设置。例如，可以要求纯白背景、不加装饰，或指定新的画面比例。

## 环境要求与 Agent 适配

本技能采用 [Agent Skills 格式](https://agentskills.io/specification)，用同一份 `SKILL.md` 保存画风规则；安装入口和可用图像工具因平台而异。

- **直接出图：** 当前环境需要能读取原图，并有接受参考图片的生成或编辑工具。
- **提示词模式：** 能看图但没有合适的生图工具时，交付针对图片的提示词和已知尺寸，并说明尚未生成图片。
- **仅有文字描述：** 不能看图时，可以根据你的描述编写提示词，但不能核对照片内容。
- 技能不附带生图模型、API 账号或生成服务。安装 Skill 不会自动补齐这些能力；不同模型的出图效果也可能不同。

已提供 **Codex、WorkBuddy、豆包工作、Qoder、MiniMax Code 开源 CLI** 的安装指引；MiniMax Code 桌面端的具体导入方式仍待核对。这表示整理了相应接入方式，不代表新版已在所有产品上完成实测。具体情况见[兼容与测试记录](docs/compatibility.md)。

## 安装

请按[安装指南 / Installation guide](docs/installation.md)选择对应 Agent，包含本地技能包导入、CLI 目录、更新和调用方法。

Codex 用户可以把仓库地址发给助手：

> 请把 https://github.com/jiaxinyang1104/y2k-pixel-doodle 安装为 Skill。

其他 Agent 可能需要先下载并导入本地技能包，不能一概假定粘贴 GitHub 链接就能安装。GitHub 用于分发文件；上架各平台技能市场是另外的流程。

## 使用方法

在所用 Agent 中开启新任务，上传图片，并通过名称调用已安装的 Skill。自然语言调用更便于跨平台使用；菜单或斜杠命令取决于具体客户端。

**生成插画**

> 用 `y2k-pixel-doodle` 把这张照片转成白底手绘像素插画，保留姿态和表情。

Codex 也可以使用 `$y2k-pixel-doodle`；其他 Agent 可使用其技能选择菜单或支持的命令。

**加入风格参考图**

> 用 `y2k-pixel-doodle` 转绘图 1，参考图 2 的像素线条和配色。

**只写提示词**

> 用 `y2k-pixel-doodle` 根据这张图写一段生图提示词。

**调整默认效果**

> 使用纯白背景，不加小贴图，保持原图的横向比例。

## 文件结构

```text
y2k-pixel-doodle/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── docs/
│   ├── installation.md
│   └── compatibility.md
├── examples/
│   ├── cat.png
│   ├── cat-original.jpg
│   ├── cat-comparison.png
│   ├── courtyard.png
│   ├── courtyard-original.jpg
│   └── courtyard-comparison.png
├── README.md
├── README.zh-CN.md
└── LICENSE
```

- `SKILL.md`：触发说明、视觉规则和工作流程。
- `agents/openai.yaml`：保留 Codex 显示配置，通用执行规则放在 `SKILL.md`。
- `docs/installation.md`：各 Agent 的中英文安装和调用说明。
- `docs/compatibility.md`：区分官方接入说明与实际测试，提供验证用例。
- `examples/`：用于 README 展示的原图、生成插画和拼合对照图，并非运行 Skill 的必需输入。

## 许可证

Skill 指令和配套配置采用 [MIT 许可证](LICENSE)。示例图片及其原始素材可能涉及其他权利，发布者在公开或再分发前应确认使用范围。

