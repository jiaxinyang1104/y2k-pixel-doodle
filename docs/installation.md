# Installation / 安装指南

[English README](../README.md) · [中文说明](../README.zh-CN.md) · [Compatibility / 兼容记录](compatibility.md)

## 中文

### 先确认你需要的能力

这是指令型 Skill，不附带图片模型、API Key 或生图脚本。读取图片并写提示词，需要图片理解能力；直接转绘还需要一个接受参考图片的图像生成或编辑工具。纯文字生图工具不能替代参考图输入。平台能安装技能，不等于已配置好这些能力。

### 获取技能文件

仓库地址：<https://github.com/jiaxinyang1104/y2k-pixel-doodle>

可用 GitHub 的 **Code → Download ZIP** 下载。解压后，找到直接包含 `SKILL.md` 的文件夹。技能运行的必需文件是 `SKILL.md`；`agents/openai.yaml` 是 Codex 的显示补充，`docs/` 与 `examples/` 用于说明和展示。

需要导入技能包时，按客户端支持的格式选择文件；若源码 ZIP 被拒绝，先解压，再将直接包含 `SKILL.md` 的技能文件夹重新打包，避免额外套两层仓库目录。本仓库不承诺所有客户端接受相同的 ZIP 布局。

### Codex

把仓库地址发给 Codex：

> 请将 https://github.com/jiaxinyang1104/y2k-pixel-doodle 安装为 Skill。

也可按当前官方文档，将技能文件夹放入个人 `~/.agents/skills/` 或项目 `.agents/skills/`，例如 `~/.agents/skills/y2k-pixel-doodle/SKILL.md`。已有安装可能位于其他受支持目录；更新已有副本，避免同时安装多个同名版本。若列表未刷新，重启客户端。

调用时上传原图，并写“用 `$y2k-pixel-doodle` 把这张图转成白底手绘像素插画”。

来源：[官方技能说明](https://learn.chatgpt.com/docs/build-skills)。

### WorkBuddy

在左侧 **专家·技能·连接器 → 技能** 中选择 **添加技能 → 上传技能**，按文件选择器支持的格式导入本地技能包，检查已安装列表并启用。官方文档中的对话安装只针对技能市场条目；不要假定对话里粘贴任意 GitHub 链接就能安装本仓库。

在任务里上传原图，通过技能菜单选择或按名称说明要使用本技能。图像理解及参考图生成能力须在当前账号、模型和工具配置下另行确认。

来源：[WorkBuddy 技能说明](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)。

### 豆包工作

官方介绍支持自定义技能和导入本地技能文件。进入当前客户端的技能管理入口，使用本地导入功能，并按其要求选择技能文件。具体文件类型、包结构、按钮名称和本技能的参考图生图链路尚未实测，请以当前版本的导入提示为准；这里不提供未经核对的安装目录。

导入后，在新任务中选择技能或按名称调用，并上传原图。普通豆包聊天、豆包工作独立端和飞书入口的能力不应视为完全相同。

来源：[飞书官方的豆包工作介绍](https://www.feishu.cn/content/article/7677519271848610746)。

### Qoder

这里的 Qoder 指官方产品 Qoder；不能据此推断其他名为 QCoder 的产品也兼容。

- **Qoder 桌面端：** 进入 **扩展 → 技能 → 添加技能 → 上传 Skill**，可选择技能 ZIP、`.skill` 或 `SKILL.md`；不直接上传文件夹。在新任务里输入 `/`，从技能列表选择本技能。桌面端也会发现 `~/.agents/skills` 中的技能。
- **Qoder CLI：** 将技能文件夹放入 `~/.qoder/skills/y2k-pixel-doodle/`，或当前项目 `.qoder/skills/y2k-pixel-doodle/`。确认其内有 `SKILL.md`，启动新会话；已有会话可用 `/skills reload` 刷新。按技能名称或 CLI 提供的命令调用。

QoderWork 等独立客户端可能有自己的目录和界面，请使用对应文档，不混用 CLI 路径。

来源：[Qoder 桌面端](https://docs.qoder.com/zh/qoder/skills)、[Qoder CLI](https://docs.qoder.com/cli/Skills)。

### MiniMax Code

官方开源 MiniMax Code 文档确认支持工作区 `.agents/skills`、`.claude/skills`、`.minimax/skills`。例如，将技能文件夹放在项目的 `.minimax/skills/y2k-pixel-doodle/`，其内保留普通文件 `SKILL.md`，再在该工作区开启新会话。可用 `/skills` 检查当前会话发现的技能，再按实际列表调用。

以上是开源 CLI/工作区加载方式，不作为同名桌面客户端的导入路径保证。桌面端请按当前技能管理入口操作；具体包导入和图像生成能力仍待验证。

来源：[MiniMax Code 官方文档](https://github.com/MiniMax-AI/minimax-code/blob/main/docs/tui-capabilities.md)。

### 通用调用与更新

> 使用 y2k-pixel-doodle，把附件转成白底手绘像素插画，保持原图构图和表情。如果当前环境不能参考图生图，请输出完整提示词，并说明尚未生成图片。

只要提示词时，明确写“只写提示词，不调用生图工具”。多张图要标清哪张是原图、哪张是风格参考。

更新时，用新版替换原安装位置的技能文件，保留自己的修改备份；界面导入的版本按客户端支持的更新方式处理。重开任务并确认实际加载的是新版。GitHub 更新不会自动同步到所有已安装副本，也不会自动上架各平台技能市场。

## English

### Requirements and package

This instruction-only skill includes no image model, API credentials, or generation script. Photo-based prompts require image understanding. Redrawing also requires a generation/editing tool that accepts reference images. Installation alone does not supply either capability.

Download the repository through **Code → Download ZIP**. After extraction, locate the folder that directly contains `SKILL.md`. The skill's only required runtime file is `SKILL.md`; `agents/openai.yaml` is supplementary Codex metadata. Follow the importer's accepted format. If it rejects the repository archive, repackage the actual skill folder without extra directory nesting; archive layout acceptance has not been verified in every host.

### Installation by host

| Host | Installation and invocation |
| --- | --- |
| Codex | Ask it to install the repository URL, or place the folder in a supported user/project skills location such as `~/.agents/skills/y2k-pixel-doodle/`. Update an existing copy rather than creating duplicates. Invoke `$y2k-pixel-doodle` with the source image attached. |
| WorkBuddy | Open the Skills area under Experts/Skills/Connectors, choose Add Skill → Upload Skill, and import a local package accepted by the picker. Enable it in Installed. Its documented conversational installer targets marketplace entries, not arbitrary GitHub repositories. |
| Doubao Work | Its official introduction documents local skill import. Use the current client's skill management/import interface. Accepted package details and this skill's image workflow remain untested; no installation directory is assumed. |
| Qoder desktop | Extensions → Skills → Add Skills → Upload Skill accepts a ZIP, `.skill`, or `SKILL.md`. Folders cannot be uploaded directly. Select the installed skill through `/`. It also discovers `~/.agents/skills`. |
| Qoder CLI | Put the folder in `~/.qoder/skills/y2k-pixel-doodle/` or project `.qoder/skills/y2k-pixel-doodle/`. Start a new session or use `/skills reload`. This does not establish compatibility with another product called QCoder or with every QoderWork variant. |
| MiniMax Code CLI/workspace | The official open-source client supports project `.agents/skills`, `.claude/skills`, and `.minimax/skills`. For example, use `.minimax/skills/y2k-pixel-doodle/SKILL.md`; start a new workspace session and inspect `/skills`. This is not a verified desktop-app import path. |

The official sources for each row are linked in the Chinese sections above. Documentation was checked on **2026-11-10**; installation notes are not end-to-end test results. See [compatibility.md](compatibility.md).

### Use and update

Attach your source photo and say:

> Use y2k-pixel-doodle to turn the attachment into a white-background, hand-drawn pixel doodle. Keep its composition and expression. If reference-image generation is unavailable, return a complete prompt and state that no image was generated.

For prompt-only work, explicitly request a prompt without generation. Label source and style references separately. Update the existing installed copy using the host's supported mechanism, then start a new task. Updating GitHub does not update all installed copies or publish the skill to agent marketplaces automatically.
