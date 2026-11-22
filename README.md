# pic-ppt

[English](README.en.md)

**把单张 PPT 截图或设计效果图重构为文字可编辑的 PowerPoint 幻灯片。** `pic-ppt` 是一个 Codex Skill，适合手上只有一张效果图、还需要在 PowerPoint 里改文字或替换配图的场景。默认一张图对应一页，交付 `.pptx` 和该页的渲染预览。

## 如何重构

1. 识别有效幻灯片区域，按原图比例复原无字底图。
2. 逐个重绘边框、插图和图标。需要透明背景的素材使用带 Alpha 通道的 PNG。
3. 用 PowerPoint 原生文本框还原标题、正文、图注和可辨识标签，保留原文、层级与配色。
4. 按原图位置与遮挡顺序合成，再对照预览检查文字、边缘与布局。

文字可直接修改。底图、边框和配图是独立图片对象，可单独移动、缩放或替换。图片内部的线条、形状和细节仍以像素保存。被前景挡住的背景由周围画面推断补全。

## 安装与使用

1. 从 [GitHub Releases](https://github.com/HuiiiiiiFly/pic-ppt/releases/latest) 下载 `pic-ppt.zip` 并解压。也可以直接复制仓库里的 [`pic-ppt/`](pic-ppt/) 目录。
2. 把整个 `pic-ppt` 目录放到个人 `~/.agents/skills/`，或放到项目根目录的 `.agents/skills/`。以个人安装为例，最终路径应为 `~/.agents/skills/pic-ppt/SKILL.md`。Windows 上的 `~` 对应你的用户目录。
3. 在具备参考图编辑和 PPTX 生成、渲染能力的 Codex 环境中上传截图，然后调用 `$pic-ppt`。在 ChatGPT Work 中，可以用 `@` 选择已安装的 Skill。

```text
请用 $pic-ppt 重构我上传的幻灯片截图。保留原尺寸比例、内容与配色，文字用原生文本框，边框和图标可单独替换。交付 PPTX 和渲染预览。
```

Skill 由 Markdown 指令和工具配置组成，运行时调用宿主环境的生图和演示文稿工具。完整流程需要能根据参考图重绘并输出透明背景素材，还需要能生成和渲染 PPTX。详见 [Codex Skills 官方文档](https://learn.chatgpt.com/docs/build-skills)。

## Skill 文件

- [`SKILL.md`](pic-ppt/SKILL.md) 描述完整重构流程。
- [`agents/openai.yaml`](pic-ppt/agents/openai.yaml) 提供 Skill 界面信息和调用示例。
- [`references/asset-prompts.md`](pic-ppt/references/asset-prompts.md) 提供底图、边框和图标的生图提示词模板。
- [`references/layout-and-checks.md`](pic-ppt/references/layout-and-checks.md) 记录定位、排版和验收方法。
