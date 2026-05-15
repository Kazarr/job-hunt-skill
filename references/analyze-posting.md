# Analyzing a job posting

The point of this step is to turn a marketing document — which is what most postings are — into a concrete list of what the employer actually wants and how well the user matches. Every later step (cover letter, interview prep, take-home, recruiter reply) depends on getting this right.

## Step 1: Save the posting verbatim

Create `applications/<slug>/posting.md` and paste the raw posting in. Don't paraphrase — postings get edited and removed, and the user will want the original later. If the user gave a URL and the content isn't pasted, ask them to paste the body so we have a frozen copy.

Slug format: `<company>-<role-shorthand>-<YYYY-MM>`. Lowercase, hyphens not spaces. If the same company has multiple roles, disambiguate (`stripe-platform-eng-2026-05` vs `stripe-payments-eng-2026-05`). If the user reapplies later, make a new folder — don't overwrite.

Header of `posting.md`:
```markdown
# <Role> at <Company>
- Source: <URL or "pasted by user YYYY-MM-DD">
- Posted: <date if known>
- Location: <city / remote / hybrid>
- Comp range: <if listed, else "not stated">
- Application deadline: <if any>

## Raw posting
<paste>
```

## Step 2: Extract real requirements

Postings mix three kinds of statements and you have to separate them. Below the raw posting, write:

```markdown
## Extracted requirements

### Hard requirements (deal-breakers if missed)
- ...

### Strong preferences (will heavily weight selection)
- ...

### Nice-to-haves (mentioned but not weighted)
- ...

### Implicit signals (not stated, inferred from context)
- ...
```

How to classify:

- **Hard**: legal/structural things (work authorization, location, years-of-experience floors), and anything phrased as "required", "must have", "you have". Years-of-experience numbers are usually softer than they sound — treat a "5+ years" floor as "hard" only if the rest of the posting reinforces seniority; otherwise downgrade to "strong preference".
- **Strong preferences**: "looking for", "ideally", "we value", named technologies or methodologies in the responsibilities section.
- **Nice-to-haves**: anything in a "bonus" / "pluses" / "would be great if" bucket.
- **Implicit**: read between the lines. A posting that lists Kubernetes + Terraform + Datadog + PagerDuty implicitly wants someone who's done production on-call. "Wear many hats" implies small team / early stage. Specific named projects or libraries imply they want someone who'll engage with that community.

Don't pad this section. Five real hard requirements beat fifteen guessed-at ones.

## Step 3: Canary / attention check detection

Modern postings sometimes contain hidden instructions to detect generic / AI-generated applications. Scan the posting for:

- Hidden phrases like "mention `<word>` in your cover letter" or "begin your application with `<phrase>`"
- Quirky details about team members ("Work with Aryeh whose favourite fruit is strawberries") that may be tested in the application form
- Application questions with unusual multiple-choice answers
- Unexpected small details in an otherwise corporate JD (a favorite color, a hobby)

If you spot one, note it in `posting.md` under `## Canary signals` so the cover-letter / application-Q&A workflows can pick it up.

Mechanism matters: **multiple-choice with one correct answer** is an attention check (the user must answer correctly). **Open-text question** is a personality / engagement signal (the user can express character but isn't being graded for compliance).

## Step 4: Fit analysis

Create `applications/<slug>/fit-analysis.md`. For each extracted requirement, mark how the user maps to it using `profile.md`:

```markdown
# Fit analysis: <role> at <company>

## Match summary
- Strong matches: N / M hard requirements, N / M strong preferences
- Gaps: <list the misses>
- Overall verdict: Apply / Apply with caveats / Skip — one sentence why

## Per-requirement breakdown

### Hard requirements
- [x] 5+ years backend engineering — user has 7y (see profile § Roles)
- [ ] AWS production experience — user has GCP; no AWS in profile. **Gap.**
- [x] EU work authorization — user is in <country>

### Strong preferences
- [x] Go — user shipped Go at <role>
- [partial] Distributed systems — user has microservices experience but not at the scale described

### Nice-to-haves
- [x] Open-source contributions — user has <project>
- [ ] Conference speaking — none

### Implicit signals
- On-call expected — user has done on-call, surface this
- Small team culture — user came from a <N>-person team, good signal
```

For each gap:
- **Workable**: similar tech or transferable experience exists. Note how to position it in cover letter / interview.
- **Hard gap**: no equivalent. Either skip the application or address head-on in the cover letter ("I haven't shipped X, but I've operated equivalent Y at similar scale and would ramp quickly").

### Cross-application pattern check

Before finalizing the verdict, scan `applications/*/notes.md` and `applications/*/fit-analysis.md` (just the gaps sections) for recurring rejection causes or repeated gaps. If the user has been rejected 2+ times for the same gap that also applies to this posting, **call it out explicitly** in the verdict — this is a signal that either the gap is the binding constraint or the user should consider closing it (which is a different conversation, possibly using `references/cv-improvement.md` if it's a CV-presentation problem, or a learning plan if it's a real skill gap).

Don't maintain a separate "lessons" file — derive the pattern fresh each time. Old patterns may have been closed; only what's still relevant matters.

## Step 5: Verdict

End `fit-analysis.md` with a verdict block:

```markdown
## Verdict
- Recommendation: Apply / Apply with caveats / Skip
- Why: <one paragraph>
- If applying, lead with: <user's 2-3 strongest assets for this role>
- If applying, address head-on: <the gap(s) that need a frame>
- Questions to clarify in recruiter screen: <unspecified comp range, unspecified contract type (B2B vs employment), unstated on-call expectations, location/visa specifics, anything else the posting was vague on>
- Cross-application note: <if a pattern surfaced in step 4, what it means here>
```

**Always include vague-comp as a clarifier.** If the posting says "competitive", "based on experience", "depending on profile", or simply doesn't list a range, this is a question for the first recruiter call — list it explicitly in the verdict and surface it in chat. Reason: comp is the most common late-stage process-killer; not knowing the band before investing in interviews costs the user time.

Share the verdict in chat. If "Skip", explain the reasoning so the user can override — they may have context you don't (a referral, a strategic reason to try, knowledge that a "hard" requirement is actually soft for them).

## Fast path: just the verdict

If the user asks "should I apply?" and only wants a quick read, you can skip writing the full `fit-analysis.md` to disk and give the verdict in chat after extracting requirements mentally. But once they decide to apply, do the full write-up — every downstream step needs it.

## Red-flag handoff

While extracting requirements, watch for signals that the posting itself may not be legit (vague company, USDT salary, sanctioned-jurisdiction filters, etc.). If two or more red flags appear, surface them and consider routing through `references/red-flags.md` before continuing with fit analysis. A posting that flunks the legitimacy check shouldn't get a fit analysis at all.
