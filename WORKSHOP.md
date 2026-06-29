# 🚀 GitHub Copilot — From Zero to Hero

> WeAreDevelopers World Congress 2026 · Hands-on Workshop · **2 hours**

AI isn't just auto-completing lines of code anymore — it's changing how we architect, build, and ship. In this workshop you'll move beyond tab-completion and unlock the **agentic** power of GitHub Copilot: turn raw data and a spec into working applications by delegating the work to AI agents, then learn how to monitor, debug, and control them.

You'll build **two apps** from the same dataset — a static site by *just asking*, then a full Next.js app using a **Plan → Implement** workflow.

---

## 🎯 What you'll learn

- Create a project from a template and drive Copilot in **Agent mode** with the **Auto** model.
- Turn a one-line prompt into a working multi-page website.
- Watch the cost: **AI Credits** and the **Debug / Agent console**.
- See why **tab-completion & inline chat** still matter — but are no longer the main act.
- Use a grown-up workflow: **Plan first, implement second**, to build a Next.js app.

## 🧰 What we'll use

- A ready dataset: **385 sessions**, **589 speakers**, **73 workshops** from the congress.
- **VS Code** + GitHub Copilot (today's hands-on tool).
- GitHub Copilot **CLI** and the Copilot **app** — installed below, explored at the end.

## ⏱️ Agenda (10:30 – 12:30)

| Time | Part |
|------|------|
| 10:30 | Intro + setup (repo from template, clone) |
| 10:45 | **Part 1** — HTML site with Agent + Auto |
| 11:15 | AI Credits & Debug console, completion/inline chat |
| 11:35 | Commit & push |
| 11:45 | **Part 2** — Plan → Implement a Next.js app |
| 12:20 | Wrap-up + stretch goals |

---

# ✅ Prerequisites & installation

Set up **VS Code**, **GitHub Copilot**, and **Git** for the hands-on parts. Also install the Copilot **CLI** and **app** — we'll explore them in the final section.

> Don't have a GitHub Copilot subscription? A 30-day free trial is available at <https://github.com/features/copilot>.

<details>
<summary><b>1. Install VS Code</b> (macOS / Windows / Linux)</summary>

- **All platforms:** download from <https://code.visualstudio.com>.
- **macOS:** `brew install --cask visual-studio-code`
- **Windows:** `winget install Microsoft.VisualStudioCode`
- **Linux (Debian/Ubuntu):** `sudo snap install code --classic`

Verify: `code --version`
</details>

<details>
<summary><b>2. Install Git</b></summary>

- **macOS:** `brew install git` (or `xcode-select --install`)
- **Windows:** `winget install Git.Git`
- **Linux:** `sudo apt install git`

Verify: `git --version`
</details>

<details>
<summary><b>3. Enable GitHub Copilot in VS Code</b></summary>

1. Open VS Code → **Extensions** (`Ctrl/Cmd + Shift + X`).
2. Install **GitHub Copilot** and **GitHub Copilot Chat**.
3. Click **Sign in** and authorize your GitHub account.
4. Open Chat (`Ctrl/Cmd + Alt + I`) and confirm you can pick **Agent** mode with the **Auto** model.
</details>

<details>
<summary><b>4. Install the GitHub Copilot CLI</b></summary>

The CLI brings the agent to your terminal. **Requires Node.js ≥ 22 and npm ≥ 10.**

First install Node (skip if `node -v` already shows v22+):
- **macOS:** `brew install node`
- **Windows:** `winget install OpenJS.NodeJS.LTS`
- **Linux:** `sudo apt install nodejs npm` (or use [nvm](https://github.com/nvm-sh/nvm))

Then install Copilot CLI (same on all platforms):

```bash
npm install -g @github/copilot
```

> If your `~/.npmrc` has `ignore-scripts=true`, use: `npm_config_ignore_scripts=false npm install -g @github/copilot`

Run `copilot`, sign in with `/login`, then `/exit`. Verify: `copilot --version`.
Docs: <https://docs.github.com/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli>
</details>

<details>
<summary><b>5. Install the GitHub Copilot app</b></summary>

The desktop Copilot app runs the same agent outside the editor, with sessions and plan mode. We'll demo it at the end.

- **macOS / Windows:** download from <https://github.com/features/copilot> → **Download**, install, and sign in with your GitHub account.
- **Linux:** not yet available — use the **CLI** (step 4) instead.

Needs an active Copilot subscription (the same one used for VS Code).
</details>

---

# 🟢 Part 0 — Get the data

We start from a template repo containing only the congress data — no code yet.

### Step 1 · Create your private repo from the template

1. Open **<https://github.com/github-copilot-workshop/we-are-developers-2026-data>**.
2. Click **Use this template → Create a new repository**.
3. Name it (e.g. `wad-copilot-workshop`), set **Private**, create.

### Step 2 · Clone and open

```bash
git clone https://github.com/<your-username>/wad-copilot-workshop.git
cd wad-copilot-workshop
code .
```

Peek at `data/` — `sessions.json`, `speakers.json`, `workshops.json` (+ agenda, masterclasses, database).

---

# 🟡 Part 1 — Build a site by *just asking* (Agent + Auto)

No scaffolding, no boilerplate. Open Copilot Chat, pick **Agent** mode + **Auto** model, paste one prompt, and watch it build.

### Step 3 · Create a branch

```bash
git checkout -b feature/html-site
```

### Step 4 · The prompt

In VS Code: Chat panel → **Agent** → model **Auto** → paste:

<details>
<summary>💬 <b>Show the prompt — HTML site</b></summary>

```text
Build a simple static website (no framework, just HTML/CSS/JS) from the JSON in the data/ folder.

Create two pages:
1. index.html — a searchable, filterable list of all sessions from data/sessions.json. Each
   card shows the title, day, time range, stage, tags and speaker names. Add a search box and a
   filter by day (Wednesday/Thursday/Friday) and by tag.
2. speakers.html — a grid of all speakers from data/speakers.json with photo, name, title,
   company, and links to LinkedIn/GitHub/website. Add a search box by name or company.

Link the two pages with a shared nav bar. Load the JSON at runtime with fetch. Make it clean,
responsive, and fast. Put everything in a site/ folder. Then start a local server and verify it
loads with no console errors.
```
</details>

Let it run end-to-end. Accept edits, let it start a server, open the preview.

> 💡 **Auto** picks the best available model for each step; you stay focused on the goal, not the knobs.

---

# 💸 Part 2 — Watch cost & debug the agent

### AI Credits

Agentic requests use **premium requests / AI credits** that vary by model. See live usage at **<https://github.com/settings/billing>** (Copilot section) and pricing at **<https://docs.github.com/copilot/concepts/copilot-billing/about-premium-requests>**. Picking **Auto** is the cheapest path — Copilot routes to a right-sized model.

### Debug / Agent console

In VS Code: **View → Output → "GitHub Copilot"** (and the Chat thread itself) shows tool calls, terminal commands, files touched, and timing. Use it to see *exactly* what the agent did — and to stop or steer it.

---

# ⌨️ Part 3 — Yes, completion still exists (briefly)

Open `site/index.html`, start a comment like `<!-- footer with copyright -->`, and let **completion** finish the line. Or select markup, press `Ctrl/Cmd + I` for **inline chat**: *"make this button a primary color."*

> ⚠️ It works — but this is **not** how we work day-to-day anymore. We delegate, not nudge.

---

# 💾 Part 4 — Commit & push

```bash
git add .
git commit -m "Static sessions + speakers site (built with Copilot Agent)"
git push -u origin feature/html-site
```

No PR — just push the branch. Done with the quick win.

---

# 🔵 Part 5 — The pro workflow: Plan → Implement (Next.js)

Back to a clean slate and build something real: a **My Agenda** planner where attendees pick sessions and save them.

### Step 5 · Reset

```bash
git checkout main
git checkout -b feature/agenda-app
```

### Step 6 · First, **Plan**

Ask Copilot to plan before coding (use Plan mode, or just request a plan):

<details>
<summary>💬 <b>Show the prompt — Plan</b></summary>

```text
Plan a Next.js (App Router, TypeScript) app called "My Agenda" using the data in data/. Don't
write code yet — propose a plan: pages, components, data loading, and how a user picks sessions
and saves their personal agenda to browser localStorage. Keep it simple, no backend. Show me the
file structure and steps, then wait for my go-ahead.
```
</details>

Review the plan, tweak it, then approve.

### Step 7 · Then, **Implement**

<details>
<summary>💬 <b>Show the prompt — Implement</b></summary>

```text
Implement the approved plan. Scaffold a Next.js + TypeScript app. Load data/sessions.json and
data/speakers.json. Browse: searchable session list filterable by day and tag. Add/remove each
session to "My Agenda" with a button; persist selections in localStorage. A /my-agenda page lists
saved sessions grouped by day with total count, sorted by time, with a clear-all. Style it clean
and responsive. Run the dev server and verify add/remove/persist works with no console errors.
```
</details>

Watch the agent scaffold, install deps, edit files, and run `npm run dev`. Verify, then commit:

```bash
git add . && git commit -m "Next.js My Agenda app (Plan → Implement)" && git push -u origin feature/agenda-app
```

---

# 🏁 Wrap-up & stretch goals

You went **zero → hero**: a site from one prompt, then a real app via Plan → Implement, while keeping an eye on cost and the agent console.

**Stretch:** add speaker pages, export agenda as `.ics`, deploy to Vercel, or repeat Part 5 with the **Copilot CLI** / **app** instead of VS Code.

- Copilot docs: <https://docs.github.com/copilot>
- Copilot CLI: <https://docs.github.com/copilot/concepts/agents/about-copilot-cli>
- Dataset: <https://github.com/github-copilot-workshop/we-are-developers-2026-data>
