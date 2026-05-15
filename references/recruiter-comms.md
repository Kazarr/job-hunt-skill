# Recruiter communication

Two flows: **parsing incoming** (recruiter just emailed, what are they really asking?) and **drafting outgoing** (follow-up, rejection reply, scheduling, declining gracefully). Both share the same voice: senior, direct, no fluff, no premature commitments.

## When to invoke

- User pastes a recruiter email and asks for help interpreting / replying
- User says "I haven't heard back from X in a week, should I follow up?"
- User got a rejection email and wants to draft a reply
- User got an offer or scheduling request and needs to respond
- User is composing a cold outreach to a recruiter / hiring manager (e.g. LinkedIn DM after a broken application form)

## Parsing incoming recruiter messages

When the user pastes a recruiter email, before drafting anything, extract:

```markdown
## Incoming parse: <date> from <name>

**Role / opportunity (if any):**
**Company (end client, if knowable):**
**Recruiter / agency:**
**Comp signal (if any):**
**Timeline / urgency:**
**Exclusivity ask (any 'work only with us' language?):**
**Specific asks of the user:**
**What they're really asking (read between the lines):**
**Likely next step they're aiming for:**
```

Save this to the relevant `applications/<slug>/notes.md` (under a `## Communications` section) if it relates to an existing application. If it's a brand-new opportunity, save the email to `applications/<new-slug>/posting.md` (or `recruiter-intro.md` if there's no formal posting yet) and create the application folder.

### Three-tier staffing model awareness

Many roles come through a chain: **head hunter → staffing agency → end client**. Each takes a margin. When the recruiter mentions multiple party names, identify which tier they sit in:

- **Head hunter / external recruiter** sourcing for the agency or end client — they get a commission on placement. Often anchors comp low because their margin sits on top of what the agency / client pays.
- **Staffing agency / consultancy** — places contractors at end clients. Has its own margin.
- **End client** — where the work actually happens.

If the chain is opaque, ask the user: "Who's the actual end client, and who's between you and them?" This matters for rate negotiation and for understanding why a recruiter behaves the way they do.

### Reading recruiter behavior

Common patterns to surface for the user:

- **Anchoring low** ("budget is X-Y, we're proposing the middle"): the middle is rarely real — there's usually room above.
- **False urgency** ("we need a decision by tomorrow"): real opportunities can wait a day. Push back politely.
- **Exclusivity ask** ("represent you exclusively for this client"): standard for senior contracting. Usually OK if scoped to one client. Not OK as a blanket "all opportunities through us".
- **Vague on the client** ("a leading fintech company"): can mean either NDA / early-stage representation, or fishing for candidates with no real role. Ask for the client name before investing time.
- **Pressuring on rate before interview**: don't commit. "Happy to discuss specifics after the interview when we both know it's a fit" is the right move.
- **Asking for current comp**: in most jurisdictions, the user can deflect. "I'd rather anchor on what the role is worth than what I'm currently paid."

## Drafting outgoing messages

All outgoing drafts go to chat by default. The user reviews, edits, copies into their email / LinkedIn / whatever channel. Save to `applications/<slug>/notes.md` only if the user wants a record.

### General voice rules

- **Concise.** A follow-up email is 3 sentences, not 3 paragraphs. A rejection reply is 2.
- **No filler softeners that reduce urgency.** "Happy to wait", "no pressure", "whenever convenient" — these tell the recipient deprioritizing this is fine. Cut them unless the user genuinely wants to deprioritize.
- **No sycophancy.** "I just wanted to say what an honor it would be…" — cut.
- **No premature commitment.** Don't say yes to rate / start date / exclusivity before there's a real offer on the table.
- **One clear ask per message.** If you need a status update and to schedule a call, that's two messages.
- **Mirror the recruiter's register.** If they're formal, lean slightly formal. If they're casual, you can be casual back.

### Follow-up after silence (week+ since last contact)

When to send: 5–7 working days of silence after a stage where they said they'd follow up. Earlier is needy; later is being forgotten.

Pattern:
```
Hi <Name>,

Following up on our <call / message> on <date> — you mentioned <specific
thing they said>. Have you had a chance to <the thing>?

<Optional: one sentence of new context if relevant, e.g. "I've moved
forward with one other process so wanted to check timing.">

Best,
<User>
```

Pitfalls to avoid:
- "Just checking in" — too vague, doesn't reference the specific commitment they made
- "Hope you're well" — fine but optional; cut if the message is otherwise short
- "No rush" / "happy to wait" — reduces urgency
- "Sorry to bother you" — apologizing for following up on something they committed to is the wrong frame

### Reply to a rejection

When to send: same or next day. Keep it short. The relationship may be worth more than this specific role — many recruiters remember well-handled rejections.

Pattern (1–2 sentences):
```
Hi <Name>,

Thanks for letting me know. Appreciate the consideration — if anything
relevant comes up, please keep me in mind.

Best,
<User>
```

Variations:
- If the rejection cited a specific gap and the user wants feedback: "Out of curiosity — was it primarily `<X>` that was the deciding factor, or were there other concerns? Useful for my own calibration." (Only if the user wants this answered honestly.)
- If a referral / strong relationship is in play: slightly warmer, but still under 4 sentences.

Pitfalls:
- Long letters about how disappointed you are
- Asking them to reconsider (sometimes works; usually doesn't and burns goodwill)
- Sarcasm or veiled criticism of the process
- "I disagree with this decision and here's why" — even if true

### Scheduling reply

When the recruiter offers a time / asks for availability:

If their proposal works:
```
<Time> works — sending a calendar invite. <Link or platform> for the call?
```

If it doesn't work, offer 2–3 specific alternatives, not "let me know when works":
```
Can't do <their time> — would <alt 1>, <alt 2>, or <alt 3> work? All
times <user's time zone>.
```

Including the time zone matters. Many cross-border interviews die on this.

### Declining an opportunity

When the user is going to pass on a role (rate too low, bad fit, location wrong, etc.):

Pattern:
```
Hi <Name>,

Thanks for the introduction. After looking at it, I don't think this is
the right fit — <one-line reason, optional>. If you have <kind of thing
the user does want> come up, I'd be happy to take a look.

Best,
<User>
```

If the reason is delicate (rate, red flag): be brief and honest without being lecturing. "The rate doesn't work for me on this one" is fine. "The USDT salary is a non-starter" is true but burns more bridges than needed — "this isn't the right fit, but please keep me in mind for `<X>`" is enough.

### Cold outreach (LinkedIn DM, etc.)

The export's NRB pattern is the model — when an application channel breaks, reach out directly.

Pattern (LinkedIn DM, ~3 sentences):
```
Hi <Name>, I'm a <senior role> currently between roles, looking for
<specific kind of thing>. I tried <company>'s <channel> but ran into <issue>.
Would you be open to a quick chat about potential matching roles?
```

Pitfalls:
- Generic openers ("Hope this finds you well")
- Pitching yourself before asking for their time
- Walls of text in a DM

### Exclusivity replies

When asked to represent exclusively for a specific opportunity:
> "Happy to work exclusively with you on `<this client>` for the duration of this process. If other opportunities through other channels come up, I'll handle those separately."

When asked to represent exclusively across all opportunities (overreach):
> "Exclusive on `<this specific opportunity>` works for me. I'd rather keep other channels open in general, but I'll be transparent if there's any overlap."

### Rate-related replies

Route through `references/rate-negotiation.md` — that's the strategy reference. This file just handles the wording once the strategy is decided.

## What to capture in `notes.md`

After any meaningful outgoing or incoming message, add to `applications/<slug>/notes.md`:

- Update the status frontmatter if it changed (`drafting → applied`, `applied → recruiter-screen`, etc.)
- Add a chronological log line: `YYYY-MM-DD — <what happened>`
- If the message contains long-lived facts (recruiter's name, agency, the end client, comp range mentioned), add them to the `## Contacts` or `## Application context` sections

Don't ask the user to update `notes.md` — do it automatically when a message is drafted or parsed.
