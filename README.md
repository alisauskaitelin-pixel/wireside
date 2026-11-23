# wireside

A live events website I run with a team of AI agents. You tell it what you like doing (comedy, board games, jazz, running, language exchanges..) and it tells you about the events in your city that match, in time to actually go. It covers The Hague, Amsterdam, Rotterdam, Hong Kong and Singapore.

Live at [wireside.app](https://wireside.app). You can see what it would send you without signing up.

I'm a marketer, not a developer. Every line of code was written by Claude agents in Claude Code. My job was the one a product lead has: deciding what it is, saying what's wrong with it, and being the only person who can make it go live.

---

## Where it stands (23 Nov 2026)

| | |
|---|---|
| Cities | 5 |
| Upcoming listings it knows about | 14,678 |
| Places & platforms it reads from | about 160 |
| Tagged releases to the live site since 12 Nov | 33 |
| Automated tests | 877 |
| Written quality reviews | 304 |
| Hosting cost | free plans only |

That's four weeks from the locked brief on 27 Oct.

---

## How the team is set up

Seven agent sessions, each owning one thing, and one hub that talks to me.

- **Product** keeps the board, writes the spec for every change & decides what's in scope.
- **App** builds the website and runs releases.
- **Quality** reviews every final file before anything ships, and checks the live site after.
- **Design** draws screens and tests layouts at every width from phone to wide screen.
- **Sources** finds the events, venue by venue, city by city.
- **Content** writes the words on the site & keeps the privacy page true to what the code does.
- **Go-to-market** drafts the posts and outreach I send myself.
- **The hub** relays my decisions word for word, checks what the others report before it reaches me, and keeps a ledger of every ask (about 140 rows so far) so nothing quietly disappears.

I only talk to the hub. The others talk to each other.

---

## The rules that made it work

Most of these came from something going wrong first.

**Quality passes the final file.** A "pass if you fix X" gets read again once X is fixed. Quality reads the exact version that will go live, and if anything changes after, it reads it again.

**Nothing goes live without my word.** I type "deploy" in the App agent's chat myself. No agent can take another agent's message as my approval, and no scheduled job can either.

**Checks on the live site only read.** Agents can open pages but never submit anything (a test that "just signs up once" leaves a real person in the database).

**Agents never see a key.** Passwords and tokens get pasted by me, straight into the place they go. When a setup needs a database password, the agents prepare everything around it and leave the last paste to me.

**Every number carries its denominator.** A report that says "most events work" comes back with a question. "51 of 262 fresh page loads failed" is the kind of line I can act on.

**The hub checks before it tells me.** When an agent says something is live, the hub loads the page itself first.

---

## One week, as an example

On a Saturday night Quality noticed that about 1 in 6 freshly built pages showed a bare Cloudflare error instead of the site. The site was going over the free plan's computing limit per page. App fixed it in two parts on the free plan (paying for a bigger plan was off the table), and Quality load-tested it: 1,187 fresh page loads with zero errors, where the old version started failing after about 33 minutes.

Then App's own logs showed the uncomfortable part - every one of those errors had come from our own test traffic. 0 of 1,004 real visits had hit it. So I had told myself, and the agents had told me, that visitors were affected when they weren't. The fix was still worth it (a real traffic spike would have done the same), but the agents corrected their records & so did I, and "measured on our own test load" became a line every report has to say out loud.

---

## What's not in this repo

The code. Wireside is one of the Labs products I build on Minds by Animoca Brands, so the code isn't mine to publish. What's here is how it's run, which is the part worth showing anyway.
