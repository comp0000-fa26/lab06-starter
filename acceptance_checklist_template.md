# Acceptance checklist — ClassPoll (self-assessment)

Tick a box only when you have **verified** the behaviour yourself against your
deployed app — not just "the code looks right". Each ticked box the TA can
independently verify is worth 1 mark (7 total).

- [ ] **AC1.** Creating a poll with valid input produces a URL of the form
      `/poll/<short-id>` where short-id is 6 alphanumeric chars.
- [ ] **AC2.** Creating a poll with <2 or >6 options is rejected with a clear error.
- [ ] **AC3.** Voting endpoint accepts one vote per browser session (cookie-based).
- [ ] **AC4.** Voting endpoint rejects a second vote from the same session with HTTP 409.
- [ ] **AC5.** The results page shows current tallies for each option.
- [ ] **AC6.** The results page auto-refreshes every 3 seconds (polling or SSE).
- [ ] **AC7.** The app is deployed at a public URL the TA can reach.

## Evidence
- Deploy URL: `https://________________________________`
- GitHub repo URL: `https://github.com/______________________`
- `GET /api/health` returns `{"ok": true}`: [ ] yes

## Notes for the TA (optional)
> If any box is unticked, say one sentence on what's missing and why — an honest
> "AC6 not done, ran out of time" is better than a tick you can't back up.
