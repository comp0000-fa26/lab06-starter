# ClassPoll — Product Requirements Document

## Overview
A single-purpose web app for running ad-hoc polls in class. One presenter
creates a poll; many students vote; everyone sees the results live.

## User stories
- As a presenter, I can create a poll with a question and 2–6 options.
- As a presenter, I get a short share URL I can show on screen.
- As a voter, I can open the share URL on my phone and vote once.
- As a voter, I see the live tally update after I vote.

## Acceptance criteria (the TA will check these)
- [ ] Creating a poll with valid input produces a URL of the form
      `/poll/<short-id>` where short-id is 6 alphanumeric chars.
- [ ] Creating a poll with <2 or >6 options is rejected with a clear error.
- [ ] Voting endpoint accepts one vote per browser session (cookie-based).
- [ ] Voting endpoint rejects a second vote from the same session with HTTP 409.
- [ ] The results page shows current tallies for each option.
- [ ] The results page auto-refreshes every 3 seconds (polling or SSE both OK).
- [ ] The app is deployed at a public URL the TA can reach.

## Out of scope
- User accounts, authentication.
- Persistence beyond 24 hours.
- Anti-cheat beyond the cookie check (we know cookies can be cleared — that's fine).

## Tech constraints
- Front-end and back-end must be in the same repo, deployable to Vercel
  serverless functions (10-second timeout) or Cloudflare Pages.
- No external database — use Vercel KV, Cloudflare D1, or in-memory
  with a clearly-stated 24h expiry.
- License: MIT.
