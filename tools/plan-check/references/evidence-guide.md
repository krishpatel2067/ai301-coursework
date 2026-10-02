# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

Each context is listed from most important to least important.

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

In the plan: find it under a "Diagonsis" or "Root Cause" header.
Context: repro evidence, thread highlights, issue.

A plan whose diagnosis involves the same file, area, pipeline, or system follows the context. A plan which picks a completely different area contradicts the rest of the thread.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

In the plan: find it under the "Scope" or "Files or Areas" or related header.

A plan who lists the files or areas explicitly sets clear boundaries that can be checked later. Bonus points for listing files or areas _not_ to touch. A plan that vaguely mentions a component (e.g. "the RAG") is ripe for scope creep.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

In the plan: find it as a numbered list of steps, typically under "Approach" or "Order of Work".

Steps read like an instruction manual - no large gaps between steps to open it up to chance or interpretation. If a hundred people were to follow the steps, they should all get the same result.

Grade on the content, never the structure. While the location suggests a numbered list of steps, a good plan _can_ still be clearly executable without it.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

In the plan: find it under the "Test" or "Test Plan" header.

The plan lists existing tests, proposes new automated tests, or describes a through manual test while truly testing the change proposed. Its proposed tests aren't flaky, irrelevant, or unclear (e.g. "run the function").

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

In the plan: look for caveats, risks, unknowns, or deviations.

A plan that sounds too good to be true probably is. Weed out plans that use too many absolutes or too much assertion. A plan that's honest about any shortcomings is more realistic.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

In the plan: consider its entire content.
Context: contribution policy, repro evidence, issue, thread highlights.

A plan that fits in with the repo conventions and current discussion gets positive attention. A plan that's straight boilerplate gets ignored. If the contribution policy requires disclosure for any AI use, the plan must do so (even if it mentions "I do not plan to use AI"). The plan must show that it acknowledges the thread context, for example, by following the right lead (if any provided earlier).
