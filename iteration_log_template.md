# Iteration log — ClassPoll

> This log is graded as heavily as the app. It is a timeline of how you actually
> built ClassPoll with an agentic IDE: every prompt, every diff you accepted or
> rejected, every time you took over manually, and every time you started over.
>
> **The honesty premium is real.** A log full of "prompt → prompt → done" with no
> friction at all reads as fiction and forfeits the premium (3 marks). A log that
> documents a struggle and then resolves it earns it in full. The TA spot-checks
> ~20% of logs against your actual `git log` and IDE session transcripts.

## How to fill this in
- Add one section per chunk of work (initial scaffold, then one section per
  acceptance criterion you fixed).
- In each section, use the table: `t` is a step counter, `Action` is one of
  `prompt` / `manual edit` / `test` / `revert` / `restart`, `Outcome` is what
  actually happened (including failures).
- Note explicitly when prompting failed and you fell back to a manual edit, and
  why prompting wasn't enough.

---

## Scaffold: initial build (agent-only, first 20 minutes)

| t  | Action          | Outcome                                        |
|----|-----------------|------------------------------------------------|
| 0  | prompt          |                                                |
| 1  | prompt          |                                                |
| 2  |                 |                                                |

---

## Fix: <acceptance criterion you worked on>

| t  | Action          | Outcome                                        |
|----|-----------------|------------------------------------------------|
| 0  | prompt          | Asked agent to ...                             |
| 1  | prompt          | Agent did ... but ...                          |
| 2  | manual edit     | I changed ... because prompting kept ...       |
| 3  | test            | Criterion met / still failing because ...      |

---

## Reflection (3–5 sentences)
- Where did prompting work well, and where did you have to take over manually?
- What is the one thing you would prompt differently next time?
