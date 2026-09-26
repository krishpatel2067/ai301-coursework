# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

Find it in the repro comment often near the beginning.

Must contain OS, environment, and other relevant tool info (e.g. `npm` version for a `Node.js` project).

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

Find it in the repro comment often in a numbered list.

Must guide a stranger to the starting state (if different from default), then to the bug state.

For example:

If the bug requires a server to be up and running, the steps first lead a stranger to running that server (or at least mention that a server must be running), then the steps to repro the bug are described, action-by-action to take.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

Find it in the input/output excerpts, logs, or screenshots in the repro comment.

The repro's tested behavior must match the issue's tested behavior (correct version numbers, same steps to reproduce, same output).

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

Find any cannot-reproduce remarks in the claim comment.

Any claim comment that claims to have reproed the issue must have proper evidence in a repro comment, following the other sections in this guide.

An honest cannot-reproduce (optionally with the steps tried in a repro comment) is better than a claimed repro that claims more than its evidence shows.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

Evaluate by looking at the claim and repro comments.

Repro/claim structure matches the repo-provided template, if any. AI use is disclosed if the repo contribution policy requires it. Repro steps are specific and honest, using much of the terminology and technology from the issue rather than vague boilerplate like "I couldn't repro on my machine".
