---
name: wish
description: "After any context compaction (earlier conversation replaced by a summary) in a folder whose AGENTS.md begins with the HTML comment `wish` or `wish: draft`, use this skill to re-read that AGENTS.md from disk; it replaces any earlier copy in your context. Otherwise use it only when the user invokes $wish: it interviews them about their real world, writes AGENTS.md, then builds until every goal can be experienced."
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

## Which kind of wish

Look at what is in this folder:

- AGENTS.md starts with `<!-- wish -->`: an earlier wish. Interview only about the new wish, update Goals and Constraints under its Recording rule, then build. No setup, no draft.
- AGENTS.md starts with `<!-- wish: draft -->`: an unfinished interview. Continue it from the draft.
- There is code: an existing project to convert. Set up, write the draft, then convert.
- Otherwise (empty, or only things the user brought for this wish, such as data, photos or models): a new wish. Set up, write the draft, then interview.

## Set up the folder

Do this without asking and without technical words:

1. If this is the user's home, desktop or downloads folder, or it holds personal files unrelated to the wish, stop. Tell the user, in plain words, to make the wish in a new folder of its own.
2. If this folder isn't the root of its own git repository, make it one. Commit what is already there before you change anything. Never add a remote or push unless the user asks.
3. If you find passwords, keys or tokens in code or in files git would commit, move them into one local file that git ignores. If any have already left this computer (pushed or published), tell the user, in one real-world sentence, which one to change.

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
| App | who uses it, and where | "用 Rust 写" is a preference: ask why. |
| Embedded device | the board in hand, its sensors, where it is installed | "用 ESP32": if that board is what the user has, it is a fact; record it. |
| Scientific computing, simulation | the measured object, the data, the judgment the results support | "精度要高": ask what the results decide, e.g. "误差小于测量误差". |
| 3D modeling | what the made thing is for | "要能打印": the printer model and print size are facts; ask for them. |
| Game | who plays, on what device, how long a session lasts | "要好玩" is a fine goal; goals don't need a clear line. |
| Web slides | the audience, the venue, the length of the talk | "像苹果发布会那样": ask which part is meant; record only that experience. |
| Backend | who or what calls it, and how much | "要高可用": ask what happens in the real world when it is down. |
