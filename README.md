# GitHub Copilot — From Zero to Hero

A 2-hour hands-on workshop for **WeAreDevelopers World Congress 2026**.

Go from tab-completion to agentic Copilot: build a static site by *just asking*, then a Next.js app using a **Plan → Implement** workflow — all from the congress dataset.

👉 **Start here: [WORKSHOP.md](./WORKSHOP.md)**

Dataset template: <https://github.com/github-copilot-workshop/we-are-developers-2026-data>

## Workshop registration automation

The issue template asks attendees for the **Workshop secret word** and the registration workflow dispatches it to `we-are-devs-2026/workshop-automation` as `client_payload.workshop_secret_word`.

Configure the expected word in the private automation repository as the GitHub Actions secret `WORKSHOP_SECRET_WORD`. Use that exact name for the secret/environment variable; do not use `SECRET_WORD` or `secret_word`. This repository also needs `WORKSHOP_AUTOMATION_DISPATCH_TOKEN` so the workflow can send the `workshop-registration` repository dispatch event.
