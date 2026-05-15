# Red flag and authenticity analysis

A job posting (or recruiter approach) can be perfectly real, mildly sketchy, or an active trap. The cost of skipping a borderline-shady opportunity is small. The cost of cleaning up after a bad employer — unpaid invoices, scope creep, visa entanglement, reputational damage — is large. This reference covers how to read the signals.

## When to invoke

- User says "this posting feels off"
- User says "is this company / posting legit"
- Two or more flags appear during normal `analyze-posting.md` work
- Recruiter approach looks unusual (USDT salary mention, weird channel, undisclosed client, etc.)
- User pastes a posting and asks "should I apply" but something in the posting is structurally weird

## Output

Brief red-flag analysis in chat — you don't need a separate file unless the user explicitly wants one saved. If saving, write to `applications/<slug>/red-flags.md` (or just append a `## Red flags` section to `applications/<slug>/posting.md`).

## The three-tier framework

Flags don't auto-skip an opportunity. Combinations do.

### Yellow flags — ask questions, don't auto-skip

These are common in legitimate companies and don't indicate anything wrong on their own. Worth probing in early conversations:

- Salary / rate undisclosed
- Heavy "passion" / "culture fit" / "rockstar" / "family" emphasis over concrete responsibilities
- Generic company description without specific clients or named products
- Very short tech stack list (~3 items) or very long (everything ever)
- "Remote" without specific country / time zone constraints
- Free fruit / ping pong / pizza framed as primary benefits
- Office locations listed but no remote tolerance
- Job title slightly inflated relative to responsibilities (or vice versa)
- Posting reposted often (could mean churn, or could mean slow process)

**Action:** note them, ask questions about them in the recruiter screen or initial email. One yellow flag is nothing.

### Orange flags — think before applying

These need explanation. Each one alone might be fine; investigate before investing time:

- Important info revealed only after applying (location restrictions, work pattern, comp structure)
- Salary far below or far above market for the role / region
- Country exclusion lists without explanation ("must not currently reside in X, Y, Z")
- Company LinkedIn page very new (<1 year) or absent for a company that claims to be established
- Glassdoor consistently negative on the same axes (especially compensation, management, work-life)
- CEO / founder not findable online for an established company
- Crypto-only company in a bear market (layoff risk)
- Many simultaneous remote openings for a small company (could be growing, could be churning)
- Equity-heavy compensation with minimal cash for someone past the early-career stage
- Recruiter pushing for an unusually fast decision
- Generic offshore registration (BVI, Cayman, Seychelles, Panama) — common in crypto, sometimes fine, sometimes not
- Stack misalignment between posting and engineering blog (suggests posting is generic or outdated)
- Job title or seniority changes between sources (LinkedIn vs careers page vs recruiter)

**Action:** investigate before applying. Look for patterns (one orange flag, ok; two or three, treat as red). Ask the user if they have additional context.

### Red flags — strong default to skip

Any of these on their own is usually enough. Combinations are unambiguous skips:

- **Salary paid in cryptocurrency** (USDT, BTC, ETH, etc.) — no tax compliance for most jurisdictions, no legal recourse, anti-money-laundering risk on the user's side
- **Pay-to-work**: any request for training fees, equipment fees, certification fees, "deposits", "bonds"
- **Request for credit card, bank routing, or full ID before a signed contract** — straight-up fraud pattern
- **Interview conducted via Telegram / WhatsApp / Signal** for a corporate role (legitimate companies use Zoom, Google Meet, Teams)
- **Corporate "recruiter" using gmail / yandex / outlook / proton** for a real-named established company (vs the company's own domain)
- **Contract in a different language than the work language, with no translation provided**
- **Extremely broad non-compete** (all of EU, 2+ years, all of "technology") — unenforceable in many jurisdictions but signals bad-faith terms
- **No legal entity in the user's country of residence** combined with employment (rather than B2B) framing — no recourse on disputes
- **Office address that's a virtual mailbox or shared workspace** for a company claiming substantial operations
- **Sanctioned jurisdictions as primary operations** — beyond legal risk, often paired with anti-AML structure
- **"Off the books" / cash-only / under-the-table** wage arrangements
- **Insisting on personally identifiable documents (passport, ID card scans) before any offer** — identity theft pattern
- **Recruiter refuses to disclose the end client name even after the user asks directly** — fishing for candidates rather than real role

**Action:** skip. Don't engage further. The user can decline politely (`references/recruiter-comms.md` § Declining) without explaining the red flag in detail.

## Pattern detection

The most useful signal is **multiple flags together**. Single flags are often false alarms; combinations rarely are.

Common combination patterns from real-world cases:

- **"Crypto + USDT + offshore + sanctioned-jurisdiction filter"**: a company asking you to receive salary in USDT, registered in BVI/Cayman, with a filter excluding sanctioned countries from applicants — this is a pattern of operating at the edge of regulations. Skip even if the role looks good.
- **"Vague posting + AI-generated language + typos + insecure recruiter web presence"**: signals an agency or recruiter that's mass-fishing rather than running a real search. Probably not malicious, but a sign that conditions will appear during interviews rather than upfront — energy cost is high.
- **"Big-tech logo + recruiter from gmail + Telegram interview ask"**: impersonation. Big companies don't recruit this way.
- **"Tight deadline + comp far above market + 'pay for training' or 'send your bank info to set up payroll' before contract"**: full scam pattern.

When you spot a combination, name the pattern explicitly in chat:

> "Three flags here that combine into a pattern: salary in USDT (red), BVI registration (yellow on its own), and Russian-language requirement undisclosed in the JD (orange). Together this is a 'operating at edge of regulations' pattern. My read: skip."

## JD authenticity signals

Separate question: is this *job posting* itself genuine, or padded / generated / fake?

**Signals the posting might be AI-generated or padded by a third party:**

- Typos that look like AI-generation artifacts ("Javascriptte" instead of "JavaScript", "fullstck", random capitalization)
- Duplicate bullets (same point appearing twice with slight rewording)
- Rhetorical "Do you want to be…?" questions targeting different candidate personas
- Generic responsibilities padded with corporate filler
- Missing concrete info: no client name (for an agency posting), no location, no contract type, no rate / salary, no duration
- Inconsistent vocabulary (uses "engineer" and "developer" and "specialist" interchangeably for the same role)
- Skills list that includes things contradictory to the role description

**Signals the recruiter / agency itself may be questionable:**

- LinkedIn profile shows no IT recruiting experience for an IT recruiting role
- HTTP-not-HTTPS link on their public profile in 2026 — small thing, but unjustifiable for an IT-adjacent professional
- Personal social media full of unrelated content (MLM, get-rich-quick) — signals not their primary focus
- Email signature uses a free email provider instead of an agency domain
- Reverse image search on profile photo finds it elsewhere

**Read of these signals:**

- AI-generated / padded JD doesn't automatically mean scam. Often it means: an agency got a thin brief from a real client and expanded it with AI without proofreading. The client is real; the process is sloppy. The cost to the user is mostly that conditions ("oh by the way, it's on-site twice a week, in another country") will surface during interviews rather than upfront.

- A questionable recruiter profile is a stronger signal. Real corporate recruiters care about their professional presence. If the recruiter's LinkedIn looks like an afterthought, the search itself probably is.

**Response pattern:** before sending a CV, ask direct questions:

```
Before sending my CV, could you confirm:
1. Who is the end client, or at least the sector / type of company?
2. Location — fully remote, hybrid <city>, or on-site?
3. Contract model — employment, B2B, or other?
4. Salary / rate range?
5. Expected project / contract duration?
6. Hiring process — how many rounds, any technical assessments?
```

If detailed answers come back → the client is real; the recruiter was just sloppy on the brief. Proceed.
If vague answers come back → fishing for candidates / no real client. Stop investing time.

## Practical heuristic before applying

Quick checks the user (or Claude on their behalf) can run in 5 minutes:

1. **Google the company.** Real companies have Trustpilot reviews, news mentions (not just press releases), industry chatter. If only PR articles exist, warning sign.
2. **Check the business register** in the company's claimed jurisdiction. When was it founded? Who are the directors? Most countries have free or cheap company registry lookups.
3. **LinkedIn search "Company name" + filter to past employees.** Is the tenure pattern healthy or is everyone leaving after 3–6 months?
4. **Glassdoor with focus on "management" and "compensation".** Product may be cool, but how are people treated and paid?
5. **Look up the recruiter / HR contact on LinkedIn.** If they don't have a profile, or it's brand new, or they have no relevant experience — flag.
6. **Ask about payment terms before the interview.** Currency, frequency, contract type. Avoidance = red flag.

For a senior user, this is cheap and very high signal. Five minutes of upfront research saves hours of wasted interview prep.

## Crypto / Web3 specific

The crypto / Web3 space has more variance than most sectors. Some companies are legitimate and well-run; others are scams or near-scams. Specific signals to weight:

- **Anonymous team** (developers known only by pseudonyms / handles) — common in DeFi but a real risk in employment context
- **Recently issued token used as part of compensation** — value is speculative; treat as 0 for floor-floor calculations
- **"Promised returns" framing** in marketing — both red flag for the company's regulatory standing and bad sign for the role
- **Audits absent or stale** on smart-contract-heavy products
- **Heavy reliance on "tokenomics" rather than revenue** for a company past the early stage
- **Founder team has been associated with previously rugged / failed projects**

A crypto company is not automatically a skip. Apply the same yellow/orange/red lens, and weight harder on the legal/structural items (jurisdiction, comp structure, recourse).

## Reporting back to the user

After running the analysis, give a clear verdict in chat:

> "Quick red-flag pass on `<posting>`:
> - Yellow: `<list>`
> - Orange: `<list>` — `<one-sentence interpretation>`
> - Red: `<list>` — `<one-sentence interpretation>`
>
> Pattern read: `<the combination, if any>`
>
> Recommendation: `<Apply / Proceed with these questions answered first / Skip>`."

If the verdict is "skip", and the user asks why, walk through it briefly. Some users will override and apply anyway — that's their call. The skill flagged the risks; the user decides.

If the verdict is "proceed with questions", offer to draft those questions (route to `references/recruiter-comms.md`).
