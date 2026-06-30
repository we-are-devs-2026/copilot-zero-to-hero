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
| --- | --- |
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
3. Name it (e.g. `we-are-devs-2026/<your-username>-wad-copilot-workshop`), set **Private**, create.

### Step 2 · Clone and open

```bash
git clone https://github.com/we-are-devs-2026/<your-username>-wad-copilot-workshop.git
cd <your-username>-wad-copilot-workshop
code .
```

Peek at `data/` — `sessions.json`, `speakers.json`, `workshops.json` (+ agenda, masterclasses, database).

---

# 🟡 Part 1 — Build a site by *just asking* (Agent + Auto)

No scaffolding, no boilerplate. Open Copilot Chat, pick **Agent** mode + **Auto** model, paste one prompt, and watch it build.

This website should list all the speakers order by name, and should run as a pure static HTML site. (no dependency on JSON file itself)

### Step 3 · Create a branch

```bash
git checkout -b feature/html-site
```

### Step 4 · The prompt

In VS Code: Chat panel → **Agent** → model **Auto** → Enter your prompt.

<details>
<summary>💬 <b>sample prompt</b></summary>

```text
Build a simple static website (no framework, just HTML/CSS/JS) that list all the speakers, located in the data/speakers.json file.
This page should be opened directly in the browser, and should not depend on the JSON file itself, and do not need any server. The page should be responsive and clean.
Put the page in ./site/
```

</details>


Let it run end-to-end. Accept edits, Copilot will open VSCode browser, you can also open it in your own browser. When done, verify the site works by opening `site/index.html` in a browser.


> 💡 **Auto** picks the best available model for each step; you stay focused on the goal, not the knobs.

---

# 💸 Part 2 — Watch cost & debug the agent


Github Copilot is consuming AI Credits from a pool provided by your organization. You can find information in the [documentation](https://docs.github.com/en/copilot/concepts/billing/usage-based-billing-for-organizations-and-enterprises#what-are-github-ai-credits).


You can see the "cost" of you interaction using different approaches in VSCode:

- Move you mouse at the bottom of the conversation: (see 27.4 credits in the example below)
   ![Credits](./images/001-credits.png)

- At the bottom of the Copilot Chat, click on the "Session Info" button, you will see the context and the Copilot Usage (AIC)

   ![Session Info](./images/003-session-info.png)


- Open the **Agent Debug Logs** window, simply go in the Command Palette (Ctrl/Cmd + Shift + P) and search for "Agent Debug Logs", you will see the number of tokens but more importantly the Copilot Usage (AIC)
   ![Agent Debug Logs](./images/002-debug-agent.png)


You can find information about Optimization of AI Credit in the VSCode Documentation:

- [Optimize AI credit usage in VS Code](https://code.visualstudio.com/docs/agents/guides/optimize-usage)




---

# ⌨️ Part 3 — Yes, completion still exists 

Open `site/index.html`, start a comment like `<!-- footer with copyright -->`, and let **completion** finish the line. 

Or  press `Ctrl/Cmd + I` for **inline chat**: *"Add a footer with Copyright information and create with love by copilot (emoji)."*

> ⚠️ It works — but this is **not** how we work day-to-day anymore. We delegate using agents, not line-by-line completion. Completion is still useful for small edits, but the agent is the main act.

---

# 💾 Part 4 — Commit & push

```bash
git add .
git commit -m "Static sessions + speakers site (built with Copilot Agent)"
git push -u origin feature/html-site
```

Note if you are in VSCode or other IDEs, you can also use the **Source Control** panel to stage, commit, and push,

Also something nice in VSCode Terminal, once you have type `git add .`, Copilot is proposing the next action with a sparkle icon, see image below:

![Git add propose next action](./images/004-generate-commit.png)


---

# 🔵 Part 5 — The pro workflow: Plan → Implement

Back to a clean slate and build something real: a **My Agenda** planner where attendees pick sessions and save them.

### Step 5 · Reset

```bash
git checkout main
git checkout -b feature/agenda-app
```

### Step 6 · First, **Plan**

Ask Copilot to plan before coding (use Plan mode, or just request a plan).

Start a new conversation in Copilot Chat, pick **Plan** mode, and enter your prompt.

The goal here is to create a full application (Next.js + TypeScript) that allows users to browse sessions, filter them, and save their personal agenda in localStorage. The app will be simple, with no backend. (This to help you understand the power of planning before implementing, and make it easier to test and deploy).

<details>
<summary>💬 <b>Show the prompt — Plan</b></summary>

```text
I want to create a new application with the latest version of Next.js and Shadcn/ui. 
- I want this application to allow me to view all the sessions and speakers from the WeAreDevelopers World Congress 2026 dataset (data/sessions.json and data/speakers.json).
- I want to be able to filter the sessions by day and tag, and search for sessions by title or speaker name.
- I want to be able to add/remove sessions to/from "My Agenda" and persist my selections in localStorage.

Ask question if you need more information.
```
</details>


### Step 7 · Then, **Implement**

Review the plan, tweak it, then approve, and implement it in **Autopilot** mode


#### Step 7a · Another session another tasks

One of the nice things about working with Agents, is that you can have multiple sessions, each with its own plan and tasks. You can also have multiple agents working on different tasks at the same time.

Start another session in GitHub Copilot Chat, pick **Agents** mode, and ask GitHub Copilot to update the Readme with an ERD diagram of the data model.

Something like :

> Can you add a new ERD in the readme file based on the content of data 

You can add the `data` folder to the context of the session, and GitHub Copilot will be able to read the data and generate an ERD diagram based on it.

---

# 🟣 Part 6 — Working with GitHub Copilot CLI

Once you have installed the CLI, open a terminal in VS Code or on your system, and make sure you are in the root of your project.

You can now interact with GitHub Copilot directly from your terminal:

- Press `Tab` to switch between **Session**, **Issues**, **PR**, and **Gists**.
- In **Session**, you can enter specific commands using `/`, for example `/model`.

Select the model and choose **Auto**.

Then ask GitHub Copilot to work on 2 tasks in parallel in the same session using background agents with the `/fleet` command:

```text
/fleet Can you add support for multiple themes light, dark, and 3 other one, and add a search form in the speaker form to search by name and company
```

You can follow the tasks using the `/tasks` command.

You can look at your consumption and context using the commands: `/usage` & `/context`, and simply use `/help` to see all the commands available.

## Managing CLI sessions

When you change topic, it is important to start with a clear context so Copilot has a clear understanding of the ask.

With the CLI, you have several options:

- Start a new terminal and run `copilot` again.
- Clear the current session with `/clear`.
- Start or switch sessions with `/session`.
- If you exit Copilot and want to return to an old session, run:

```bash
copilot --resume
```

## Permissions and sandbox

By default, Copilot asks before running tools that can modify files or execute commands. For a trusted workshop project, you can choose to allow more autonomy:

- Use `/allow-all` inside a session to enable all permissions for tools, paths, and URLs.
- Start Copilot with `copilot --allow-all` or `copilot --yolo` to enable all permissions from the beginning.
- Use `/sandbox enable` to run the session with additional isolation and restrict access to your filesystem, network, and system capabilities.

> ⚠️ Only use `--allow-all`, `--yolo`, or `/allow-all` in a project you trust. These options reduce confirmation prompts, but also give Copilot more freedom to read, edit, and run commands.



## Review your changes locally

A good pattern is to review your changes in your local environment before opening a PR. This is also useful when your source code is not hosted on GitHub, which is possible with Copilot CLI.

The CLI includes 2 specific commands for this:

- `/review` to run a code review agent on your local changes.
- `/security-review` to run a security-focused review on your local changes.

You can run them one by one, or use subagents with `/fleet` to run multiple reviews in parallel, even with different models:

```text
/fleet Can you do a code review with GPT-5.3-Codex, and a security-review with Claude Sonnet 4.6 on my changes
```

In the image below you can see the 2 agents running with 2 different models:

![](./images/005-cli-code-review.png)