# Personal Codex skills

Reusable personal workflows for Codex.

## Included skills

- `coding-coach`: learner-owned implementation, bounded explanations, live code review, test design, and project-local coaching history.

## Install on another PC

Authenticate Git with a GitHub account that can read this private repository. In Codex, ask:

> Use skill-installer to install coding-coach from https://github.com/luisivanhr/codex-skills/tree/main/coding-coach.

Alternatively, clone this repository and copy the complete skill folder. On Windows PowerShell:

```powershell
git clone https://github.com/luisivanhr/codex-skills.git
Set-Location codex-skills
$skillsDir = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $env:USERPROFILE '.codex\skills'
}
New-Item -ItemType Directory -Force -Path $skillsDir | Out-Null
$destination = Join-Path $skillsDir 'coding-coach'
if (Test-Path -LiteralPath $destination) {
    throw 'coding-coach already exists. Back it up and compare it before replacing.'
}
Copy-Item -LiteralPath '.\coding-coach' -Destination $destination -Recurse
```

Start a new Codex chat in your project and ask:

> Use $coding-coach to help me implement [feature]. Begin by agreeing on the deliverable, learning depth, and time boundary.

If the skill is not discovered, restart Codex.

## Updating

Edit skills in this repository, review the diff, commit, and push. On another PC, run `git pull --ff-only` inside its clone, then replace the installed skill folder with the updated complete folder after backing up any local edits. Pulling this repository alone does not update an installed copy. A fresh folder replacement also removes files retired from the workflow.

Keep project code, credentials, and `coaching_history.md` in their own projects. This repository contains reusable instructions only. Preserve each skill's `agents` and `references` directories when copying it.
