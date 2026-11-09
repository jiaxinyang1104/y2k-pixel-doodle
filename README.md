# Y2K Pixel Doodle

English | [简体中文](README.zh-CN.md)

Turn a photo into a white-background, hand-drawn pixel doodle inspired by early desktop painting programs. The skill preserves the subject's recognizable pose and expression while using uneven mouse-drawn lines, loose color fills, and tiny colorful marks.

It works with portraits, pets, objects, architecture, and landscapes. You can ask for a finished illustration or a reusable image-generation prompt.

## Examples

Each comparison is a single image: original on the left, generated illustration on the right.

### Pet

![Pet: original photo on the left and generated pixel illustration on the right](examples/cat-comparison.png)

### Architecture

![Architecture: original photograph on the left and generated pixel illustration on the right](examples/courtyard-comparison.png)

## What the skill does

- **Uses one pixel-pencil style throughout.** Facial features, outlines, scenery, and small decorations share a coarse pixel grid, line weight, and irregularity.
- **Keeps the expression readable.** Eye direction, eyelid shape, eyebrows, and mouth position guide the redraw. The subject's pose, key features, and spatial relationships remain recognizable.
- **Adds handmade imperfections.** Uneven outlines, a few missed pixels, loose strokes, and slightly misaligned color fills give the image its doodle quality.
- **Adapts the background.** For a person, pet, or object, a few bent structural lines suggest the setting while keeping attention on the subject. For a landscape, the important shapes and depth guide the drawing.
- **Adds tiny accents.** A few irregular colored hearts, stars, loops, or other marks sit in the white space by default.
- **Follows the source frame.** The skill aims to retain the input's composition, aspect ratio, and pixel dimensions. Exact generation and export options depend on the available tools.

Explicit instructions override these defaults. For example, you can request a plain white background without decorations or specify a different aspect ratio.

## Requirements

To create an illustration directly, use an AI environment that can inspect an input image and access an image-generation or image-editing tool. The skill is a set of instructions; it does not include an image model.

The assistant can also write a prompt based on the input image. Exact dimensions and final file export depend on the host environment and its available tools.

## Install in Codex

Give this repository URL to Codex and ask:

> Install this GitHub repository as a skill.

Alternatively, clone it into your personal skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/jiaxinyang1104/y2k-pixel-doodle.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/y2k-pixel-doodle"
```

If the destination already exists, `git clone` will stop rather than overwrite it. Check the existing skill before updating it.

## Usage

Start a new Codex conversation, attach an image, and invoke the skill by name.

**Generate an illustration**

> Use `$y2k-pixel-doodle` to turn this photo into a white-background pixel doodle. Keep the pose and expression.

**Use a style reference**

> Use `$y2k-pixel-doodle` to redraw image 1. Use image 2 as a reference for the pixel lines and colors.

**Write a prompt only**

> Use `$y2k-pixel-doodle` to write an image-generation prompt for this photo.

**Adjust the defaults**

> Use a plain white background, omit the small stickers, and keep the original landscape ratio.

## Repository layout

```text
y2k-pixel-doodle/
├── SKILL.md
├── agents/
│   └── openai.yaml
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

- `SKILL.md` contains the trigger description, visual rules, and workflow.
- `agents/openai.yaml` provides the display name, summary, and example invocation for Codex.
- `examples/` contains source images, generated illustrations and side-by-side comparisons for the README. They are not required inputs for the skill.

## License

The skill instructions and accompanying configuration are available under the [MIT License](LICENSE). Example images and their source materials may have separate rights; the publisher should confirm their permitted use before redistribution.
