# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

Order matters because gaining context is necessary before reading the thing you grade.

1. Issue - note the title, trigger conditions, files/systems involved, environment details, and scope/scale.
2. Contribution policy - note if any AI use disclosure is required (assume none by default).
3. Repro evidence - note the files/systems involved, input, output, environment details, and conditions needed to reproduce.
4. Thread highlights - note any updates or leads in chronological order.
5. Candidate plan - note all its content.
6. Candidate PR - title, description, diff, and all other content within.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

In _eval_ mode:

- Issue - the original post in the package under the header "## Issue".
- Contribution policy - under "## Repo Facts" > "contribution policy" bullet point; especially search for "AI policy".
- Repro evidence - under the header "## Repro evidence".
- Thread highlights - all bullet points under the header "Thread highlights ({n} comments total)" (where n is a number).
- Candidate plan - under the header "Candidate plan".
- PR - under the header "Candidate PR".

In _live_ mode:

- Issue - link provided by the student.
- Contribution policy - repo files `CONTRIBUTING.md` and `AI_POLICY.md` (sometimes at root, often under `docs/`).
- PR - in `plan.md`, `pr_draft.md`, or whatever file the student points you to.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Follow the read order, gathering evidence as outlined above.
2. Consider each check in the order that its written in the rubric.
3. Grade a check 'P' if all the passing conditions are met. If one passing condition is clearly violated, grade as 'F'. If evidence listed is genuinely missing in the package, grade '?'.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

- Two choices: `accept` or `reject`.
- Follow the verdict rule in the rubric to reach the verdict.
- '?' for a check counts as `unclear`. Use the verdict rule to see how to deal with `unclear`. If the verdict rule doesn't mention it, fall back on `SKILL.md`.
