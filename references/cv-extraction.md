# CV extraction — building `profile.md` from a CV

A new user shows up with a job posting or a question. `profile.md` doesn't exist yet. This reference covers how to bridge that gap: get a CV from them, parse it into structured `profile.md` sections, and fill the things a CV doesn't contain with a short follow-up interview.

This runs once per user, when `profile.md` is missing or empty. It's not a per-application thing.

## Trigger

Invoke this reference when:
- `profile.md` doesn't exist or is empty, **AND**
- The user has asked for something that needs their context (fit analysis, cover letter, interview prep, recruiter comms drafting, rate negotiation, CV improvement)

If the user only asked for market-only analysis (red flags, posting authenticity, general rate market check), don't force a CV ask — handle the request and note that user-specific work would benefit from a profile when they're ready.

## Step 1: Ask for the CV

In the user's chat language, with no scripted exact phrasing — but covering these points:

- "I can help much better if I know your background."
- "Paste your CV here, or give me a file path. PDF, DOCX, MD, TXT all work."
- "If you'd rather skip, I'll still do what I can on this without your profile — market analysis, red-flag check, etc. — but anything that asks 'is this a fit for **me**' will be limited."
- (If the user explicitly says they have no CV) "We can also build the profile through a short interview. Want to do that instead?"

Wait for their reply before doing anything else.

## Step 2: Read and parse

If they pasted CV text → read it directly.
If they gave a file path → read the file. Claude can read PDF, DOCX, MD, TXT.
If the file path is non-readable (corrupted, image-only PDF, weird format) → tell them, ask for paste or a different format.

Parse into the structure of `templates/profile.md`. Don't be mechanical — extract intent, not just words. A CV bullet "Led migration from monolith to microservices" goes to the relevant role's `## What I actually did` section, but may also seed a `## STAR stories` entry if the user has more to say about it.

What to extract directly:
- **Identity**: name, location (city/country if known), languages spoken if listed
- **Contact and links**: email, phone, LinkedIn, GitHub, personal site — only if on the CV
- **Roles**: company, title, dates, location, every bullet, the tech stack used
- **Education**: degree, institution, dates, certifications
- **Skills inventory**: anything listed under skills, tools, technologies
- **Achievements**: any quantified wins (numbers, percentages, scale, $) — pull these into `## Achievements` as standalone entries even if they're already on a role
- **Open source / talks / publications**: if mentioned

What NOT to extract (or extract with skepticism):
- Mission-statement / objective sections — usually fluff
- "Soft skills" laundry lists — extract only if backed by evidence elsewhere
- Vague claims without specifics ("excellent communicator", "team player")

## Step 3: Identify the gaps

A CV does not contain (and rarely contains well):
- Target role direction and seniority anchor
- Compensation expectations and walk-away floor
- Contract type preference (employment vs B2B / contracting vs whatever the user's jurisdiction calls it)
- Hard constraints (location, remote/onsite, no-on-call, industry exclusions)
- Why the user is looking (clean, non-bitter version for talking points)
- "Why contractor not employee" type framings (if relevant)
- STAR stories (CVs have bullets, not narratives)
- Talking points / reusable answers to common interview questions
- Work authorization details specific to target markets
- Things the user wants to learn / grow into

After extraction, list the gaps explicitly:

```
I've pulled the following from your CV into profile.md:
- 3 roles (X, Y, Z) with full bullets
- Skills inventory
- 2 quantified achievements
- Education

The CV doesn't tell me a few things I'll need. Could you answer briefly?

1. What kind of role are you targeting next? (Title, level, kind of company / domain.)
2. What's your comp expectation, and is there a floor you'd walk away from?
3. Employment, B2B contracting, or doesn't matter?
4. Any hard constraints? (Location, remote/onsite, industry, schedule.)
5. Why are you looking right now? (Clean version — this becomes a talking point.)
6. Anything off-limits to mention to employers but useful for me to know?
```

Ask 4–6 questions at once, not one at a time. The user can answer in one message and we move on.

If the user has obvious gaps in the CV itself (huge time gaps, vague role descriptions, no quantification, missing summary), don't ask about them at this stage — note them and offer `references/cv-improvement.md` after the basic extraction is done.

## Step 4: Write `profile.md`

Use `templates/profile.md` as the scaffold. Fill it with what you have. Sections with no data get left as placeholder lines — they grow over time.

For roles, preserve more than the CV said. If the user mentioned offhand that they "owned the Kafka rewrite" in a follow-up answer, add it to the role's `## What I actually did` section even if it wasn't on the CV.

For the `## Summary — long form` section: synthesize a 3–5 paragraph version from the role bullets and the gap answers. This isn't the CV summary; this is the verbose version the agent reads as context.

For `## STAR stories`: seed 2–3 entries pointing at role bullets that look like good story candidates, but mark them `<needs filling>` — the user will populate the Situation / Task / Action / Result when they prep for an actual interview that calls for them. Don't fabricate the narrative.

For `## Talking points`: seed the structure (Tell me about yourself, Why looking, etc.) with first-draft answers based on what the user told you. Mark each with `<draft — refine before first interview>` so the user knows to look them over.

## Step 5: Confirm with the user

Don't just dump `profile.md` and walk away. Tell them in chat:

- "I've written `profile.md` with what I extracted. Quick rundown: `<3 bullets of what's there>`."
- "Three things I want you to double-check before we move on:
  - `<a specific extraction the user should verify>` — e.g. "I marked your role at X as Senior Backend Engineer; the CV said 'Engineer III' — confirm which you want as the canonical title?"
  - `<a gap I filled with a draft>` — e.g. "I drafted your 'why looking' talking point as `<text>`. Sound right?"
  - `<a place I noticed thinness>` — e.g. "Your CV lists 'cut latency significantly' without a number. Got the actual figure?"
- "Anything else I missed?"

The user's reply tunes `profile.md` once before we proceed. After that, edits happen incrementally as the user mentions new context.

## Step 6: Handoff

After confirmation, return to whatever the user originally asked for. Don't ask for permission to continue — just do the thing.

If the CV looked thin / weak / outdated (and the user might benefit from working on it), at the end of step 5 say something like:

> "Heads up: your CV is light on `<quantified results / summary / recent work>`. Want me to help you strengthen it (one-off, on your master CV — not per-application) before we go further, or come back to it later? Either is fine."

If they say yes, route to `references/cv-improvement.md`. If they say later, drop it.

## If the user declined to share a CV

Proceed in market-only mode:
- Recruiter behavior analysis — works without profile
- Posting red-flag analysis — works without profile
- Rate market reference — works against general data, but no walk-away comparison
- Fit analysis — limited; can extract requirements but can't measure fit
- Cover letter / interview prep — flag that these need profile context and ask the user for the minimum needed in-chat (one or two relevant past roles, one achievement) before producing

Note in the chat that switching to full mode is just "paste your CV when you're ready".

## If the user has no CV at all

Run the structured interview through the same sections of `templates/profile.md`, but in chunks. Don't ask for everything at once:

1. **Round 1** — identity, location, target role, comp expectations, constraints (the gap questions, asked upfront)
2. **Round 2** — most recent role in depth (title, dates, what they actually did, the wins)
3. **Round 3** — previous 1–2 roles, lighter detail
4. **Round 4** — skills inventory, education, anything else relevant

Spread these over the conversation, not all at once. The first round is enough to start being useful. Subsequent rounds happen as natural moments arise (writing a cover letter pulls more detail from role 2; interview prep pulls a STAR story; etc.).

At any point the user can paste a CV and we merge.
