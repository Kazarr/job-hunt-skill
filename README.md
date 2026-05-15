# job-hunt skill

A Claude Code skill that helps a user run their job hunt — analyzing postings, drafting cover letters, researching companies, prepping for interviews, handling recruiter communication, negotiating rates, planning take-home challenges, spotting red flags in postings, and (one-off) improving a weak CV. The user's career context lives on disk in `profile.md` so it doesn't have to be re-derived every session.

## What it does

When Claude detects a job-hunt intent (you paste a job posting, paste a recruiter email, ask for help with comp, etc.), it follows [`SKILL.md`](SKILL.md), which routes to one of these focused references:

- [`references/analyze-posting.md`](references/analyze-posting.md) — extract real requirements, run fit analysis, give a verdict
- [`references/cover-letter.md`](references/cover-letter.md) — draft a cover letter that earns the read
- [`references/company-research.md`](references/company-research.md) — produce a decision-grade brief on the employer
- [`references/interview-prep.md`](references/interview-prep.md) — predict questions, map STAR stories, target tech prep
- [`references/recruiter-comms.md`](references/recruiter-comms.md) — parse incoming recruiter messages; draft follow-ups, rejection replies, scheduling
- [`references/rate-negotiation.md`](references/rate-negotiation.md) — anchoring, walk-away math, B2B-vs-employment conversion in the user's jurisdiction
- [`references/take-home.md`](references/take-home.md) — time allocation, testing philosophy, AI-usage discipline, domain gotchas
- [`references/red-flags.md`](references/red-flags.md) — yellow/orange/red flag framework, JD authenticity, pattern detection
- [`references/cv-extraction.md`](references/cv-extraction.md) — first-time setup: parse the user's CV into `profile.md`, fill gaps with a short interview
- [`references/cv-improvement.md`](references/cv-improvement.md) — one-off help making the user's master CV stronger (never per-application)

## What it does NOT do

- Per-application CV tailoring (CV is single source of truth, lives in the user's own tool)
- Autonomous reminders, scheduled follow-ups, or any "agent that runs in the background"
- Producing or maintaining the user's actual CV file
- Cross-application state files (no recruiter database, no comp baseline file, no lessons log — context lives in `profile.md` and individual `applications/<slug>/notes.md`)

If you want any of these, build a separate app — they're not what this skill is for.

## Layout

```
SKILL.md                  # entry point — Claude reads this first
profile.md                # user's career context (verbose, internal) — created on first use
applications/             # one folder per role applied to
  <company-role-YYYY-MM>/
    posting.md
    fit-analysis.md
    cover-letter.md       # when drafted
    company-research.md   # when researched
    interview-prep.md     # when prepping
    take-home.md          # strategy notes (actual code lives elsewhere)
    notes.md              # status frontmatter + chronological log
references/               # workflow guides, loaded on demand
templates/                # blank scaffolds
```

## How it's meant to be used

1. **First time the skill needs your context** — paste a job posting (or ask for a cover letter, fit analysis, etc.) and Claude will ask for your CV. Paste it or give a file path; Claude extracts a structured `profile.md` and follows up with 4–6 targeted questions for things a CV doesn't have (target role direction, comp expectations, hard constraints).
2. **Per application** — paste the posting. Claude saves it to `applications/<slug>/posting.md`, runs fit analysis, reports a verdict in chat, then asks what's next (cover letter, research, interview prep, etc.).
3. **Ongoing** — paste recruiter emails when they arrive, ask for comp guidance, ask "what's stale in my pipeline". Claude updates `applications/<slug>/notes.md` status frontmatter as things move.

## Trigger phrases

You don't need a magic word. Examples that all activate the skill:

- Pasting a job posting URL or full text
- "Help me apply for this"
- "Draft a cover letter for the Stripe role"
- "Research Acme before my interview"
- "What rate should I ask for?" / "They offered X, is it fair?"
- "I got a take-home — 2.5 hours, payment form"
- "Recruiter just emailed, how do I reply?"
- "Is this posting legit?"
- "My CV needs work"
- "Where am I in the pipeline?" / "What's stale?"

## Install

### As a personal skill (recommended)

Copy or symlink this folder into your Claude personal skills directory:

- Windows: `%USERPROFILE%\.claude\skills\job-hunt`
- macOS / Linux: `~/.claude/skills/job-hunt`

Claude Code picks it up next session. `profile.md` and `applications/` will be created inside the skill folder as you use it.

### As a project-local skill

Drop this folder into a project's `.claude/skills/job-hunt/` directory. Useful if you want profile + applications stored alongside other project files.

### Directly inside this repo

Open this repo in Claude Code and start working — Claude reads `SKILL.md` automatically because it's at the repo root. The `applications/` directory already exists; `profile.md` gets created on first use.

## Privacy note

`profile.md` is sensitive — it contains more detail than your public LinkedIn (comp floor, why you're looking, industries to avoid, etc.). `applications/<slug>/` folders contain tailored materials per role.

If you push this repo to a remote, make it private, or uncomment the relevant lines in `.gitignore` to exclude `profile.md` and `applications/` from version control. The skill itself (`SKILL.md`, `references/`, `templates/`, `README.md`) is fine to share.

## Design notes

- **Single source of truth on disk: `profile.md`.** Verbose, more than goes on a CV. Everything else is derived from it on demand.
- **Progressive disclosure.** `SKILL.md` is small; references load only when relevant. Keeps the context window lean across many sessions.
- **One folder per application.** Easy to find later, easy to compare past materials, easy to log status without overwriting history. Frontmatter in `notes.md` makes "what's in my pipeline" a quick scan.
- **No autonomous behavior.** The skill responds to what you bring. It doesn't volunteer reminders or check stale entries unless you ask.
- **Universal by construction.** No assumptions about your stack, region, or contract type — `profile.md` records all of that, and the references adapt to whatever's in it.
