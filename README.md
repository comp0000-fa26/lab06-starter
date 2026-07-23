# Lab 6 — Starter (ClassPoll)

Vibe-coding a full-stack web app from a PRD. See the lab handout
(`lab-06.pdf`) for the full walkthrough, rubric, and rules.

**There is no app code in this starter — that is the point.** You build ClassPoll
yourself by prompting an agentic IDE (Cursor) against the PRD.

## Before the Lab
You need to create a `Vercel` account before the lab starts. Please sign up at [https://vercel.com/signup](https://vercel.com/signup).



## Files
- `PRD.md` — the ClassPoll product requirements doc. **Read it first** 
- `iteration_log_template.md` — copy to `iteration_log.md` and fill in as you
  build. Graded as heavily as the app; the honesty premium is real.
- `acceptance_checklist_template.md` — copy to `acceptance_checklist.md` and tick
  only the criteria you have verified yourself.
- `.gitignore` — Node/Next.js + Vercel; keeps `node_modules/`, `.next/`, and
  every `.env*` out of git. **Never commit a `.env` / `.env.local`.**

## The rules
1. **First 20 minutes: prompts only.** No hand-editing any file. You prompt, read
   the diff, accept/reject, prompt again. This forces you to prompt *precisely*.
2. After that, manual edits are allowed — but try prompting first and only fall
   back to a manual edit when prompting fails. Log every fallback and why.
3. Pick **one** failing acceptance criterion at a time and fix just that one
   without breaking the others.

## How to start (in an empty sibling directory, not this one)
Create an empty folder named `xxxxxxxx_lab06` on your Desktop (Replace xxxxxxxx to your SID). Then, open the folder with `Cursor`, copy `PRD.md` into that folder, and prompt the agent with something like:

> Read the PRD at PRD.md and create the initial scaffold. Use Next.js 14 App
> Router with serverless functions for the API, Vercel KV for storage, and
> Tailwind for styling. Initialise the git repo and commit each milestone.

The agent will build the class poll for you. You may not hand-edit any file. You prompt, you read the diff, you **accept** or **reject**, and you prompt again in the **first 20 minutes**.

**After 20 minutes** the typical state is a Next.js app that creates polls and votes via API routes, but with at least one acceptance-criteria violation — commonly it doesn’t **reject the second vote**, **doesn’t auto-refresh**, or the share URL is `/poll?id=...` **instead of** `/poll/<short-id>`.

## Vercel KV
Follow the steps to create the Vercel KV for the class poll application:

1. Go to [https://vercel.com/login](https://vercel.com/login) and login your account.
2. Select `Storage` on the left bar
3. Click `Create Database`
4. Click `Upstash` and choose `Upstash for Redis`
5. Click `create`
6. Choose `Free` for the `Installation Plans`

## Deploy + verify
Run it in Terminal with `Command Prompt`:

```bash
npm i -g vercel
vercel login          
vercel                # follow the interactive deploy
```

The deploy processes will ask you something like this:

- Which project? `Create a new project`
- Name? `lab06example` (Replace lab06example to name that you want)
- Customize settings? `N`
- Customize advanced settings? N

After deployment, it will display something like this:
```
✓ Created         <project_name>/lab06example
  Inspect         https://vercel.com/<project_name>/lab06example/E8u23XsoVxjKAGdjNiYfzTCFrztQ
  Production      https://lab06example-asdccvvdd-<project_name>.v  Production      https://lab06example-asdccvvdd-<project_name>.vercel.app
▲ Aliased         https://lab06example.vercel.app
```
You can get the URL of your deployed class poll in `Aliased`.

### Before opening the deployment URL
Go back to `Vercel Storage` and click `Connect to Project`.
1. Select your project.
2. Check all boxes under `Environments`.
![Env Setting](/images/env.png)

3. Click `Connect Project`.
4. Run `vercel env pull .env.development.local` in the terminal to make the latest environment variables available to your project locally.

Since it takes time to deploy the app with `Vercel`, it is suggested that you run the class poll locally while still implementing the application by using:
```bash
npm run dev
```
**Usually, it should be running at [http://localhost:3000/](http://localhost:3000/)**

## Diagnose and Fix one specific gap
Pick one acceptance criterion still failing and work the agent to fix **just that one** without breaking the others. Students who try to fix everything at once usually break the working parts.Manual editing is now permitted, but keep prompting first and fall back to manual edits only when prompting fails. The `iteration_log.md` template forces you to note this:

e.g.,
```
## Fix: vote endpoint not rejecting duplicates
| t  | Action          | Outcome                                        |
|----|-----------------|------------------------------------------------|
| 0  | prompt          | Asked agent to add cookie check                |
| 1  | prompt          | Agent added cookie but used wrong cookie name  |
| 2  | manual edit     | Renamed cookie to match what /poll/[id] reads  |
| 3  | prompt          | Asked agent to add 409 response                |     
| 4  | test            | Both tests pass; criterion met                 |
```

**Copy `iteration_log_template.md` to `yyyyyyyy_lab06` folder and rename it to `iteration_log.md`**

## After fixing the problems
Run `vercel --prod` to deploy the class poll to production.

You can check if the deployment URL responds correctly by running:
```bash
curl.exe -s https://lab06example.vercel.app/api/health   # expect: {"ok": true}
```

## Deliverables (submit via Moodle by the following Friday)
1. **GitHub repo URL** — public, MIT licence.
2. **Deploy URL** — Vercel or Cloudflare, reachable from the public internet
   (also put it in `deploy_url.txt` for the autograder).
3. **`iteration_log.md`** — honest build timeline.
4. **`acceptance_checklist.md`** — your self-assessment.
