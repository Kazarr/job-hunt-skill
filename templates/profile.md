# profile.md — `<Name>`

> **What this file is.** Verbose internal context about the user, for the agent's use during job-hunt work. Goes deeper than any CV — captures things employers never see (rate floor, why they're looking, no-go industries, hard constraints). The agent reads this before producing any user-specific artifact.
>
> **What it isn't.** Not a CV. Never sent to employers. Lives inside the skill; never rendered or exported by default.
>
> **How it gets populated.** Most of it comes from CV extraction on first invocation, with supplementary gap questions for things a CV doesn't contain. Grows organically as the user mentions new context.

## Identity
- Full name:
- Preferred name / pronouns:
- Location (city, country):
- Time zone:
- Open to: remote / hybrid / onsite — preferences and willingness to relocate
- Work authorization: e.g. "EU citizen", "US H1B holder, would need transfer", "UK Skilled Worker visa"
- Languages spoken with rough fluency: e.g. "Slovak (native), English (C1), German (B1)"
- Chat language preference: e.g. "Slovak" / "English" / "match my latest message" (default)
- Jurisdiction for contract / tax context: e.g. "Slovakia — živnosť (B2B) preferred over employment"

## Contact and links (optional — only what the user wants here)
- Email:
- Phone (if relevant for cover letters / CVs):
- LinkedIn:
- GitHub:
- Personal site / portfolio:
- Other relevant profiles:

## Career positioning
- Current state: e.g. "employed at X, passively looking" / "between roles, actively searching" / "currently freelancing, want stable engagement"
- Target role(s): job title, level, domain
- Roles deliberately not targeting (and why):
- Target company shape: stage (early / growth / public), size, remote/hybrid/onsite, domains of interest, domains to avoid
- Notice period at current role:
- Earliest start date:

## Compensation expectations
- Target range (gross, with currency and context): e.g. "EUR 5500–6500/month gross, Slovakia"
- B2B day rate target (if applicable): e.g. "EUR 300–350/day"
- Walk-away floor:
- Non-negotiables: e.g. "no equity-only comp", "no on-call beyond 1 in 6", "no relocation"
- Last comp received (for context only, not for disclosure):
- B2B vs employment preference and why:

## Summary — long form
Three to five paragraphs the user could say out loud as a thorough "tell me about yourself". Written in first person, with company names, role names, and specifics. The condensed CV summary lives elsewhere; this is the verbose version the agent uses to compress into tailored framings.

## Roles
Reverse chronological. Each role is more detailed than its CV bullets — the agent picks and compresses from here.

### `<Company name>` — `<Role title>`
- Dates: `<YYYY-MM>` – `<YYYY-MM or present>`
- Location: `<city / remote>`
- Reporting line: who they reported to, team size, where the team sat in the org
- Tech stack (or domain stack) used day-to-day:
- What the company / product does (one paragraph — useful context when interviewers haven't heard of the company):

**What I actually did, in detail:**
- Bullet 1 — what, how, outcome, numbers if available
- Bullet 2
- Bullet 3
- More is fine. Verbose is the point.

**Stories worth telling from this role:** (see also `## STAR stories` below — this is just a pointer)
- One-line pointer to each story.

**Why I left / am leaving (honest version):**
- For the user's own clarity. Interview-friendly framing of "why looking" goes under `## Talking points`.

### `<Previous Company>` — `<Role title>`
(Same structure.)

### Earlier roles
Roles older than ~10 years, or not relevant to current targeting, get one-line summaries:
- 2010–2012: Junior Developer at `<Company>`, mainly `<stack>`.

## Education
- Degree, institution, dates. One line each unless directly relevant.
- Certifications, only if recent and relevant.
- Coursework or thesis topic, only if it strengthens the case for a specific kind of role.

## Skills inventory
Verbose — the agent selects subsets per artifact.

- **Primary languages / tools (used recently, would work in tomorrow):**
- **Secondary (worked with, would need a day to ramp):**
- **Frameworks and libraries:**
- **Infra and platforms:**
- **Data stores:**
- **Observability / ops:**
- **Methodologies / practices:**
- **Domain knowledge:** (payments, healthtech, ad tech, education, etc.)
- **Soft skills with evidence:** e.g. "Mentored 3 juniors at `<prev co>`, two promoted within 18 months"

## Achievements (quantified)
Standalone, number-backed wins — the bullets that make cover letters and CVs land. Keep them flat and easy to scan.

- `<Title>` — what, where, when, my role, the numbers, why it was non-trivial
- `<Title>` — ...

## Open source / side projects
- Project name, link, what it is, the user's role, what's worth highlighting.

## Talks / writing / public work
- Conference talks, blog posts, podcast appearances. Title, venue, year, link.

## STAR stories
Pre-prepared narratives for behavioral interviews. 90 seconds spoken / ~200–300 words written each.

### `<Short story name>`
**Categories it covers:** e.g. technical decision, conflict, failure
**Company / when:** `<company, YYYY>`

**Situation.** 2–3 sentences — where, when, what was going on, why it mattered.

**Task.** 1–2 sentences — what the user was specifically responsible for.

**Action.** Longest section — what the user did, the trade-offs considered, the decisions made. Use names of technologies, people, decisions.

**Result.** 2–3 sentences — concrete outcome with numbers if available. What was learned.

**Pitfalls in telling this:**
- e.g. "Don't make it sound solo — be clear on team vs me"

Categories to cover with at least one story each:
- [ ] Technical (or domain) decision under real trade-offs
- [ ] Project that went wrong / failure the user owned
- [ ] Conflict with a peer or manager, resolved
- [ ] Mentoring or growing someone
- [ ] Driving cross-team work without formal authority
- [ ] Saying no / pushing back on scope or deadline
- [ ] Most complex problem solved
- [ ] Time the user missed something and recovered
- [ ] Time the user changed their mind based on data

## Talking points (reusable answers to common questions)
Common interview questions whose answers stay roughly the same across companies. Reusing them means the user doesn't re-derive a fresh phrasing each loop.

- **Tell me about yourself.** (90-second structure: what I do now → key strength → what pulls me forward.)
- **Why are you looking / why between roles?** (Clean, non-bitter version.)
- **Why this kind of company / role?** (Generic frame; per-application specifics added in each cover letter / interview prep.)
- **Why contractor not employee?** (If relevant to user's setup — jurisdiction-aware framing.)
- **How do you handle disagreement?** (One signature story.)
- **What are you working on growing right now?** (Honest growth area + how the user is addressing it.)
- **Salary expectations.** (Range + framing for deflection, see `## Compensation expectations` above.)

## Things I'm working on / want to learn
Useful for "what are you doing to grow" questions, and for the agent to spot when a role is genuinely aligned with the user's growth direction.

## Constraints and preferences (private — never goes to employers)
- Schedule constraints (kids, caregiving, etc.)
- Locations off-limits and why
- Companies / industries to avoid (with reasons so future-the-agent can judge edge cases)
- Past employers tricky as a reference
- Anything else the agent should know but never disclose

## Update log
- `<YYYY-MM-DD>`: profile.md created from CV
- `<YYYY-MM-DD>`: added `<story name>` after interview prep for `<company>`
- ...
