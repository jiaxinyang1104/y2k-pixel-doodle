# Compatibility and tests / 兼容与测试

[Installation / 安装指南](installation.md) · [English README](../README.md) · [中文说明](../README.zh-CN.md)

## 中文

### 当前状态

文档核对日期：**2026-11-10**。本次完成的是通用指令适配与文档检查，未在其他 Agent 中批量安装，也未调用生图服务进行跨平台出图测试。

“官方支持某种技能接入方式”“本技能成功安装”和“本技能能在该环境交付图片”是三种不同结论。下表分别记录，不能用官方安装文档代替实际测试。

| 环境 | 官方接入依据 | 本修订安装/调用实测 | 参考图出图实测 | 测试版本 |
| --- | --- | --- | --- | --- |
| Codex | 本地技能目录与技能安装流程 | 待记录 | 待记录 | 未记录 |
| WorkBuddy | 上传本地技能包 | 待测试 | 待测试 | 未记录 |
| 豆包工作 | 官方介绍支持自建与本地导入；具体包格式待核对 | 待测试 | 待测试 | 未记录 |
| Qoder 桌面端 | 上传 ZIP、`.skill` 或 `SKILL.md` | 待测试 | 待测试 | 未记录 |
| Qoder CLI | 用户级/项目级技能目录 | 待测试 | 待测试 | 未记录 |
| MiniMax Code 开源 CLI | 工作区技能目录 | 待测试 | 待测试 | 未记录 |
| MiniMax Code 桌面端 | 独立客户端的具体导入方式待核对 | 待测试 | 待测试 | 未记录 |

官方链接与目录细节见[安装指南](installation.md)。已有 README 示例用于说明画风，不证明本次修订在每个 Agent 上都已通过测试。

### 每种能力下应交付什么

| 当前实际能力 | 预期结果 |
| --- | --- |
| 能看图，且工具支持参考图生成/编辑 | 分析原图并生成图片；实际传入参考文件，检查成图后交付 |
| 能看图，但没有合适的参考图工具 | 完整的定制提示词、已知原图尺寸、参考图分工；明确尚未生成图片 |
| 不能看图，仅有用户文字描述 | 根据描述编写提示词，注明未核对原图；不猜测画面细节或像素尺寸 |
| 用户只要提示词 | 输出提示词，不启动生图 |

精确像素尺寸还取决于生成工具和导出工具。无法确认宽高时，不填写猜测值；只能保持比例或无法按原尺寸导出时，说明实际限制。模型不同，结果可能不同；兼容不代表逐像素一致。

### 建议测试用例

以下用例用于实际验收，当前不宣称已经跑过：

1. **人物：** 使用自己有权处理的照片，检查表情和姿态是否保留，五官与衣物轮廓是否共用粗糙像素线。人物照片不必作为公开仓库素材。
2. **动物：** 使用 `examples/cat-original.jpg`。检查耳朵、眼神、身体姿态，以及歪轮廓、漏白填色和小贴图的尺度。
3. **建筑/环境：** 使用 `examples/courtyard-original.jpg`。检查主要建筑轮廓、树的位置、前后景关系；环境作为主体时不能只剩空白。
4. **提示词模式：** 对同一原图明确要求“只写提示词”。应得到具体内容和完整风格规则，不能触发生图。
5. **无生图能力：** 在没有参考图生图工具的环境运行。应交付提示词并说明限制，不能声称已生成。
6. **无图片理解能力：** 使用无视觉能力的环境。应指出不能核对原图，可按用户描述工作，不虚构图片内容。
7. **多图：** 两张独立原图应分别处理；原图加风格图则应标清角色，不能把风格图主体混入结果。
8. **画幅：** 用已知宽高的横、竖图，记录实际文件宽高与裁切。工具未支持原尺寸时，检查是否如实说明限制。

### 记录一次实际测试

记录：日期、Agent 名称与版本、操作系统、模型、图片理解方式、生图工具/连接器、技能修订或提交号、测试用例、输入尺寸、输出尺寸、结果、失败原因。没有验证的项保持“未测试”，不要从安装成功推断出图成功。仅公开已获授权的测试素材。

## English

### Status and scope

Documentation was checked on **2026-11-10**. This revision adds host-neutral execution rules and installation notes. It has not been installed and image-tested across the listed agents as part of this update. No exact client versions are claimed.

The table above separates documented integration, actual installation/invocation testing, reference-image generation testing, and tested version. Codex is pending a recorded run for this revision; all other listed clients are untested. MiniMax Code's documented workspace routes refer to its open-source CLI, not a verified import path for its desktop application. Doubao Work's exact accepted package format also remains unverified. Existing example images demonstrate the style, not cross-agent acceptance.

### Expected behavior

- With image understanding and a reference-image generation/editing tool, actually pass the source file, generate the image, and inspect the result.
- With image understanding only, return a tailored prompt, known dimensions and reference roles; clearly state that no image was generated.
- Without image understanding, work from the user's description, mark the source as unverified, and do not invent visual details or dimensions.
- For a prompt-only request, do not invoke generation.

Dimensions depend on both generation and export support. Report unverified sizes or tool limitations rather than claiming exact preservation. Cross-agent compatibility does not mean identical output across models.

### Acceptance cases and evidence

Use a permitted portrait, the included cat photo, and the courtyard photo. Check expression, pose, a shared coarse grid for face/body/background, imperfect lines, scribbly fills, tiny stickers, and subject-dependent background density. Also check prompt-only mode, missing generation capability, missing vision, separate-image versus style-reference roles, and portrait/landscape frame handling.

For each run record the date, host/version, OS, model, vision method, image tool, skill revision/commit, case, source/output dimensions, outcome and failure details. Leave untested fields marked as such. Installation success alone is not proof of image-generation success. Use private test inputs locally unless publication is authorized.
