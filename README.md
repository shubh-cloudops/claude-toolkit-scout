# claude-toolkit-scout

A Claude skill that researches the web and recommends only **top-rated** tools, repos, VS Code extensions, Claude skills/plugins and MCP servers for any project, with a link and live evidence behind every number.

Example: describe "Terraform on Azure, beginner, Windows 11" and get back the top 3 picks per category, plus the well-known tools it rejected and why. In testing it rejected **Trivy** (38k ★) because of its March 2026 supply-chain compromise, which a simple star count would have missed.

## How it decides

Every candidate must pass two gates:

1. **Hard filter (numbers):** per-source minimums, such as ≥1,000 GitHub stars with a release in the last 6 months, or ≥4.5 rating from ≥50 G2 reviews. A number that can't be verified live fails.
2. **Judgement score (reviews):** 1–5 on fit, review sentiment, maintenance, docs and safety. To pass, the average must be ≥4.0 with no criterion below 3. A security incident caps safety at 2.

Picks are labelled **Excellent** (≥4.5) or **Very good** (4.0–4.4). Nothing else is shown, and lists are never padded.

| Design choice | Why |
|---|---|
| Two gates instead of one score | Numbers make it repeatable; the review read catches popular-but-risky tools |
| Every number needs a link from this run | Stops the model from quoting stale or invented stats |
| Hacker News API for community signal | Reddit is often blocked to AI web tools; the HN Algolia API is open |
| Single `SKILL.md` file | Works unchanged in both Claude Code and claude.ai |

## Install

**Claude Code (Windows, PowerShell):**

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills\project-toolkit-scout"
Invoke-WebRequest https://raw.githubusercontent.com/shubh-cloudops/claude-toolkit-scout/main/skill/SKILL.md -OutFile "$HOME\.claude\skills\project-toolkit-scout\SKILL.md"
```

Expected result: running `/skills` in Claude Code lists `project-toolkit-scout`.

**claude.ai:** go to Settings → Capabilities → Skills, choose Upload skill, and upload a zip of the `skill/` folder.

## Use

Ask Claude: *"Find the best tools for my project: a Python FastAPI app deployed to Azure. I'm a beginner on Windows 11."*

## Example output

See [examples/test-results.md](examples/test-results.md) for a full run on 3 sample projects (Terraform on Azure, Python web app, AWS data pipeline), including what the test changed in the skill.

## Limitations

- Ratings change, so every report is dated.
- Judgement scores come from Claude reading the evidence. They are a reasoned opinion, not ground truth.
- Some sources (Reddit, the VS Code Marketplace average rating) may not be readable from AI web tools. The skill falls back as described in `SKILL.md`.

## Licence

MIT
