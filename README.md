*[Русская версия](README.ru.md)*

# skills-from-expertise

A skill that turns someone else's expertise into a working method: the agent follows it, and
you get a specialist where there was no way to hire one.

## Why this exists

A project needs a marketer. Or a lawyer, an editor, an instructional designer: someone who
knows the subject and can make decisions inside it, and there is no budget to hire them.
The expertise itself, meanwhile, is out in the open: talks, breakdowns, courses, interviews.
The obvious move is to turn that into a skill and work from it.

What happens next is almost always the same. The model produces a tidy summary, accurate and
well organised, that you cannot actually work from. Everywhere the expert was choosing between
options and knew exactly why, the file says "it depends".

The knowledge came across and the decisions did not, when the decisions were the whole point.

## What the skill does

It finds the points in the material where the expert makes a choice, and reconstructs the sign
they chose by. Out of that comes a procedure: what to do, in what order, by what criterion,
and where the method stops working.

A finished skill is easy to test. A methodology demands something, so it can be broken: done
out of order, chosen wrongly, applied past its condition. A summary cannot be broken, because
it demands nothing and only describes how things happen to be.

**If it is impossible to get something wrong by following the file, the file obliges nothing.**

## How this differs from the official specification

The Agent Skills specification answers **how to shape the file**: fields, structure, limits,
progressive disclosure. All of it is necessary, and none of it is repeated here.

That leaves the second question, **what to put inside**, because a file that is flawless
in form will load happily and change nothing you do. This skill is about the contents.

## What is in the file

| Block | What it settles |
|---|---|
| **Extracting the method** | How to find the choice points in a talk or a book and reconstruct the criteria the expert decides by |
| **Working with a live expert** | Which questions draw out the procedure and which do not: asked directly how they decide, an expert usually describes not what they do but how it is conventionally explained |
| **Losses during extraction** | The most valuable part is said in passing and disappears first, which is why the digest comes before assembly and the cross-check after |
| **Limits on filling gaps** | A prohibition that was not in the source takes a working option away from the reader, and an invented figure reads as a verified fact although nobody measured it |
| **Legal framing** | Method is not protected, expression is: what may be taken, when a quote is needed, which license to apply |
| **Checks before delivery** | Eight ways to test a finished file, and separately why all of them judge the text rather than whether the method works |

Plus three reference files that load when needed: types of source, legal particulars, and how
to organise a set once there are many skills.

## Installation

The repository holds two language versions of the same skill. Install one of them, either
`skills-from-expertise` or `skills-from-expertise-ru`.

**The easiest way is to ask your agent.** Open your project in Claude Code, Codex, or Cursor
and say something like this:

```
Install the skill from here: https://github.com/PolarSnowflake/skills-from-expertise
I need the English version, the folder skills/skills-from-expertise.
Put it in this project's skills folder.
```

The agent will download and place it. No archives and no terminal required.

**Through the CLI, if you have it.** English version:

```
npx skills add PolarSnowflake/skills-from-expertise --skill skills-from-expertise
```

Russian:

```
npx skills add PolarSnowflake/skills-from-expertise --skill skills-from-expertise-ru
```

The command detects which agents you have installed and asks where to put it. To name one
explicitly, add `-a claude-code` at the end.

**By hand.** Press the green **Code** button at the top of the repository page, choose
**Download ZIP**, unpack it, and copy the folder you want out of `skills/` into wherever your
agent keeps skills: `.claude/skills/` for Claude Code, `.codex/skills/` for Codex CLI, or
`.agents/skills/`, the shared location most agents read.

Once installed, the skill loads by itself when the conversation turns to creating or rewriting
a skill. If that doesn't happen, ask for it directly: "work by skills-from-expertise".

## When you have many skills

It helps to separate skills by topic, so that while assembling a new one the model does not see
neighbours from an unrelated area. That prevents references between skills that should never
have appeared: while the whole set sits on your disk such a reference goes unnoticed, and
the moment you hand someone a single skill it points at nothing.

There are two ways to separate them.

**A separate project per topic** is the most reliable: the agent sees exactly the skills that
live in that project.

**A subfolder with its own skills folder**, if everything has to live in one place:

```
project/
├── .claude/skills/          shared across the project
├── marketing/
│   └── .claude/skills/      visible when working with files in this folder
└── development/
    └── .claude/skills/
```

One subtlety here: nested skills are not picked up at startup but at the moment the agent first
opens a file inside that folder, and they stay available for the rest of the session.

Categories **inside** the skills folder itself do not work: `.claude/skills/marketing/name/`
will not be found, because only one level of nesting is scanned.

## Getting started

The skill carries its assembly rules itself, but one thing is worth adding at the start
of a session: what you consider a finished result and what conditions you work under, since
whatever sits in the standing context fires more reliably than what gets pulled in along
the way.

Paste this as your first message, filling in the brackets:

```
Role: you build skills from sources — you turn someone else's expertise into a methodology
that can be used to make decisions, not into a restatement of content. Work by the
skills-from-expertise skill.

What we do in this chat: I give you a source — a video, a transcript, an article, a table,
screenshots of a board. You return a finished skill.

The result of every build is three things, and a skill without the first and the third
does not count as done:

1. A digest of the source — as a separate .md file, before assembly of the skill begins.
   In chat: a link to the file and only two sections, "said in passing" and "what was left
   out." Do not paste the full retelling into chat, I will read the file. Wait for my
   reaction before assembling.
2. The skill file.
3. A report: what was extracted, where you had to fill gaps, what was deliberately left out
   and why, what remained uncovered, what I decide. As the last line of the report — exactly
   this format, with numbers filled in, not described in words:
   Format: description N/1024 · name N/64 · license: <value or "no field">

How to work with me:
- Ask questions in one batch and number them so I can answer in a single message.
- Don't ask permission to continue. The only planned stop is after the digest.
- Show edits to existing files before making them. Deletions — verbatim.
- Don't retell the source to me instead of working.

Standing conditions:
- Purpose of the result: [publication for the community / private use / commercial
  distribution].
- Domain: [what the skills in this project are about].
- Files: skills in .claude/skills/<name>/, digests in [folder].
```

Only **purpose** has to be filled in: both the license and how thoroughly traces of someone
else's source get cleaned depend on it.

## How it develops

The skill was built from practice and exercised on real builds across several different
domains, from ones where everything rests on judgement to ones where the task has a right
answer. Every rule appeared after something went wrong on a live build, and the next ones
will appear the same way.

Your area may be built differently, and that is the interesting part: **tell us where
the method failed on your material**. Those cases are what turn into new rules, and you can
report them under Issues, and there is more in [CONTRIBUTING.md](CONTRIBUTING.md).

## About the languages

The original is written in Russian and the English version is a translation of it. Both live
in this repository and install separately, so take whichever language you find it easier
to argue with the model in.

The model is the one reading the file, but a rule that doesn't suit you is something you will
notice, and then it is worth either changing it locally or sending it here so it changes
for everyone.

## Sending a fix

You don't need git: problems can be reported under the **Issues** tab of this repository,
and if you want to fix something yourself, fork it and open a pull request. Both paths are
described step by step in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT, see [LICENSE](LICENSE). Take it, change it, bundle it into your own sets, commercial
ones included. The only condition is keeping the attribution notice.
