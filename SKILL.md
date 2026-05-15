---
name: job-hunt
description: Help a user run a job hunt end-to-end — analyzing job postings, drafting cover letters, researching target companies, preparing for interviews, handling recruiter communication, negotiating rates, tackling take-home challenges, spotting red flags in postings, and improving a weak CV. Use whenever the user shares a job posting (URL, PDF, or pasted text), mentions applying for a role, asks for a cover letter, asks "should I apply to X", asks for interview prep, pastes a recruiter email and wants help replying, asks about compensation or rate negotiation, asks "is this posting legit", asks for help with a take-home challenge, asks to review or improve their CV, or says things like "I want to apply for this", "help me with my application", "draft a cover letter", "prep me for this interview", "research this company", "is this a fit", "the recruiter said X, what do I reply", "my CV needs work". The skill should activate even when the user does not explicitly say "job hunt" — a pasted job description, recruiter email, or compensation discussion is enough.
---

# Job Hunt

A workflow for helping a user run a job search where the high-cost, repetitive thinking — what to send a recruiter, whether a posting is a fit, what to write in a cover letter, how to prep for an interview, how to anchor a rate, whether a posting is even legit — is done well and quickly, and the user's career context lives on disk so it doesn't have to be re-derived every session.

## Mental model

There is **one master file**, `profile.md`, that captures everything Claude needs to know about the user to guide them on their job hunt: who they are, what they've done, what they're targeting, what their constraints are, the stories they tell in interviews, the talking points they reuse. This file is more verbose than what would go on a CV — it includes things employers never see (rate floor, why they're looking, no-go industries, constraints).

`profile.md` is **internal context**, not a CV. The user maintains their actual CV in their own tool (Word, Google Docs, a PDF, LinkedIn). The skill helps with everything *around* the CV — fit analysis, cover letters, recruiter messages, interview prep, rate negotiation — and can also help the user *improve* their CV (one-off pass), but it never tries to produce or maintain a per-application tailored CV.

For each application the user is actively working on, a folder under `applications/<slug>/` holds the posting, fit analysis, cover letter draft, company research, interview prep notes, take-home work, and a `notes.md` with status frontmatter and a chronological log. Folders accumulate. Old applications stay for reference.

## Directory layout

```
profile.md                    # user's career context (verbose, internal)
applications/
  <company-role-YYYY-MM>/
    posting.md                # raw posting + extracted requirements
    fit-analysis.md           # gap analysis vs profile
    cover-letter.md           # when drafted
    company-research.md       # when researched
    interview-prep.md         # when prepping
    take-home.md              # strategy notes (actual code lives elsewhere)
    notes.md                  # status frontmatter + chronological log
references/                   # workflow guides (loaded on demand)
templates/                    # blank scaffolds
```

`profile.md` and individual `applications/<slug>/` folders are user data — they accumulate as the user works. The `references/` and `templates/` directories are part of the skill itself.

## Bootstrapping a user the first time

If `profile.md` does not exist, the user is new. Don't block them with a setup interview — but the first time they ask for something that needs their context (fit analysis, cover letter, anything user-specific), bridge the gap by asking for their CV.

Pattern, in the user's own language:

> *"I can help much better if I know your background. Paste your CV here, or give me a file path (PDF / DOCX / MD / TXT all work). If you'd rather skip, I can still do market-only analysis on this posting — recruiter behavior, red flags, rate market check — but anything that asks 'is this a fit for **me**' will be limited."*

If the user provides a CV → follow `references/cv-extraction.md`: parse the CV into `profile.md` sections, then ask 4–6 targeted gap questions for things a CV doesn't contain (career direction, comp expectations, hard constraints, why they're looking).

If the user declines → do market-only analysis. Note in the chat which parts of the answer are limited by the missing profile.

If the user has no CV at all → run the same `cv-extraction.md` workflow in interview mode: ask through the sections one at a time. Mention that they can also paste a draft CV later and the skill will merge.

If the user's CV is thin / sparse / outdated → after extracting what's there, offer `references/cv-improvement.md` to help strengthen it before going further. This is one-off help with their *master* CV, not per-application tailoring.

## What to do based on what the user asks

The user usually arrives mid-flow. Detect intent and route to the right reference. Don't make them say a magic phrase — a pasted job description, a pasted recruiter email, a comp question, or a "is this legit?" is enough signal.

| User signal | Workflow | Reference |
|---|---|---|
| Pastes a job posting / URL with no other context | Save posting, run fit analysis, ask what's next | `references/analyze-posting.md` |
| "Is this a fit?" / "Should I apply?" | Fit analysis only (skip the writeup if user wants a quick read) | `references/analyze-posting.md` |
| "Draft a cover letter" / "Write a cover letter" | Cover letter for this application | `references/cover-letter.md` |
| "Research this company" / "What do I need to know about X" | Company research brief | `references/company-research.md` |
| "Prep me for the interview" / "What will they ask" | Interview prep | `references/interview-prep.md` |
| Pastes a recruiter email / "what do I reply" / "draft a follow-up" / "they rejected me, how do I respond" | Recruiter communication — incoming parse and/or outgoing draft | `references/recruiter-comms.md` |
| "What rate should I ask" / "they offered X" / "how do I negotiate" / "B2B vs employment" | Rate negotiation strategy | `references/rate-negotiation.md` |
| "I have a take-home" / "they gave me a coding challenge" | Take-home strategy | `references/take-home.md` |
| "Is this posting legit" / "this feels off" / "red flag check" | Red-flag and authenticity analysis | `references/red-flags.md` |
| "Review my CV" / "my CV is weak/thin/old" / "help me rewrite my CV" / "build me a CV from scratch" | CV improvement (one-off, master CV — never per-application) | `references/cv-improvement.md` |
| First-time invocation, profile.md missing, user-specific work requested | CV extraction + supplementary interview | `references/cv-extraction.md` |
| "Update my profile" / "add X to my profile" / "I just got promoted to Y" | Append to `profile.md` directly — no reference needed | — |
| "How's my pipeline" / "what's outstanding" / "what's stale" | Scan `applications/*/notes.md` frontmatter, summarize in chat | — |

If the intent is ambiguous (just a URL, no instructions), default to fit analysis — it's cheap, the user always wants it, and it sets up everything else.

If the user mentions a recurring pattern in their rejections ("rejected 3 times for Node now"), don't create a state file for it — but **do** weight future fit analyses against that pattern and call it out explicitly when relevant.

## Universal rules

These apply across every workflow.

1. **Pull from `profile.md`, never invent.** If a fact (achievement, metric, dates, technology used) isn't in `profile.md`, ask the user — do not fabricate. A cover letter or CV improvement with invented numbers can sink an offer at reference-check time.
2. **Use the user's voice.** No "leveraged synergies", no "results-oriented professional", no filler superlatives. Match the register of how the user actually writes in their own profile prose and CV. If the user writes plainly and directly, all artifacts read plainly and directly.
3. **Mirror the user's chat language.** If the user writes in English, respond in English. If Slovak, Slovak. If they switch, follow. Never assume a default — read the cue from their most recent messages.
4. **Match the posting's language for artifacts.** A cover letter for a German posting is written in German (unless the posting's application instructions say otherwise). For mixed-language EU postings, match the language of the application instructions section, fall back to English.
5. **One folder per application.** Always work inside `applications/<slug>/`. Slug format: `<company>-<role-shorthand>-<YYYY-MM>`, lowercase, hyphens not spaces (e.g. `stripe-backend-2026-05`). If the user reapplies to the same company in a different month, make a new folder — don't overwrite.
6. **Don't promise what we haven't confirmed.** When researching a company or writing about why the user is excited about a role, label speculation explicitly ("Likely — needs confirmation:"). Saying "I know your team is migrating to Rust" when it isn't is worse than saying nothing.
7. **Keep `notes.md` updated.** Every meaningful event on an application (applied, recruiter reply, interview scheduled, rejection, ghosted) gets a one-line dated entry **and** the status frontmatter updated. This is what the pipeline scan reads.
8. **Don't produce a CV.** CV creation and per-application tailoring are out of scope. The exception is `cv-improvement.md`, which helps the user produce or polish their *master* CV as a one-off — and even then, output goes to chat by default for the user to take back to their own tool, not into a maintained `cv.md` file in the skill folder.
9. **Localize market context.** Rate ranges, contract types (B2B vs employment vs UoP vs 1099), tax implications — all depend on the user's jurisdiction. Read it from `profile.md`'s identity section. If `profile.md` doesn't say, ask once and write it back.
10. **No autonomous action.** The skill does not send reminders, schedule follow-ups, or push the user. It responds to what the user brings. If the user asks "what's stale", scan and report — but don't volunteer "by the way, Acme is stale" without being asked.

## Output discipline

Substantive artifacts go to files. Short conversational outputs stay in chat.

To files:
- Job postings (`applications/<slug>/posting.md`)
- Fit analyses (`fit-analysis.md`)
- Cover letters (`cover-letter.md`)
- Company research briefs (`company-research.md`)
- Interview prep documents (`interview-prep.md`)
- Take-home strategy notes (`take-home.md`)
- Application logs (`notes.md`)
- Updates to `profile.md`

In chat only:
- Fit verdicts, summary takeaways
- Status reports / pipeline summaries
- "Here's what I changed and why" diff explanations
- Suggested edits the user might want to make manually
- Improved CV drafts (these are taken back to the user's own CV tool, not maintained here)

If the user explicitly asks for something to be saved that isn't in this list, do it — but don't volunteer files by default.

## Status frontmatter for `notes.md`

Every `applications/<slug>/notes.md` starts with this block, kept current as the application progresses:

```yaml
---
status: drafting | applied | recruiter-screen | hiring-manager | technical-screen | take-home | onsite | offer | negotiating | rejected | withdrawn | ghosted
applied_date: YYYY-MM-DD | null
last_event: YYYY-MM-DD
next_action: <one line>
recruiter: <name, if any>
---
```

When the user mentions a status change (even casually — "I just sent it" / "they replied" / "got rejected"), update this block plus add a chronological log line. Don't wait to be asked.

When the user asks "where am I in the pipeline" or "what's stale", scan every `applications/*/notes.md` frontmatter and summarize in chat — group by status, flag entries where `last_event` is more than 7 days ago and status is in {applied, recruiter-screen, hiring-manager, technical-screen, take-home, onsite, negotiating}.

## On Slovak / non-English context

If the user writes in Slovak / Czech / Polish / German / French / etc., the skill follows along. Treat references in `references/` as guidance written in English for Claude — apply them, don't translate them aloud. Artifacts the user will read go in their language; artifacts intended for an employer go in the posting's language.

For Slavic-language users specifically: contract types like "živnosť" (Slovakia) / "IČO" / "JDG" (Poland) / "OSVČ" (Czech) all map to B2B contracting and should be handled in `rate-negotiation.md`'s framework. The skill should read the user's jurisdiction from `profile.md` and use the local terminology.

## When references kick in

Read the relevant reference *before* doing the work, not after. Each reference covers patterns that are easy to get wrong from memory — the right opening line for a cover letter, what a recruiter email is really asking, how to weight a rate anchor without losing the negotiation. The references are short on purpose; reading the right one costs little and prevents a lot.

If the user's request spans multiple references (e.g. "draft a cover letter and prep me for the interview"), do them in sequence and read each reference at the moment its work starts, not all upfront.
