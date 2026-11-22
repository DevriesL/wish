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

## 反馈问题

告诉你的 coding agent 哪里不对，让它把问题报给 wish，它会自己去提 issue。

### 给 agent 的说明

一个问题提一个 issue，提到 https://github.com/DevriesL/wish/issues ，比如用 `gh issue create --repo DevriesL/wish`。先把完整草稿给用户看，用户同意后再发。删掉个人信息、账号、密钥和文件路径。

标题：`[<规则>] <哪里不对>`。`<规则>` 是出问题的 SKILL.md 小节或 AGENTS.md 规则，比如 `[Recording] 把一次性的要求记进了 Constraints`。

正文：

1. **许的愿**：那句 `$wish …`，以及是新文件夹、已有项目，还是后来追加的愿望。
2. **用户遇到了什么**：引用用户的原话，以及用户本来期望怎样。
3. **哪条规则**：涉及哪条规则，属于哪种情况：没被遵守；遵守了但规则本身错了或不清楚；没有规则覆盖。
4. **证据**：出问题的那几段对话；现在的 AGENTS.md，如果它的修改历史有关，附上 `git log -p AGENTS.md`；出问题之前有没有发生过上下文压缩。
5. **环境**：agent 的 CLI 和版本、模型，以及已安装的 wish `SKILL.md` 的 `git hash-object`。
6. **建议的修改**（可选）：能避免这个问题的、对 `SKILL.md` 或 AGENTS.md 模板最小的措辞改动。守住 wish 的原则：不加工程化机制，字越少越好。
