---
name: project-toolkit-scout
description: Use when the user describes a project and wants the best tools, plugins, repos, MCP servers and Claude skills for it, researched live on the web and filtered to top-rated picks only.
---

# Project Toolkit Scout

Research the web for the tools a project needs and return only picks that are verifiably rated excellent. Quality over quantity: a short honest list beats a long padded one.

## Step 1: Understand the project

Collect these before researching. If any are missing, ask them all in one message, as multiple choice with a recommended option and "Other":

1. What the project does (one or two sentences).
2. Tech stack or cloud, if already chosen (e.g. Azure, AWS, Python, Terraform).
3. Operating system and editor (e.g. Windows 11 + VS Code).
4. Skill level: beginner / intermediate / advanced.
5. Budget: free only / free tier first / paid is fine.

## Step 2: Pick the categories

Choose only the categories this project actually needs, from:

- Core tools and frameworks
- Open-source repos (starters, templates, examples)
- Editor extensions (VS Code)
- Claude skills and plugins
- MCP servers
- Packages / libraries
- Infrastructure as code (Terraform providers/modules)
- CI/CD and testing
- SaaS services

## Step 3: Find candidates

For each category, run several web searches and collect 5-10 candidates. Good places to look:

- GitHub (repo pages, topics, "awesome-" lists)
- VS Code Marketplace
- Anthropic's official skills and plugin repos; the official MCP registry
- npmjs.com, pypistats.org, Terraform Registry
- G2 / Capterra for SaaS
- Hacker News comments via `https://hn.algolia.com/api/v1/search?query="<name>"%20<topic>&tags=comment&hitsPerPage=10` (works where Reddit is blocked)
- Reddit threads from the last 2 years, when reachable

Blog "top 10" lists may be used to *find* candidates, never as evidence.

## Step 4: Gate 1, hard filter

Fetch each candidate's source page and check its row. It must meet every number. If a number cannot be verified from a page fetched in this run, the candidate fails.

How to read the numbers reliably:

- **GitHub activity:** the repo's main page often hides commit dates. Fetch `github.com/<owner>/<repo>/releases` instead and use the latest non-pre-release. GitHub omits the year for dates in the current year, so "04 Aug" means this year.
- **VS Code ratings:** the marketplace page often shows installs and rating count but not the average. Use installs, rating count and publisher; if the extension has a GitHub repo, check its releases for the update date.

| Category | Source | Minimum to pass |
|---|---|---|
| GitHub repo / open-source tool | GitHub repo page + /releases | >=1,000 stars, commit or release in last 6 months, not archived, has a licence |
| VS Code extension | VS Code Marketplace | >=100k installs, updated in last 12 months, AND either rating >=4.5 from >=100 ratings OR the official extension of the tool's vendor with >=1M installs |
| Claude skill or plugin | Anthropic repo/marketplace or its GitHub repo | Official Anthropic or tool-vendor source (e.g. hashicorp/agent-skills), OR >=500 stars and commit in last 6 months |
| MCP server | MCP registry + GitHub repo | In the registry or vendor-published, plus >=500 stars and commit in last 6 months |
| Package | npmjs.com / pypistats.org | >=100k weekly downloads (npm) or >=1M monthly (PyPI), release in last 12 months |
| Terraform provider / module | Terraform Registry | Official or Partner tier, OR >=1M downloads, release in last 12 months |
| SaaS / paid product | G2 or Capterra | >=4.5 from >=50 reviews, and a free tier or trial |

Community check (all categories): at least one positive, specific recommendation on Hacker News or Reddit in the last 2 years, and no well-upvoted thread calling it broken, abandoned or unsafe. Put the name in quotes and add a topic word (e.g. `"checkov" terraform`), and ignore hits about something else with the same name.

Safety check (all categories): search `<name> security incident` and `<name> CVE` for the last 2 years. A supply-chain compromise or unpatched critical CVE caps the Safety score at 2, which means it fails Gate 2.

## Step 5: Gate 2, judgement score

For candidates that passed Gate 1, read reviews, open issues and community threads. Score 1-5:

| Criterion | 5 means |
|---|---|
| Fit | Solves this project's exact need at the user's skill level |
| Review sentiment | Reviewers consistently call it reliable and easy to use |
| Maintenance | Issues get answered, recent releases, no unresolved breaking bugs |
| Docs | Clear getting-started guide, works on the user's OS |
| Safety | No known security incidents, sensible permissions, reputable publisher |

Pass = average >=4.0 and no criterion below 3.

Rating label: **Excellent** if average >=4.5, **Very good** if 4.0-4.4. Nothing else is shown.

## Step 6: Output

Show the **top 3 per category**, ranked by judgement average. If fewer than 3 pass, show what passed and write "Only N passed the quality bar." Never pad.

Use this format for each category:

```
### <Category>

| # | Name | What it does for this project | Rating | Evidence |
|---|------|-------------------------------|--------|----------|
| 1 | [Name](link) | One line | Excellent (4.6) | 12.3k stars, last commit 2026-10-01; Marketplace 4.7 (2.1k ratings) |

Why #1: one line.
```

End with:

1. **Start here**: the 3-5 picks to install first, in order.
2. **Rejected (notable)**: up to 5 well-known names that failed, with the reason (e.g. "archived", "3.9 rating").
3. **Checked on**: today's date. Note that ratings change over time.

## Rules

- Every number needs a link and must come from this run, never from memory.
- Prefer official sources over third-party summaries.
- Flag anything paid with its price and whether a free tier exists.
- Never suggest tools that need secrets hard-coded; mention the secret store to use instead.
