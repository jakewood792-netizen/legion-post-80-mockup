# American Legion Post 80 — Rebuild Notes

Client: Butler-Harmon American Legion Post 80, New Richmond, WI. Boss approached
Jake directly on 2026-09-04 to redesign wilegionpost80.org. Deal is being worked
out; no signed agreement or pricing yet as of 2026-09-05.

Current live site is Wix, stale since 2023, thin/broken in several places — see
the "what's wrong with the current site" list below before pitching. Plan is a
full rebuild (static HTML/CSS, same stack as the other client mockups), moving
off Wix rather than patching it — pending final confirmation with the client
since it means canceling their Wix plan and cutting over DNS at launch.

## What's wrong with the current site (audited 2026-09-05)
- Footer copyright still says 2023 — site hasn't been meaningfully updated since.
- Homepage hero image is stuck on a blurry lazy-load placeholder that never resolves.
- Events page is a wall of unstructured text (bar hours + one bingo date), not a
  real calendar — includes stray leftover Wix formatting artifacts.
- Hall Rental page is nearly empty — no photos, no pricing, no capacity, just
  "please complete the form." This is likely their best revenue-generating page
  and it's the weakest one.
- Nav URLs are messy Wix auto-slugs (e.g. Hall Rental lives at
  `/hall-rental-new-richmond-wi`, not something predictable).
- No self-serve way for the post to update anything themselves — likely why it's
  gone stale.

## What this mockup uses as REAL content (pulled from the live site, not made up)
- Address: 1260 Wall Street, New Richmond, WI 54017
- Phone: (715) 246-4980
- Email: butlerharmonpost80@gmail.com
- Bar hours: Fri 3pm-close, Wed 6pm-close, Thu 6pm-close (+ all reg-season Packers games)
- Red Friday shirt / happy-hour promo detail
- "Also known as Butler-Harmon Post 80"
- Programs blurb: veterans assistance/advocacy, youth mentoring, families/children in need
- Membership blurb: camaraderie, discounts, American Legion Magazine

## What's still a placeholder — needed from the client before this ships
- [ ] Real photos: hall interior, exterior, bar area, kitchen, an event in progress
      (Hall Rental gallery + homepage hero currently use styled placeholder boxes)
- [ ] Hall Rental: actual capacity, rental rate, what's included, deposit policy
- [ ] Membership: current eligibility requirements + dues amount
- [ ] Programs: specifics behind each of the three program areas (what does
      "veterans assistance" concretely offer, etc.)
- [ ] Real Facebook page URL (placeholder `facebook.com/` link used everywhere for now)
- [ ] Decision: which Google account owns the Events calendar — use their existing
      butlerharmonpost80@gmail.com, or set up something new? See conversation notes
      — whichever account owns it should belong to the post, not to Jake personally.
      Once decided, swap the `.calendar-placeholder` block on events.html for the
      real Google Calendar embed iframe.
- [ ] Both forms (Hall Rental inquiry, Contact) are static HTML right now — need a
      real submission backend before launch (e.g. Formspree, or a simple
      Supabase table + email notification like the GC Storage site uses).

## Architecture decisions made
- Self-serve Events calendar via embedded Google Calendar (not a custom admin
  panel) — chosen because the post's likely volunteer staff turnover favors a
  tool people may already know over a custom system only Jake understands.
  Same approach earmarked for News once that's fleshed out.
- Static HTML/CSS/JS, same pattern as Beauje/Scott Freer/T.L. Sinz mockups —
  deploy to GitHub Pages for the pitch, then a real host once approved.
