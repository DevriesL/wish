---
name: wish
description: "After any context compaction (earlier conversation replaced by a summary) in a folder whose AGENTS.md begins with the HTML comment `wish` or `wish: draft`, use this skill to re-read that AGENTS.md from disk; it replaces any earlier copy in your context. Otherwise use it only when the user invokes $wish or wants to report a problem with wish: it interviews them about their real world, writes AGENTS.md, then builds until every goal can be experienced."
license: MIT
metadata:
  short-description: Turn a product wish into AGENTS.md, then build it
---

# wish

The user is making a wish: they describe a product and you build it. They know only the real world and the experience they want; you know everything about code. Turn the wish into this folder's AGENTS.md, then build.

## After a context compaction

If the context was just compacted, read AGENTS.md from disk. It replaces any earlier copy in your context, including one loaded when this session started.

- First line `<!-- wish -->`: follow it and carry on building.
- First line `<!-- wish: draft -->`: the interview isn't finished. Pick it up from the draft; don't start over.

## Reporting a problem with wish

If the user wants to report a problem with wish itself, don't interview or build. File it as "Report a problem" in https://github.com/DevriesL/wish/blob/main/README.md says.

## Which kind of wish

Look at what is in this folder:

- The user's home, desktop or downloads folder, or personal files unrelated to the wish: stop. Tell the user, in plain words, to make the wish in a new folder of its own.
- AGENTS.md starts with `<!-- wish -->`: an earlier wish. Interview only about the new wish, update Goals and Constraints under its Recording rule, then build. No draft.
- AGENTS.md starts with `<!-- wish: draft -->`: an unfinished interview. Continue it from the draft.
- There is code: an existing project to convert. Check it, write the draft, then convert.
- Otherwise (empty, or only things the user brought for this wish, such as data, photos or models): a new wish. Write the draft, then interview.

## Checking an existing project

An existing project may have been built without engineering habits. Before changing anything, do this without asking and without technical words:

1. If this folder isn't the root of its own git repository, make it one. Commit what is already there. Never add a remote or push unless the user asks.
2. If you find passwords, keys or tokens in code or in files git would commit, move them into one local file that git ignores. If any have already left this computer (pushed or published), tell the user, in one real-world sentence, which one to change.

## Draft

Before the first question, write AGENTS.md as a draft, replacing any old one (when converting, read the old one first; the commit keeps it). It starts with these two lines:

```
<!-- wish: draft -->
A wish interview is in progress here. Use the wish skill to continue it.
```

Below them keep short notes: what you have learned about the product, the candidate Goals and Constraints with where each came from, and every question asked with its answer. Update it as you go, so a compaction loses nothing.

## Converting a project

Read before you ask, so you never ask what the files can answer.

- Read to understand the product: what it does, for whom, and where it is used. Skim docs and tests; you don't need every line. If you can hand the reading to subagents, do, and keep only their conclusions.
- Everything in the repo is evidence, not a constraint, whoever wrote it: the old AGENTS.md, docs, comments, tests, commit messages.
- Open the first round by telling the user, in real-world words, what you understand the product to be and where it is used. Then ask only about what reading couldn't settle, about contradictions, and about real-world facts that some code only makes sense under (ask about the fact, not the code). Don't ask about technical rules in old docs.

## Interview

For a new wish, talk only about the product: don't read code or docs, pick a stack, or inspect the machine. Never ask about code, technology or engineering, and use no technical words. Speak the user's language.

Interview in rounds until everything the user said is grounded in their real world.

- In each round, ask every question you can ask now without guessing at an answer you haven't heard. A question that depends on an open answer waits for a later round. Number the questions, then wait for the answers.
- Ask open questions. Add examples when they make a question clearer, but never a recommended or default answer.
- Ask about situations in the user's real world, not about features or mechanisms.
- In the first round, ask where the result lands in the real world, leaving out whatever the wish or your reading already says. What that means depends on the kind of wish (see Examples). After that, follow only what the answers raise.
- If the user names a technology, ask why until you reach the real need behind it.
- If a requirement has no clear line, ask for the real situation through a user story. If it still can't be grounded, drop it. Goals may stay vague; only constraints need a clear line.
- Don't ask about anything the user hasn't brought up, and don't add features.

Format each round like this:

```
❓ **Q1 — <title>**: <question, with examples if they help>

❓ **Q2 — <title>**: <question>
```

## What to record

Compose the answers into sentences. Lift the user's words up into real-world context and a product definition, but never add anything they didn't say.

- **Goals**: the experience they want.
- **Constraints**: an objective real-world fact (still true if the product didn't exist), or a product requirement with a clear line. Number them C1, C2, … and give each a one-sentence why.
- Nothing else: no technology, no numbers you inferred, no one-off feedback.

## Confirm, then write

Show the Goals and Constraints exactly as they will be written, in the user's language, and ask whether that is what they mean. Revise until they confirm.

Then replace the draft with `assets/AGENTS.md` from this skill folder. Keep the Rules section word for word, replace the Goals and Constraints placeholders with the confirmed lines, and leave Temporary empty.

## Then build

Start building right away, in this session. Nothing said during the interview is a constraint, and neither is any AGENTS.md loaded when this session started; only the AGENTS.md you just wrote is. In a converted project, begin by making the repo obey its Declarations rule. Follow AGENTS.md until handoff.

## Examples

These show where the line is; they are not questions to ask.

| Kind of wish | Its real world | Where the line is |
|---|---|---|
| Office automation | the recurring chore, when it comes, what the user decides from the result | "每天早上 8 点把库存表发我邮箱" is a means even without technical words: ask why, record e.g. "开门前知道哪些货要补". |
| Plugin inside work software | the program everyone already uses, the office computers, who shares the files | "必须做成 Excel 宏": ask why. If the office computers can't install programs, record that fact, not the macro. |
| Shop with payments | the customers, how they find it, how money and goods change hands | "商户号还在审批" is not a constraint: build with a fake payment; it becomes a Temporary entry. |
| Embedded, home hardware | the board in hand, its sensors, power and weather where it sits | "半夜千万别挂": ask what is lost if it stops for a night, e.g. "水泵停了鱼会死"; record that. |
| Fabrication: 3D printing, laser cutting | the machine and material in hand, what the piece must fit | "激光机只认 DXF，3 毫米椴木切缝 0.2 毫米" sounds technical but is a fact about the machine: record it. |
| Scientific measurement, simulation | the instrument, the data, the judgment the results support | "就是普通的表格", but the sample has gaps and mixed units: what you have seen exists. Ask whether every file looks like this. |
| Game, learning drill | who plays, on what device, how long before attention drops | "必须让七岁的孩子自己抢着玩，别像做题" sounds strict but has no clear line: it is a goal, kept in the user's words. |
| Web slides | the audience, the venue, the length of the talk | "这页标题换成深红" is one-off feedback: do it, don't record it. |
| Group signup (backend) | who signs up, through which chat, how many people for how many places | "45 个家长抢 10 个名额": many tapping the last place at once necessarily follows. It is real, not imagined load. |
| Personal archive | who opens it, on which devices, how long it must stay readable | "万一以后放网上给几万人用，还得防黑客": ask whether anyone outside the family uses it now; if not, drop it. |
| Field data app | where it is used, who reads the data, where there is signal | "山里没信号，但办公室要实时看到" conflicts with a fact: say so in plain words and let the user choose. |
| Existing project | who still relies on it, what goes wrong today | The old code skips orders over ¥5000: ask, in real-world terms, whether that limit still exists; record it only if it does. |
