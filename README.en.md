# pic-ppt

[简体中文](README.md)

**Rebuild a slide screenshot or design mockup as a PowerPoint slide with editable text.** `pic-ppt` is a Codex skill for when you have a flattened slide image and still need to revise its wording or replace individual visuals in PowerPoint. By default, one input image produces a one-slide `.pptx` and a rendered preview.

## How it works

1. Identify the slide area and rebuild a clean, text-free background at the original aspect ratio.
2. Redraw borders, illustrations, and icons individually. Use PNGs with alpha transparency where the artwork needs a transparent background.
3. Rebuild titles, body text, captions, and legible labels as native PowerPoint text boxes, preserving the wording, hierarchy, and colors.
4. Assemble the slide in the original positions and stacking order, then compare the rendered preview with the source for text, edges, and layout.

You can edit the text directly and move, resize, or replace the background, frames, and other visuals individually. The internal lines, shapes, and details of those images remain raster pixels. Concealed portions of the background are reconstructed from the surrounding image.

## Install and use

1. Download and extract `pic-ppt.zip` from [GitHub Releases](https://github.com/HuiiiiiiFly/pic-ppt/releases/latest), or copy the [`pic-ppt/`](pic-ppt/) directory from this repository.
2. Put the entire `pic-ppt` folder in your user-level `~/.agents/skills/` directory or your project’s `.agents/skills/` directory. For a user-level installation, the resulting path should be `~/.agents/skills/pic-ppt/SKILL.md`. On Windows, `~` is your user directory.
3. Upload your screenshot in a Codex environment with reference-image editing and PowerPoint generation and rendering tools. Invoke `$pic-ppt`. In ChatGPT Work, use `@` to select the installed skill.

```text
Use $pic-ppt to rebuild my uploaded slide screenshot. Preserve the original aspect ratio, content, and colors. Use native text boxes and keep the frames and icons individually replaceable. Deliver a PPTX and a rendered preview.
```

The skill contains Markdown instructions and tool metadata. It uses the image and presentation tools provided by the host environment. The full workflow requires reference-guided image editing, transparent image output, PPTX generation, and slide rendering. See the [official Codex Skills documentation](https://learn.chatgpt.com/docs/build-skills).

## Skill files

- [`SKILL.md`](pic-ppt/SKILL.md) defines the reconstruction workflow.
- [`agents/openai.yaml`](pic-ppt/agents/openai.yaml) supplies display metadata and an example invocation.
- [`references/asset-prompts.md`](pic-ppt/references/asset-prompts.md) supplies image prompts for backgrounds, frames, and icons.
- [`references/layout-and-checks.md`](pic-ppt/references/layout-and-checks.md) describes placement, layout, and output checks.
