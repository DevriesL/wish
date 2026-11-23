# wish

[中文](README.zh-CN.md)

A skill for wish-driven programming in Codex and Antigravity: describe what you want made, answer a few questions about your real world, and the agent builds it on its own until you can use it.

## Install

**Codex**: in Codex, type:

```
$skill-installer https://github.com/DevriesL/wish/tree/main/skills/wish
```

Or run in a terminal:

```sh
npx skills add DevriesL/wish -g -a codex
```

**Antigravity**: run in a terminal:

```sh
npx skills add DevriesL/wish -g -a antigravity
```

## Use

Open Codex or Antigravity in a new folder and make a wish. To rework an existing project, make the wish in that project's folder:

```
$wish I want a ...    (Codex)
/wish I want a ...    (Antigravity)
```

Answer the questions and confirm what it writes down. It then builds without stopping and tells you where to open the result when it's done. To add a wish later, make another wish in the same folder or just tell the agent.

## Report a problem

Tell your coding agent what went wrong and ask it to report it to wish. The agent files the issue itself.

### For agents

File one issue per problem at https://github.com/DevriesL/wish/issues, e.g. with `gh issue create --repo DevriesL/wish`. Show the user the full draft and post only after they approve it. Remove personal details, accounts, secrets and file paths.

Title: `[<rule>] <what went wrong>`, where `<rule>` is the SKILL.md section or AGENTS.md rule involved, e.g. `[Recording] wrote a one-off request into Constraints`.

Body:

1. **Wish**: the line that invoked wish (`$wish …` or `/wish …`), and whether it was a new folder, an existing project, or a later wish.
2. **What the user experienced**: in the user's words, quoted, and what they expected instead.
3. **Which rule**: the rule involved, and which case it is: not followed; followed but wrong or unclear; or no rule covers it.
4. **Evidence**: the conversation excerpts where it went wrong; AGENTS.md as it is now, plus `git log -p AGENTS.md` if its history matters; whether a context compaction happened before the problem.
5. **Environment**: the agent CLI and its version, the model, and `git hash-object` of the installed wish `SKILL.md`.
6. **Suggested fix** (optional): the smallest wording change to `SKILL.md` or the AGENTS.md template that would have prevented it. Keep to wish's principles: no engineering mechanisms, as few words as possible.
