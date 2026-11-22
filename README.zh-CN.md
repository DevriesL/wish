# wish

[English](README.md)

用来做许愿式编程的 Codex skill：说出你想要的东西，回答几个关于你现实情况的问题，Codex 就会自己一直做下去，直到你能直接用上。

## 安装

在 Codex 里输入：

```
$skill-installer https://github.com/DevriesL/wish/tree/main/skills/wish
```

或者在终端运行：

```sh
npx skills add DevriesL/wish -g -a codex
```

## 使用

在一个新建的文件夹里打开 Codex，许个愿。想改造已有的项目，就在那个项目的文件夹里许愿：

```
$wish 我想做一个……
```

回答它的问题，确认它记下的内容。之后它会一直做下去，做完告诉你从哪里打开。以后想加新的愿望，在同一个文件夹里再用一次 `$wish`，或者直接告诉 Codex 就行。
