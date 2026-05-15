# Interview prep

Interview prep done well is targeted, not generic. Generic prep ("review data structures") is what every candidate does. Targeted prep means: given *this* role at *this* company, predict the specific questions, line up the user's strongest stories against them, and identify the gap(s) that need a real answer.

## Output

Write to `applications/<slug>/interview-prep.md`. This document grows over the loop — initial pass before the screen, expanded passes before each subsequent round.

## Prerequisites

- `applications/<slug>/posting.md` and `fit-analysis.md` — to know what they're hiring for and where the user is strong/weak
- `applications/<slug>/company-research.md` — to know what kind of company is asking
- `profile.md` — for the STAR stories section and talking points
- Schedule info, if known: how many rounds, formats, named interviewers

## Structure

```markdown
# Interview prep: <role> at <company>

## Format and schedule
<what we know about the loop>

## Likely question categories
Ranked by probability for this specific role/company.

## Predicted questions
Specific questions, with my best read of what each is really probing for.

## STAR stories — which to lead with
Stories from profile.md (§ STAR stories) mapped to the categories above. If a category has no good story, flag it as a prep gap.

## Targeted prep
The 5–10 topics worth refreshing for this specific role — not a textbook dump.

## Gaps to address
The one or two genuine weak spots from fit-analysis the user needs a real answer for.

## Questions to ask them
Pulled from company-research.md "Open unknowns", refined.

## Logistics
Time zone, format (video / onsite / take-home), names of interviewers, what to bring.
```

## Predicting questions

Predict by stage and company shape, not by guessing.

### Recruiter / first screen (30 min)
Mostly logistics and basic fit. Predictable questions:
- Why are you looking? (Clean, non-bitter answer — see `profile.md` § Talking points.)
- Why this company specifically?
- Compensation expectations. (Have a range — see `references/rate-negotiation.md`.)
- Notice period / earliest start.
- Other processes in progress? (Honest but vague is fine.)

### Hiring manager (45–60 min)
Read for fit, level, motivation. Mix of behavioral and lightweight technical.
- Walk me through your CV / your career. (Have a 3-minute version ready.)
- Tell me about `<specific role/project on CV>`. (Be ready to defend every line.)
- A behavioral question pointed at the role's main need. (E.g. for a senior IC: "tell me about a time you owned a technical decision that didn't work out".)
- The user's questions about the role / team / their priorities.

### Technical (or domain) screen (45–90 min)
This is where company-specific patterns matter most. Look at:
- Glassdoor interview reports (noisy, weight recent ones)
- Engineering / function blog posts about hiring (some companies publish their loop)
- The role's emphasis — systems-design-heavy posting predicts systems design screens; data-pipeline-heavy posting predicts SQL + pipeline design

Common formats for engineering roles:
- Coding (algo) — big tech, some startups
- System design — mid-senior+ at most companies
- Take-home — more common at startups; see `references/take-home.md` if one is set
- Live debugging / pair programming — companies that emphasize collaboration
- Domain-specific deep dive — specialist roles

For each, predict 3–5 specific *kinds* of problem, not just "do leetcode". Example for a payments backend role: idempotency, retry semantics, exactly-once vs at-least-once, ledger consistency under failure.

For non-engineering roles, the equivalents matter: portfolio walk-through for designers, sales call simulation for AEs, copy / brief exercise for marketing, case interview for consultants. Predict based on the function and the company's typical loop.

### Onsite / full loop
Multiple of the above plus typically:
- A second behavioral round, often with a peer ("bar raiser", "values" interview).
- Sometimes a "your project" deep dive — user presents something they've worked on. Have a 15-minute walkthrough of a real project ready, with whiteboard-able architecture or visual.

## STAR stories

The library lives in `profile.md` under `## STAR stories`. Don't write fresh stories per company — pick from the library and map them per interview.

The STAR map for this interview:

```markdown
## STAR map for <company> <role>

| Likely question type | Lead story | Backup story |
|---|---|---|
| Technical / domain decision | <Story name from profile.md> | <name> |
| Conflict | <name> | — |
| Failure | <name> | <name> |
```

If a column is empty, that's a prep gap to develop with the user *before* the interview. Either pull a story from `profile.md`'s `## Roles` sections that fits (and add it to the stories section permanently), or flag that the user needs to prepare one.

## Targeted technical / domain prep

Don't tell the user to "do leetcode" or "review the basics". Look at the posting and predict the actual surfaces:

For engineering roles, examples:
- Posting says "distributed systems" → CAP, consensus basics (Raft/Paxos at a high level), leader election, partition handling, write/read quorums, idempotency
- Posting says "databases" → indexes, query planning, transaction isolation, locking, replication trade-offs
- Posting says "Kubernetes" → pod lifecycle, scheduling, networking model, operators, common failure modes
- Posting says "ML infra" → batch vs online inference, feature stores, model versioning, GPU scheduling
- Posting heavy on "modern frontend" → signals / hooks / hydration / Core Web Vitals depending on stack

Give a focused list of 5–10 topics with a sentence each on what's worth refreshing. Don't dump a textbook.

For algo screens, look at the company's history (leetcode patterns, glassdoor reports) and pick a focused set. Quality of practice on 20 well-chosen problems beats 200 random ones.

## Gaps to address

From the fit analysis, pick the one or two genuine weak spots. For each, develop an honest answer that:
1. **Acknowledges the gap straight on.** No dodging — interviewers read dodges immediately.
2. **Points to the closest transferable experience.**
3. **Shows a concrete plan for closing it.**

Pattern:
> "I haven't shipped production `<X>`. I've operated `<Y>` at similar scale — `<one sentence of detail>`. The conceptual gap is mostly vocabulary; I'd expect a few weeks to be productive and a couple months to be at the level I am with `<Y>`. To get a head start I've been `<concrete thing>`."

Practice this answer with the user before the interview. Awkward first delivery is worse than no preparation.

## Compensation discussion

When comp comes up in any round, route to `references/rate-negotiation.md`. The interview prep should remind the user of the range and the framing, but the strategy lives in that reference.

## Questions to ask them

Three to five, real ones. Use what came out of `company-research.md`'s "Open unknowns".

Patterns that work:
- "What does the first 90 days look like for whoever takes this role?"
- "What's the biggest `<technical / domain>` challenge the team is working on right now?"
- "How does the team decide what to work on quarter to quarter?"
- "What's something that's harder here than at companies you've worked at before?" (to the interviewer about their experience)
- For the hiring manager specifically: "How would you define success for this hire after a year?"

Avoid:
- Anything answered on the company's careers page
- "What's the culture like?" — too generic, signals you didn't research
- Comp questions to the hiring manager (those go to the recruiter)

## After the interview

In `applications/<slug>/notes.md`, log:
```
2026-05-20 - Hiring manager call (Jana Novák, 45m). Topics: career walkthrough, Kafka rewrite story (well received), team structure. Next: technical screen, scheduled 2026-05-27. Liked: emphasized async-first. Watch: vague on roadmap stability.
```

And update the status frontmatter accordingly. This log is what the user reads before the next round. Compounds across the loop.
