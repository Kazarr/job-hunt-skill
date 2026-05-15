# Cover letters

A cover letter has one job: convince a reader who's already mildly interested in the CV to move the application forward. It is *not* a personal essay, a restatement of the CV, or a humblebrag. Most cover letters fail because they try to do too much; the good ones do one thing well.

## When to write one

- Posting explicitly asks for it → write one.
- Application form has a free-text "why do you want this role" field → write one (often shorter).
- No mention of a cover letter and the form has no field for it → usually skip; if the user wants one anyway, write a tight one (~250 words) and attach.
- Cold outreach / referral → write a different kind of artifact: a short personalized note, not a formal cover letter. Mention the connection in the first line.

Ask the user if it's unclear. Don't auto-produce one for every application.

## Output

Write to `applications/<slug>/cover-letter.md`. Plain text / markdown. Match the posting's language (see SKILL.md universal rules).

## Length

Three short paragraphs. ~250–350 words total. Anything longer is read diagonally at best.

## Structure that works

```
Para 1: Why this role at this company specifically — show you read the posting and know what they do.
Para 2: The strongest piece of evidence from the user's background that maps to what they need. One concrete story or accomplishment, with detail.
Para 3: What the user is looking for, brief logistics if relevant (location, availability), one-line close.
```

### Paragraph 1 — Specific opening

Open with one sentence that proves the letter is not boilerplate. The cheapest way: reference something specific the company does, has shipped, or wrote about, and connect it to what the role would have the user working on.

**Generic (kill it):** *"I am writing to apply for the Senior Backend Engineer position at Stripe, a company I have long admired."*

**Specific (keep it):** *"Stripe's Atlas team's writeup on their move to gRPC-streaming for the dashboard caught my eye last month — that kind of architectural rework against a live revenue surface is the work I've been doing for the past three years at `<prev co>`."*

If we don't actually know something specific about the company, do `references/company-research.md` first. Faking knowledge here is worse than being generic.

If a referral exists, name them in the first line: *"Jana Novák, who manages the platform team, suggested I apply for the Senior Backend Engineer role."*

If the posting has a canary phrase or attention-check requirement (see `references/analyze-posting.md` step 3), incorporate it naturally — don't bolt it on awkwardly. A canary handled well signals the user actually read the posting.

### Paragraph 2 — The proof

Pick **one** achievement from `profile.md` that maps directly to the role's main need (per the fit analysis). Tell it with enough detail that a reader believes it: what the situation was, what the user did, what the outcome was. Numbers make it land.

Don't list three achievements. One, told well. The CV does the breadth job; the cover letter does the depth job.

**Pattern:**
> When I joined `<prev co>` the `<thing>` was `<problem state>`. Over `<time>`, I `<what I did>` by `<how>`, which moved `<metric>` from `<before>` to `<after>`. That experience maps almost directly to the `<responsibility from posting>` in this role.

The last sentence closes the loop for the reader. They don't have to draw the connection themselves.

### Paragraph 3 — The close

Three things, briefly:
- What the user is looking for in their next role (one sentence, framed positively — not "I want to leave my current job because…")
- Any logistics that matter for this specific application (location, work auth, notice period — only if non-default)
- A short, normal closing sentence. Not "I look forward to hearing from you at your earliest convenience" — that's filler. Try "Happy to dig into any of this in a call." or just sign off.

## Voice

Match the user's voice from their `profile.md` prose. If they write plain and direct, the letter is plain and direct. If their natural register is more formal, lean a bit more formal — but never into stiffness.

Cut on every pass:
- "I am writing to express my interest in..." — assumed
- "I believe I would be a strong fit because..." — show, don't tell
- "Results-oriented", "passionate", "team player", "go-getter" — empty calories
- "Please find attached my resume" — they have it
- "Thank you for considering my application" — generic close

## Tone for different audiences

- **Early-stage startup**: more direct, less formal, willingness to talk about ambiguity/scrappiness, mention any startup experience explicitly.
- **Big tech**: still direct but lean on scale numbers and process maturity (RFCs, on-call, mentoring).
- **Public sector / regulated industry**: more conservative tone, emphasize reliability and care.
- **EU / non-English audiences**: still plain, but verify local norms (date in header, formal salutation, "Mit freundlichen Grüßen"-style sign-off where appropriate).

## After writing

Read it through once impersonating a tired hiring manager who has 30 other letters in the queue. If you'd skim past it, rewrite paragraph 1. The opener earns the rest of the read.

Share with the user. Common rewrite directions:
- "Too formal" → strip one round of softening words, contract verbs ("I have" → "I've").
- "Sounds generic" → paragraph 1 isn't specific enough; do more company research.
- "Too long" → cut paragraph 2's setup, keep the action and outcome.
- "Doesn't sound like me" → re-read `profile.md`'s summary prose, match its register.
