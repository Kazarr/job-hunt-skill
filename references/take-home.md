# Take-home challenges

A take-home is the most leveraged part of most loops. A strong take-home turns a borderline candidate into a hire; a weak one ends the process even when the live interviews were good. The work is half technical, half presentation — and the presentation side is what most candidates underweight.

## When to invoke

- User says "I got a take-home", "they gave me a coding challenge", "they want me to build X"
- User has a take-home in progress and wants help on strategy, structure, or specific decisions
- User has finished a take-home and wants a review before submitting

## Output

Strategy notes go to `applications/<slug>/take-home.md`. The actual code lives wherever the user does their work (their own repo, a sandbox, wherever) — **not** in this skill's folder. Don't copy code into the skill repo unless the user explicitly asks for it to live there.

## Step 1: Read the prompt carefully — before opening an editor

This is the first senior-vs-junior fork in the road. Juniors start coding immediately. Seniors spend 20–40 minutes reading, planning, and noting questions.

What to extract from the prompt:

```markdown
# Take-home: <role> at <company>

## Brief
<paste the prompt>

## Scope
- Hard requirements (must do):
- Stretch goals (nice to have):
- Constraints (time, stack, libraries forbidden, etc.):
- Submission format (zip / repo link / live deploy):
- Deadline:

## What they're really evaluating
<read between the lines — see § What they're really evaluating below>

## Open questions for the company
<things to ask before starting>

## Plan
- Time budget breakdown:
- Architecture decisions:
- What I'm explicitly NOT doing and why:

## Risk list
<things that could eat the budget>
```

Save this **before** writing a single line of code. The plan is a deliverable, not a private artifact — it shows the reviewer the user thought before doing.

## What they're really evaluating

The prompt asks for X. The reviewer is grading on more than X:

| Surface evaluation | What it really measures |
|---|---|
| "Build a CRUD app" | Can the user organize code at all? Do they understand layering? |
| "Implement search" | Do they understand the actual algorithmic / UX trade-offs, or just call a library? |
| "Build a form with validation" | Do they know real validation patterns (client + server, async, accessibility)? |
| "Production-ready" | Do they know what production-ready means? (Error handling, logging, observability, deployment story.) |
| "Pick any stack" | Do they pick a stack that fits the problem, or whatever they used last? |
| "Time-boxed at 2-3 hours" | Can they prioritize ruthlessly? Or do they try to do everything and ship nothing well? |
| "Use AI tools as you would normally" | Do they know what to delegate to AI and what to own? (See § AI usage discipline.) |

When planning, write down the implicit evaluation criteria you can infer. They're more important than the explicit ones.

## Step 2: Ask before coding

If anything in the prompt is genuinely unclear, **ask the company before starting**. Asking 1–2 well-chosen questions is a positive signal at senior level — it shows the user clarifies scope rather than assuming. Drowning the recruiter in 15 questions is not.

Good questions:
- "Is `<specific feature>` in scope or stretch?"
- "Are there constraints on `<library / framework>` I should know about?"
- "If I run over time, do you prefer I submit partial-with-strong-tests, or attempt everything?"

Bad questions:
- "What stack should I use?" (Usually answered in the prompt or open by design.)
- "Can you give me hints?"
- Anything answered by reading the prompt twice.

## Step 3: Time allocation

For a 2.5-hour task, a realistic breakdown:

| Block | Time | Activity |
|---|---|---|
| Plan | 0–20 min | Read prompt, write plan, list questions |
| Scaffold | 20–40 min | Project init, dependencies, basic structure — fast path |
| Core feature 1 | 40–90 min | The biggest piece of real value |
| Core feature 2 | 90–120 min | The second biggest |
| Polish | 120–140 min | Error handling, loading states, one meaningful test, README |
| Final pass | 140–150 min | Commit history, README check, submission |

For longer prompts (full weekend, multi-day), the same proportions roughly hold: ~10% planning, ~20% scaffold, ~50% core features, ~15% polish, ~5% submission prep.

Universal rules:
- **Don't try to do everything.** Pick the must-have, ship it well, explicitly defer the rest in the README.
- **Stop coding 15 minutes before submission.** Use those minutes to write the README and check the commit history.
- **No "I'll fix this in the next pass."** If it's broken at submission, it counts as broken.

## Step 4: Commit discipline

Commits are read. They show how the user thinks.

Good commit messages on a take-home:
- `initial scaffold` (the first commit, plain)
- `add User model + repository` (one concept per commit)
- `implement cart add/remove with NgRx store`
- `add Luhn validation on card number`
- `handle empty-cart edge case`
- `cleanup: remove unused imports`

Bad commit messages:
- `wip`
- `fix`
- `update`
- `final` (especially "final final v2")
- A single giant commit at the end with everything

Commit cadence: aim for ~5–15 commits across the task. One per meaningful unit of work. Don't manufacture commits — but don't stuff a day's work into one either.

## Step 5: The README — non-negotiable

A take-home without a README is a half-finished submission. The README is where the user shows they thought, made trade-offs, used AI deliberately, and would do the next thing if they had time.

Required sections:

```markdown
# <Project>

Take-home for <company>, submitted <date>.

## Setup
<exact commands to run locally — assume the reviewer has the language toolchain but nothing else>

## Architectural decisions
- <decision 1>: chose X because Y; trade-off: Z
- <decision 2>: ...

## Trade-offs and what I prioritized
- I chose to spend time on <X> and <Y> rather than <Z> because <reason>
- Specifically NOT in this submission: <list>
- If I had another <hour / day>, I'd: <list>

## AI usage
<honest log of where AI helped and what I directed vs accepted — see § AI usage discipline>

## Testing
<what's tested, what isn't, why>

## Open questions
<things I would have asked the team in a real context>
```

Optional but often appreciated:
- A short architecture diagram (text or ascii)
- Performance notes (e.g. "n+1 query risk in /orders endpoint, not optimized in this submission")
- Security notes (especially for any task with user input or auth — see § Security gotchas)

## Step 6: AI usage discipline

Most modern take-homes either explicitly invite AI tools or implicitly assume them. Using AI is fine; **using AI without direction is not**.

The rule: **you direct, AI implements. The decisions are yours.**

What's fine to delegate to AI:
- Project scaffolding (`init`, package install, config files)
- Boilerplate (basic component templates, simple CRUD endpoints, mock data)
- Translating from your spec into syntax (you tell it the design; it writes the code)
- Test scaffolds (you tell it what to test; AI generates the structure)
- README structure

What you must own:
- Architectural decisions (folder structure, layering, state management approach)
- Domain modeling (entities, relationships, invariants)
- Key business logic (the actual algorithm / validation / orchestration)
- Anything the prompt is specifically evaluating

In the README:

> ## AI usage
>
> I used Claude Code throughout for scaffolding and boilerplate. Specifically:
> - Initial Angular + NgRx scaffold (AI-generated, reviewed)
> - Mock product / cart fixtures (AI-generated)
> - Form-field templates (AI-generated, then customized for Luhn validation logic)
> - README structure
>
> I owned all architectural decisions (folder structure, where state lives,
> the cart→checkout data flow), domain modeling (Cart, LineItem, CardDetails
> shape), and the validation logic itself. I can defend every line.

This kind of disclosure is a positive signal at senior level. Hiding AI use that's obvious in the code reads worse than declaring it.

## Step 7: Testing strategy

**Tests on trivial code are noise.** Tests on real logic are signal.

Test:
- Selectors / queries that combine, filter, transform
- Reducers / handlers that do non-trivial logic (dedup, sort, merge, derive state)
- Utility functions, pure transformations
- Effects / side-effects that have real orchestration (retry/backoff, debounce, sequential calls with shared state)
- Edge cases that real users would hit (empty input, large input, malformed input)

Don't test:
- Trivial selectors (`state => state.users`)
- Trivial reducers (`return { ...state, loading: true }`)
- Library wrappers (Angular's HttpClient, React Query) — you're testing the library, not your code
- Generated boilerplate

If the task has very little testable logic ("build a simple form" where the logic is mostly orchestration):

> In the README:
> "I didn't add unit tests because the application logic here is mostly
> orchestration — most files are presentational components or thin reducers.
> In a real codebase I'd add E2E tests for the key user flows (cart → checkout)
> and unit tests for pure transformation logic. Happy to discuss testing
> strategy in a follow-up."

That's a senior signal, not a weakness. A wall of trivial tests is the weakness.

## Step 8: Common domain gotchas

Recognize the domain of the take-home and check for the standard pitfalls.

### Payments / cart / checkout
- **Card data should never touch your backend in production.** Use tokenization (Stripe Elements, Adyen Drop-in, etc.). For a take-home with a card form, plain inputs are fine, but call this out in the README: *"In production I would integrate Stripe Elements / equivalent so card input stays in a sandboxed iframe and our servers only ever see a token. This keeps the system outside PCI DSS scope for cardholder data."*
- Idempotency on the order-creation endpoint
- Show the user what they're being charged before they click

**Card form — checklist of senior signals to ship (every item is small, every item is judged).**

Validation logic:
- [ ] Luhn algorithm on card number (10–15 lines, pure function, unit-testable)
- [ ] Expiry MM/YY parse + reject past dates + reject month > 12
- [ ] CVV length matches brand (3 normally, 4 for Amex)
- [ ] Disable submit until form valid
- [ ] Loading / disabled state on submit while in flight

HTML attributes (these are the "real-world senior" tells — recruiters scan for them):
- [ ] `autocomplete="cc-number"` on the card number input
- [ ] `autocomplete="cc-name"` on the cardholder name
- [ ] `autocomplete="cc-exp"` on the expiry
- [ ] `autocomplete="cc-csc"` on the CVV
- [ ] `inputmode="numeric"` on numeric fields (card number, expiry, CVV) — surfaces the numeric mobile keyboard
- [ ] No `autocomplete` on the CVV beyond `cc-csc` — never persist
- [ ] Don't mask the card number with `type="password"` — the user wants to see what they typed

Accessibility (basic table stakes):
- [ ] Real `<label for=>` for every input (no placeholder-as-label)
- [ ] Inline error messages with `aria-describedby` linking input → error
- [ ] Errors announced via `aria-live="polite"` region

Security hygiene:
- [ ] Never log card numbers / CVV (search the code before submitting)
- [ ] Never persist card data to localStorage / sessionStorage / state stores
- [ ] HTTPS only (default in production; mention in README if local dev is HTTP)

Mention this list in the README's "Architectural decisions" section to make clear it was deliberate.

### Auth
- Never log passwords or tokens
- Hash passwords (bcrypt / argon2, never MD5/SHA1)
- JWT vs session: tradeoffs, not religion
- CSRF protection for cookie-based auth
- Rate limiting on login
- Don't reveal whether an email exists in the system on login failure ("invalid credentials", not "user not found")

### Search / list views
- Pagination, not "load all 10,000 records"
- Debounce on search input
- Empty state, loading state, error state
- Sorting / filtering: clear UI on what's applied
- Accessibility on the input (label, keyboard nav)

### Forms (any)
- Server-side validation in addition to client-side
- Show field-level errors near the field
- Disable submit during in-flight request
- Confirm/discard on navigate-away with unsaved changes (where relevant)

### Data / pipeline tasks
- Idempotency of the pipeline (can it re-run safely?)
- Error handling: skip, retry, dead-letter?
- Schema evolution: what if the input format changes?
- Tests on real edge data, not just happy path

### Frontend specifically
- Mobile keyboard hints (`inputmode`, `autocomplete`)
- Accessibility basics (labels, alt text, keyboard nav, focus management)
- Loading skeletons, not just spinners on slow paths
- Cumulative Layout Shift on async content
- Browser back behavior on stateful pages

## Step 9: Final pass before submitting

15-minute checklist:

- [ ] README has all required sections, and they're honest
- [ ] All commits have meaningful messages
- [ ] `npm install && npm start` (or equivalent) runs from a clean clone — actually test this
- [ ] No commented-out code or `TODO` debris
- [ ] No secrets / API keys in the repo
- [ ] Sensitive logging removed
- [ ] What's broken is acknowledged in README, not hidden
- [ ] Submission format matches what they asked for (zip / link / branch)
- [ ] Submission email / message is short and includes the link

## After submitting

Log to `applications/<slug>/notes.md`:
- Date submitted
- Time spent
- What you'd change if you had another hour (note: do this honestly — useful for next take-home)

Update status frontmatter to whatever comes next (typically `technical-screen` or back to `applied` pending review).
