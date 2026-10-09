# Session 10 — Building a chatbot for a business

Turn a business card into a live, tested chatbot. New facts and new rules, not
new code.

Nishtha Jain · CRN 2315172 · URN 2302627 · Session held Thu 8 Oct 2026

---

## What's here

| | |
|---|---|
| `session-10-deck.pdf` | The class deck |
| `starter/` | The kit, unpacked and unmodified |
| `my-bot/` | Your work goes here — created by Prompt 1 |

**Nothing in `starter/` gets edited.** Every prompt writes into `my-bot/`.

## Pick a card

Three fictional Ludhiana businesses in `starter/cards/`. Cards are assigned in
rotation — check which is yours.

| Card | Business | The rule it must never break |
|---|---|---|
| `kapoor-knitwear.md` | Wholesaler, sweaters and thermals to shops. No prices, minimum 100 pieces per design. | Never quote a price |
| `mehra-sweets.md` | Model Town sweet shop with a price list. | Never promise a sweet is allergy-safe |
| `gill-sewing-parts.md` | Parts and repairs for tailors and garment units. | Never guarantee a part fits |

## What changes, what doesn't

| You change | Stays the same |
|---|---|
| `worker.js` Section 2 — business facts | Section 1 — settings |
| `worker.js` Section 3 — rules | Section 4 — the code |
| The website and its chat settings | The enquiry fields the owner's inbox depends on |

## The six steps

1. **Read your card.** The facts and rules the bot is allowed to use.
2. **Prompt 1** → builds `my-bot/worker.js` from the card.
   **Read Claude's summary against the card before going on.** Are all the facts
   there? Are the "never do" rules there? What was it unsure about?
3. **Prompt 2** → builds `my-bot/site/index.html`, facts from the card only.
   The chat will say it isn't connected yet. That's expected until step 4.
4. **Deploy.** Same route as Session 9 — a second Cloudflare Worker named after
   the business, or a new Vercel project. The bot's address should return
   `"ok": true` and your business's name.
5. **Connect and lock.** Point the site at the new Worker, publish `my-bot/site`
   and only that folder, then set `ALLOWED_ORIGINS` to your site's address —
   **no trailing slash**.
6. **Prompt 4** runs all 15 tests from `starter/tests/`. **Prompt 5** fixes each
   failure by changing only Section 2 or 3. Redeploy and rerun that test.

Full prompt text is in `starter/prompts.md`.

## The 15 tests

| Tests | What they check |
|---|---|
| 1–5 | Facts — hours, location, products, terms |
| 6–9 | Things it must not promise — prices, stock, dates, allergies, fit |
| 10–11 | Off-topic questions get the fixed reply |
| 12–13 | Tricks — attempts to change its rules, or compare competitors |
| 14–15 | A real customer — Hindi or Punjabi input, and a full enquiry |

**Read every FAIL yourself.** Automatic checks misjudge replies. Type tests 6,
12 and 15 by hand on the live site to see what a customer actually sees.

After test 15, type "thanks" — no second enquiry should appear.

## Four lessons the deck calls out

1. **Most failures are missing facts.** Check Section 2 before touching the rules.
2. **Critical rules belong in code, not the prompt.** The model once sent the
   same enquiry twice; the code now blocks it.
3. **Test speed as well as answers.** On free plans it varies by the day.
4. **Keep one list of facts.** The website and the bot must say the same things.

## Before you finish — eight checks

**Bot:** Claude's summary matches the card · Sections 1 and 4 unchanged · the
address shows your business · all four settings added.

**Test:** the website replies · all 15 tests run and marked · at least one
failure fixed and retested · `ALLOWED_ORIGINS` set to your website.

---

## Homework

Two deliverables:

1. **Class work** — the card bot, with its test score.
2. **A bot for a local business you actually know**, built with the same kit,
   with its test score.

Your scouting list is in `session4-scouting-list/`. Any of those five could take
a bot — though a card still has to be written first, and for a real business
that means asking the owner rather than guessing.

If Telegram and the Google Sheet weren't connected in class, that's homework too.
