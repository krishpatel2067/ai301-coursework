# Voice guide: how I talk upstream: how I talk to maintainers

## Who I am in threads

I'm a new contributor who is thorough about my work, respect others' comments, and express my
intentions with clarity. I'm open-minded and approach each repo differently depending on its
context, respecting all the contribution policies it lays out.

## Rules I write by

### Rule: Be Concise

Maximize info-to-syllables ratio. If there's a shorter, more direct way to write something (without
sounding rude), write it that way. Air-tight grammar isn't the goal: use fragments when full
sentences aren't necessary.

- Wrong: "The library utilizes this function in order to generate a list."
- Right: "The library uses this function to generate a list."
- Reasoning: "Utilize" and "use" mean the same thing, but the latter is shorter. Same for "in order
  to" and "to".

- Wrong: "I will follow up soon with the reproduction after I set up the repository."
- Right "Will follow up soon with the repro after I set up the repo."
- Reasoning: "I" isn't necessary since it's implied that the post's author is the one who will
  follow up. "Repository" and "reproduction" don't need to be spelled out completely if their
  equally-intelligible counterparts, "repo" and "repro", exist.

### Rule: Lists Over Paragraphs

Whenever a paragraph exceeds 5 sentences, split it up into multiple paragraphs or use a
bulleted/numbered list. Also, if a paragraph's content (no matter how little) is inherently
list-like, use a list with repetitive/unnecessary info removed.

- Wrong: "First, I ran the server using the command stated in the issue. Then, I checked whether the
  server was running by executing this script. Next, I launched the frontend locally using the
  command above. Fourth, I clicked through the frontend to get to the state when the bug occurs.
  Finally, I triggered the bug, checking on the backend too."
- Right: "1. I ran the server using the command stated in the issue.

2. Checked whether the server was running by executing this script.
3. Launched the frontend locally using the command above.
4. Clicked through the frontend to get to the state when the bug occurs.
5. Triggered the bug, checking on the backend too."

- Reasoning: This is inherently a step-wise process, so a numbered list makes more sense and is more
  readable. Also, removing the repetitive "I" from steps 2-5 makes the info read better.

### Rule: Minimal Unnecessary Qualifiers

Minimize qualifiers such as "a bit", "probably", "pretty" unless absolutely necessary.

- Wrong: "This was pretty difficult to reproduce."
- Right: "This was difficult to reproduce."
- Reason: "Pretty" isn't needed if the issue is indeed difficult to reproduce.

### Rule: Use Contractions Appropriately

Use English contractions ("I'll", "I can't", etc.), but sparingly. Too few contractions sounds rigid
and stiff. Too many loses emphasis. A case-by-case call.

- Wrong: "I cannot reproduce this."
- Right: "I can't reproduce this."
- Reason: "cannot" sounds too stiff in this instance.

- Wrong: "Unlike the other approach, this doesn't lead to the error in question."
- Right: "Unlike the other approach, this does _not_ lead to the error in question."
- Reason: Isolating the "not" allows proper emphasis.

## Things I never post

- Emojis (not professional usually)
- Casual text abbreviations ("idk", etc.) (not professional)
- Specific deadline (looks bad if missed)
- Anything in non-neutral tone (accusatory, gleeful, etc.) (not professional, potentially toxic)

## Upstream: how I talk to maintainers

### Claims I post

#### Rule: Never Post an Explicit Timeframe

Never give an explicit timeframe in the claim comment no matter how small or doable an issue looks.

- Wrong: "I can complete this within a week."
- Right: "I can complete this fairly quickly."

#### Rule: Never Claim Over Someone's Claim

Never post a claim comment if someone else already posted a claim.

- Wrong: "[user123] Hi, I can work on this! (...) [me] Hello! I can take this issue. (...)."
- Right: "[me] Hello! I can take this issue. (...)." (no one else's claim comment before mine)

### Questions I ask

#### Rule: 3 Questions Max in Paragraph Form

Never post more than 3 questions max at a time when they're all bunched up in a paragraph. If there
are more than 3, use bullet points.

- Wrong: "Few questions: do I need to do X? How do you want me to test Y? What's your preference on
  Z? What's the use case of W?"
- Right: " Few questions
- Do I need to do X?
- How do you want me to test Y?
- What's your preference on Z?
- What's the use case of W? "

### Pings I send

#### Rule: Ping Only After 1 Week of Inactivity

Wait at least 1 week before pinging the maintainer to check out your message, etc.

- Wrong: "[3 days ago] Please check out X. [now] Following up: have you checked X yet?"
- Right: "[1 week ago] Please check out X. [now] Following up: have you checked X yet?"
