# Company research

Useful research changes how the user pitches themselves and what questions they ask. Useless research is a Wikipedia dump pasted into a doc. The goal is a short, decision-grade brief — what does the user need to *know*, not *recite*.

## Output

Write to `applications/<slug>/company-research.md`. Keep it under 600 words. If you find yourself going longer, you're researching for its own sake.

## Structure

```markdown
# <Company> — research brief
Last updated: <YYYY-MM-DD>

## What they do (one paragraph)
Plain-English description of the business. What do they sell, to whom, how do they make money. If the company is well-known, one line is enough.

## Stage and shape
- Funding / public / bootstrapped: ...
- Headcount (rough): ...
- Engineering / function team size if knowable: ...
- Office / remote posture: ...

## Stack and methodology signals
What we can infer from job postings, engineering blog, GitHub, conference talks, public statements.
- Languages / frameworks / tools: ...
- Infra and platform: ...
- Notable internal practices or known systems: ...
Sources: <linked>

## Recent moves (last 12 months)
Funding rounds, acquisitions, big launches, layoffs, leadership changes, public engineering/product posts. Only what's relevant — not press release recap.

## Culture signals
What's visible from outside: Glassdoor (with skepticism), employee blog posts, public engineering/culture writeups, conference behavior. Note signals, not verdicts.
- Strengths visible: ...
- Watch-outs: ...

## Specific to this role
- The team this role is on (if knowable): ...
- The problem the role exists to solve (inferred from posting): ...
- Likely interviewers / hiring manager (if knowable): ...

## Questions to ask in the interview
Three to five real questions, derived from the gaps in this research. Not "what's the culture like" — questions that show the user has thought about the actual job.

## Open unknowns
Things we'd want to know but couldn't find. Flag explicitly — don't fill the gap with speculation.
```

## What to actually look at

In rough priority order:

1. **The company's own engineering / function blog / handbook.** Highest signal. If they have one, read the last 3–5 posts. Stack mentions, problems they're solving, how they talk about the craft — all useful.
2. **The posting itself, re-read for context.** What does the language tell you about the team? "Wear many hats" = small team. "Drive cross-functional alignment" = larger / matrixed org. "Move fast" = either real urgency or vague filler — check funding stage to disambiguate.
3. **Recent press / funding.** TechCrunch, Crunchbase, the company's own newsroom. Look for last funding round size + date, recent product launches, leadership changes, layoffs.
4. **Public profiles of the hiring manager and likely interviewers**, if names are knowable. LinkedIn for tenure and background, conference talks and blog posts for technical perspective. Don't stalk personal social media.
5. **GitHub.** If they have a public org, look at active repos, languages, recent commit cadence, how they handle issues. Strong signal for engineering culture.
6. **Glassdoor / Levels.fyi**, treated as noisy. Read multiple reviews, weight recent ones, ignore both 1- and 5-star outliers. Levels.fyi is more reliable for comp than Glassdoor.

For non-tech roles, swap Glassdoor and Levels for the equivalent role-specific resources (e.g. design publications, sales/marketing community forums, etc.).

## What to skip

- Company mission statement marketing prose. Tells you nothing.
- Anything from before the most recent funding round or major leadership change — likely stale.
- Founder Twitter unless directly relevant.
- Pop-business news framing of the industry.

## How to use the research

In the **cover letter**: paragraph 1 specificity, sourced from "Recent moves" or "Stack and methodology signals". Don't quote the research at the company — reference what they did and connect it to the user's experience.

In the **interview**: the "Questions to ask" section is the payoff. When the interviewer says "do you have any questions for us", the user has three good ones lined up, derived from real research. Strong signaling moment.

In **fit / apply decision** (if doing research before the fit analysis is final): "Stage and shape" and "Recent moves" can flip a borderline apply/skip. A company that just did layoffs in the user's target function deserves a second think.

## Source quality

For each meaningful claim in the brief, note where it came from. A research doc with no sources is one the user can't defend in an interview — and shouldn't trust.

```markdown
- Engineering blog moved from Go to Rust last year [eng blog, 2025-10]
- Recently raised Series C, $80M [Crunchbase]
- VP Eng was previously at <other company> [LinkedIn]
```

## Refresh policy

Company research goes stale within 3–6 months. If the user is interviewing after a long delay between applying and getting a callback, do a quick refresh pass (recent posts, recent news) before the interview rather than trusting the original brief.

## Red flag during research

If the research surfaces serious legitimacy concerns (no verifiable office, no real employees on LinkedIn, only PR-style mentions in news, regulatory issues), pause the research and route to `references/red-flags.md`. Don't write a glowing brief on a company that may not be real.
