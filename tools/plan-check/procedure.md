# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

Order matters because gaining context is necessary before reading the thing you grade.

1. Issue - note the title, trigger conditions, files/systems involved, environment details, and scope/scale.
2. Contribution policy - note if any AI use disclosure is required (assume none by default).
3. Repro evidence - note the files/systems involved, input, output, environment details, and conditions needed to reproduce.
4. Thread highlights - note any updates or leads in chronological order.
5. Candidate plan - note all its content.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

For _eval_ mode:

- Issue - the original post in the package under the header "## Issue".
- Contribution policy - under "## Repo Facts" > "contribution policy" bullet point; especially search for "AI policy".
- Repro evidence - under the header "## Repro evidence".
- Thread highlights - all bullet points under the header "Thread highlights ({n} comments total)" (where n is a number).
- Candidate plan - under the header "Candidate plan".

Note: the locations may be slightly different in _live_ mode (at a real GitHub issue link).

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Follow the read order above for the first read, gathering evidence as outlined above.
2. Consider each check in the order that its written in the rubric.
3. Grade a check 'P' if all the passing conditions are met. If one passing condition is clearly violated, grade as 'F'. If evidence listed is genuinely missing in the package, grade '?'.
4. If there is more than one '?' grade, execute steps 1-3 again. If there is more than one '?' grade again, finish grading.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

- Two choices: accept or reject.
- Follow the verdict rule in the rubric to reach the verdict.
- Treat '?' as not passes (aka fails).
