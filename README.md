# wish

[中文](README.zh-CN.md)

A Codex skill for wish-driven programming: describe what you want made, answer a few questions about your real world, and Codex builds it on its own until you can use it.

## Install

In Codex, type:

```
$skill-installer https://github.com/DevriesL/wish/tree/main/skills/wish
```

Or run in a terminal:

```sh
npx skills add DevriesL/wish -g -a codex
```

## Use

Open Codex in a new folder and make a wish. To rework an existing project, make the wish in that project's folder:

```
$wish I want a ...
```

Answer the questions and confirm what Codex writes down. It then builds without stopping and tells you where to open the result when it's done. To add a wish later, use `$wish` again in the same folder or just tell Codex.
