# Rate and compensation negotiation

Compensation discussions show up at three points: (1) recruiter screen ("what are you looking for?"), (2) hiring manager round (sometimes), (3) after the loop, when an offer is being shaped. The principles are the same; the leverage shifts.

## When to invoke

- "What rate should I ask for?"
- "They offered X — is it fair?"
- Recruiter asked for comp expectations and the user is composing a reply
- The user is going B2B vs employment and needs to convert numbers
- Offer in hand, user wants to negotiate up
- User is comparing two offers

## Read this first

Read `profile.md` § Compensation expectations and § Identity before doing anything. The user's jurisdiction, currency, contract preference, and walk-away floor are all in there. If any are missing, ask the user once and write them back to `profile.md` — don't re-derive next session.

## The four numbers

Before any rate conversation, the user should have four numbers in mind:

1. **Target**: the number they'd happily accept. Optimistic-realistic. Reflects market for this role at this seniority in this region.
2. **Stretch**: ~10–15% above target. The number to anchor at when asked first.
3. **Floor**: the number below which it's a no. Walk-away.
4. **Current**: what they're making now (or last contract). For their own internal calibration only — usually not disclosed.

If `profile.md` only has one number, ask the user to extend it: "You said EUR 5500/month. What's your stretch? What's your walk-away?"

## Pre-interview: don't commit

The recruiter screen often asks "what are you looking for?" before the user has any real information about the role. Don't commit to a number then. Standard moves:

**Deflect to "after we know it's a fit":**
> "Happy to discuss specifics once we both know this is the right role. Broadly I'm in the `<range>` ballpark for senior `<role>` in `<region>`, but the specific number depends on what's actually involved."

**Give a range, anchor high:**
> "Based on what I've seen for senior `<role>` at companies your size in `<region>`, I'm looking in the `<stretch> – <stretch + 20%>` range. Open to discussing the full package once we know more."

**If they push for a single number:**
> "If you need a single number for screening, `<stretch>` is the middle of where I'd land — but that's calibrated on a typical loop and standard package. Happy to refine once we know specifics."

What to avoid in pre-interview:
- Giving your current salary. ("I'd rather anchor on what the role is worth than what I'm currently paid.")
- Giving the floor. (You're disclosing the lowest you'd accept — guarantees the offer comes in there or just above.)
- Apologizing for the range. (Don't say "I know that might be high, but…".)
- Negotiating against yourself. (Don't volunteer concessions before they ask.)

## Recruiter margin awareness

In a multi-tier setup (head hunter → agency → client), the recruiter's compensation depends on placing the user *at the lowest rate the user will accept*. The recruiter's anchor is almost always lower than the client's actual budget.

When the recruiter says "the budget is X-Y, we're proposing the middle":
- The middle is rarely the real budget ceiling.
- The agency / client has likely told the recruiter "see if you can place them at X, we'll go to Y if needed".
- Pushing back at the middle and holding at stretch usually has room.

For B2B contracting with an agency intermediary:
- The agency's margin is often 15–25% on top of what they bill the client.
- "We can't go above day rate X" sometimes means "our margin shrinks above X". Worth probing.
- If the user has a direct relationship option (or the agency relationship is loose), more leverage.

This isn't adversarial framing — agencies do real work and deserve a margin. It's just calibration so the user isn't anchored against an artificial ceiling.

## B2B vs employment conversion

Different jurisdictions have very different math. Read `profile.md` for the user's jurisdiction. Common conversions:

### Slovakia (živnosť → employment, EUR)
- Employee gross 5500/month ≈ 65–70k/year total employer cost
- Equivalent B2B day rate: ~300–350/day at ~220 working days/year
- Big factor: živnosť has paušálne výdavky (60% flat deduction up to a cap) — significantly lowers tax base
- Net difference at this level: ~1000+ EUR/month favoring B2B (after social + health + tax)

### Czech Republic (OSVČ → employment)
- Similar structure to Slovakia
- 60% paušál cap, then tax + social

### Poland (B2B / JDG → UoP / employment, PLN)
- B2B 19% flat tax (Polski Ład changed details — verify current rules)
- ZUS social contributions much lower on B2B than on employment
- Net difference can be 30–40% at senior level

### Germany (Selbstständig → Angestellt)
- Self-employed pays own KV (health) — significant
- Tax: progressive, similar
- VAT (Umsatzsteuer): adds 19% on top of invoices but is passed through
- Less universally favorable to B2B than CZ/SK/PL

### UK (Contractor / Ltd → Employee)
- IR35 status matters enormously — inside-IR35 contract erodes most of the advantage
- Outside IR35 + Ltd company: still favorable but margins compressed
- Day rates: typical senior tech £500–700/day London inside-IR35, can be more outside

### US (1099 / W-2)
- 1099 contractor pays self-employment tax (~15.3% on top of income tax)
- No employer-paid healthcare, 401k match, FICA
- Day rates need a significant premium to match a salaried package after benefits

### Other jurisdictions
Don't guess. Ask the user, or note: "I don't have reliable conversion math for `<country>`. Roughly what's the after-tax difference between employment and contracting where you are?"

## Anchoring strategy

When the user gives a range:
- **Top of range = stretch**, not target. Recruiters typically meet you at the middle of what you say.
- **Bottom of range ≥ target**, not floor. Don't include the floor in the public range.

When anchoring high:
- Pair the number with a reason. "Based on `<X>` data points / `<comp tool>` for senior `<role>` at companies in this size band in `<region>`" lands better than a number with no story.
- Don't apologize. "I might be on the higher end, but…" is negotiating against yourself.

When the recruiter pushes back:
- Don't drop immediately. "What does the rest of the package look like?" stalls usefully.
- Drop in small increments. If you anchored at stretch and they're at target, meeting at target+stretch/2 is fine. Don't move to target on first push.
- Get clarity on what they're saying no to: rate? total comp? specific component (equity, bonus, base)?

## Reading the offer

When an offer comes in, surface everything before the user accepts:

```markdown
## Offer parse: <company> — <date>

- Base / day rate / annual:
- Bonus (target %, last year actual %):
- Equity (type, grant, vest, refresh policy):
- Sign-on (cliff? clawback?):
- Vacation / PTO:
- Benefits (health, pension, learning budget, equipment):
- Notice period both ways:
- Working hours / on-call expectations:
- Remote / hybrid / onsite:
- Start date:
- Probation period and terms:
- IP / non-compete / non-solicit clauses:
- For B2B: payment terms (NET 30/60?), invoicing cadence, expense policy
- Compared to user's target/stretch/floor:
- Compared to other offers / market:
```

If the user doesn't have the full info, list what's missing and tell them to ask before deciding.

## Negotiation moves after offer

The strongest move is **stating a number and a reason**, not asking "is there flexibility?".

- "Based on `<market data>` and that I'm bringing `<X>` directly applicable experience, I'd be comfortable signing at `<higher number>`."
- "If you can move the base to `<X>` and refresh the equity in year 2, I'm in."
- "Two things stand out as off-market: `<Y>` and `<Z>`. If we can fix those I'll sign."

What recruiters / hiring managers can usually move:
- Base salary or day rate
- Sign-on bonus (one-time, doesn't break their salary band logic)
- Equity refresh
- Start date
- PTO

What's usually harder to move:
- Title (sometimes — at the band edges)
- Bonus target % (often standardized)
- Notice period (often standardized)
- Benefits structure (almost never)

## Walking away

If the offer is at or below floor and they won't move:
- Don't accept and then keep looking — burns the relationship if they find out, and bad for your own focus.
- Decline cleanly: "Appreciate the offer. I'm not able to make it work at this level. If anything changes on `<X>`, would be happy to revisit."
- Keep the door open without negotiating against yourself.

## After the conversation

Update the application's `notes.md`:
- Status frontmatter: `negotiating` if mid-discussion, `offer` once concrete, `accepted` / `declined` when resolved
- Log line with the actual numbers discussed
- Any agreed next step

If the user accepted, ask: "Want me to mark the other open applications as `withdrawn`?" Don't auto-update other folders — confirm first.

## What to NEVER do

- Lie about competing offers. Recruiters check.
- Disclose another offer's company name. ("I have another offer in the same band" is fine. "Stripe offered me X" is not.)
- Accept verbally with "I'll sign tomorrow" then keep negotiating. Once you've verbally committed at a number, that's your number.
- Negotiate after signing. Renegotiation requests post-signature read as bad faith.
