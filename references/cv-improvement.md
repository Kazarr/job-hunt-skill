# CV improvement — one-off help with the user's master CV

The user has a CV that's thin, vague, outdated, weak, or doesn't exist. This reference helps them make it stronger as a one-off pass. **Not** per-application tailoring (that stays out of scope per skill design). The output of this workflow is suggestions and optionally a draft revision that the user takes back to their own CV tool — the skill does not maintain a CV file.

## When to invoke

- User explicitly asks: "review my CV", "my CV is weak", "help me rewrite my CV", "build me a CV from scratch", "is my CV any good"
- `cv-extraction.md` finished and the CV looked thin — offer this reference and let the user decide
- The user has had multiple rejections and we suspect CV presentation might be a factor (not the only one — also check fit alignment, market timing)

## Prerequisites

- `profile.md` exists and is reasonably populated (CV extraction has happened). This is essential — improvement uses `profile.md` as the source of suggestions, not just the existing CV.
- The current CV (paste or file path) — or a clear statement of "no CV exists yet, build from scratch".

If `profile.md` is empty, do `cv-extraction.md` first.

## Output discipline

Default output: **suggestions in chat**, broken into priority tiers. The user picks which to apply and updates their own CV in their own tool.

Optional output, only on user request: a **revised CV draft in chat** (markdown). The user copies it out. Don't save a `cv.md` to the skill folder by default — the skill is not the CV's home.

If the user explicitly says "save a draft so I can iterate", save to `cv-draft.md` at the skill root with a `<!-- one-off draft, not maintained -->` comment at the top, and remind the user this is a one-time artifact.

## Step 1: Read both sources

- Read `profile.md` (the truth about the user)
- Read the user's current CV (or note: empty)

Hold both in mind. The improvement work is essentially: *what's true about this user that the CV is failing to show*.

## Step 2: Diagnose

Score the existing CV across a fixed set of common weaknesses. Don't lecture the user; quietly form a diagnosis and use it to prioritize fixes.

**Weakness checklist:**

| Weakness | What it looks like | Why it costs interviews |
|---|---|---|
| **No summary / tagline** | CV starts with contact info → straight to roles | Reviewer has no anchor for what kind of role to compare against |
| **Activity bullets, not impact bullets** | "Worked on the checkout system" / "Responsible for API design" | Reads as a job description, not an accomplishment |
| **No quantification** | "Improved performance significantly" | Reviewer can't size the work; loses credibility |
| **Same depth on every role** | 4 bullets on a 6-month internship and 4 bullets on a 4-year senior role | Looks like a template; mis-weights early career |
| **Stale terminology** | "Web 2.0", "RESTful APIs" when team is doing gRPC | Signals out-of-date practitioner even if user is current |
| **Skills as wall of 60 items** | Skills section is a paragraph of every technology ever touched | Unscannable; signals no judgment about what matters |
| **Mission / objective statement** | "Seeking a challenging position to leverage my skills" | Empty calories; takes prime real estate |
| **No clear role title progression** | Inconsistent titles, gaps unexplained | Reader has to reconstruct the career path |
| **Generic language** | "Results-oriented", "passionate", "team player" | Reads as ChatGPT-generated; canary-failing |
| **ATS-hostile format** | Two-column layout, sidebars, icons for skills | Parser strips half the content; some recruiters never see it |
| **No tech / domain stack annotation per role** | Bullets don't tell you what was built with what | Reviewer can't filter by stack relevance |
| **Missing or vague dates** | "2019 – Present" with no month | Looks careless on a senior CV |
| **Photo, age, marital status (region-dependent)** | Personal info that invites unconscious bias | Norm varies by country — flag, don't dictate |
| **Length wrong for level** | 1-page CV for 15-year career, or 3-pager for 2 years | Mismatch signals poor self-editing |
| **Missing achievements that ARE in profile.md** | Profile has quantified wins; CV doesn't surface them | The strongest evidence is hidden |

Build a diagnosis list specific to *this* CV — not all of these apply to every CV.

## Step 3: Compare against `profile.md`

What's strong evidence that's in `profile.md` but missing or weak on the CV?

- Quantified achievements that should be bullets
- Roles where the bullets are vague on the CV but verbose in `profile.md`
- Stories that contain CV-worthy headlines
- Skills the user actually has but didn't list
- Recent work / certifications since the CV was last updated

For each, note specifically: *"this concrete thing exists in your profile; let's get it on the CV"*.

## Step 4: Prioritize fixes

Sort the diagnosis into three tiers:

```markdown
## Must-fix (these are likely costing interviews)
- ...

## Should-fix (clear improvements, not as urgent)
- ...

## Nice-to-fix (polish)
- ...
```

For each item, give:
- What's currently there (a short quote of the existing CV section)
- What to change it to (a concrete rewrite, not a vague suggestion)
- Why (the failure mode it fixes)

**Example of a good fix entry:**

> ### Must-fix: replace activity bullet with impact bullet
>
> Current: *"Worked on improving API performance."*
>
> Proposed: *"Cut p99 latency on the orders API from 800ms to 120ms by adding a Redis read-through cache and rewriting the hottest query path. (Source: profile.md § Vivicta — 2023.)"*
>
> Why: activity-first bullets read like a job description; impact-first bullets read like accomplishments and let the reviewer size the work.

**Example of a bad fix entry to avoid:**

> *"Add more numbers to your bullets."* — too vague, gives the user nothing to act on.

## Step 5: Present and let the user decide

Show the prioritized list in chat. Don't dump 30 fixes at once — group them, and lead with the 3–5 that would have the biggest impact.

Pattern:
> "Top three things I'd change first:
> 1. `<must-fix #1>` — `<before> → <after>`
> 2. `<must-fix #2>` — `<before> → <after>`
> 3. `<must-fix #3>` — `<before> → <after>`
>
> There are `<N>` more in the should-fix tier and `<M>` polish items. Want me to go through them, or do these top three first and we'll see how it feels?"

The user decides the pace.

## Step 6 (optional): Produce a revised draft

If the user asks for a full revised CV ("just give me the whole thing"), produce one in chat. Use this default structure for engineering / knowledge work:

```markdown
# <Name>
<one-line tagline> | <location, remote preference> | <email> | <github / portfolio>

## Summary
<3-4 lines, anchored to target role and strongest match for it>

## Experience
<reverse-chronological>

### <Company> — <Role>
<dates> | <location>
<one-line stack annotation if useful>

- <impact bullet 1>
- <impact bullet 2>
- <impact bullet 3>

### <Previous Company> — <Role>
...

## Skills
<grouped, 3-5 categories, ~15-25 items total>

## Education
<one or two lines unless unusually relevant>

## (Optional) Selected projects / Open source / Talks
<only if they strengthen the case>
```

For other functions (design, sales, marketing, ops), adjust the section list — but the principle is the same: lead with summary anchored to target, then experience with impact bullets, then supporting sections.

Tell the user: **"This is a one-off draft. Copy it back to your own tool (Google Docs, Word, whatever). The skill won't track this file going forward — your CV stays your domain."**

If they explicitly want it saved for iteration, write to `cv-draft.md` at the root with the not-maintained header comment.

## Step 7: Build-from-scratch case

If the user has no CV:
1. Confirm `profile.md` is populated enough (run `cv-extraction.md` in interview mode first if not).
2. Produce a draft using the structure in step 6, drawing entirely from `profile.md`.
3. Walk the user through it section by section — explain *why* each part says what it says, so they can defend it.
4. Same one-off output discipline: chat by default, `cv-draft.md` if explicitly requested.

## Things to avoid

- **Don't invent.** If you'd put a number on a bullet that isn't in `profile.md`, ask the user for the number — don't fabricate.
- **Don't restyle to a fashion.** Two-column layouts, icon skill bars, color-block sidebars look modern but break ATS parsers. Plain markdown / plain Word format wins for engineering and most knowledge-work roles. (Visual roles like design are an exception — but the user knows their field's norms better than this reference.)
- **Don't tailor to a specific posting** — that's out of scope (per skill design). If the user asks for tailoring, remind them: "I help you have one strong master CV. For a specific posting, the cover letter and your interview prep do the targeting work."
- **Don't auto-trigger.** This reference runs when the user asks (or accepts an offer after extraction), never as a surprise.
- **Don't promise outcomes.** "This will get you more interviews" — no. "These fixes address the most common reasons strong candidates get screened out" — yes.

## After improvement

If the user updates their CV based on the suggestions, ask them to paste the new version (or update `profile.md` directly if there are new facts they want to be sure are captured). Otherwise the skill won't know the CV changed.

`profile.md` is the source of truth. The CV is downstream. After improvement, both should be aligned on what's real — but only `profile.md` lives in the skill.
