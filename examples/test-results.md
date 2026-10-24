# Test run: 3 sample projects

Checked on 2026-10-24. All numbers were fetched live in this run. Scores in Gate 2 are judgement calls based on the evidence listed.

Legend for "Community": ✓ = positive, specific HN comment found in the last 2 years · ✗ = searched, nothing positive found · — = not checked in this test run.

---

## Project 1: Terraform setup on Azure (Windows 11, VS Code, beginner)

### Core infrastructure as code

| # | Name | What it does here | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [Terraform AzureRM provider](https://github.com/hashicorp/terraform-provider-azurerm) | Lets Terraform create Azure resources | Excellent (4.8) | 5.0k ★, MPL-2.0, v5.5.0 on 2026-09-10, official HashiCorp | — |

Only 1 checked in this category (it is the only option for Terraform on Azure).

### Linting and security scanning

| # | Name | What it does here | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [Checkov](https://github.com/bridgecrewio/checkov) | Flags insecure Azure settings before deploy | Excellent (4.5) | 9.0k ★, Apache-2.0, 3.3.29 on 2026-10-13 | ✓ HN 2024-07 recommends it for Terraform security checks |
| 2 | [TFLint](https://github.com/terraform-linters/tflint) | Catches Terraform mistakes and bad Azure values | Very good (4.4) | 5.8k ★, MPL-2.0 (some files BUSL 1.1), v0.64.0 on 2026-07-17 | ✓ HN 2026-02 and 2025-10, praised as fast; one 2024 complaint about licence |

Only 2 passed the quality bar.

### VS Code extensions

| # | Name | What it does here | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [HashiCorp Terraform](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform) | Syntax highlighting, autocomplete, validation | Excellent (4.6) | 6.87M installs, 209 ratings, official vendor | — |

### MCP servers and Claude skills

| # | Name | What it does here | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [HashiCorp agent-skills](https://github.com/hashicorp/agent-skills) | Claude Code plugins for writing Terraform code, modules and tests | Very good (4.3) | 761 ★, MPL-2.0, v1.0.0 on 2026-08-04, official HashiCorp | — |
| 2 | [Terraform MCP server](https://github.com/hashicorp/terraform-mcp-server) | Gives Claude live Terraform Registry docs | Very good (4.2) | 1.5k ★, MPL-2.0, v1.2.0 on 2026-08-04, official HashiCorp | — |
| 3 | [Azure MCP server](https://github.com/microsoft/mcp) | Lets Claude query and manage your Azure resources | Very good (4.0) | 3.6k ★, MIT, listed in the [GitHub MCP registry](https://github.com/mcp/com.microsoft/azure); latest build is a 3.0.0 beta from 2026-07-31 | — |

### Rejected (notable)

- **Trivy** (38.1k ★): supply-chain compromise on 2026-03-19, with malicious v0.69.4 binaries and hijacked `trivy-action` tags ([Aqua advisory](https://www.aquasec.com/blog/trivy-supply-chain-attack-what-you-need-to-know), CVE-2026-33634). Safety scores 2, so it fails Gate 2.
- **Infracost** (12.5k ★): the numbers pass, but no positive, specific HN recommendation was found.
- **pre-commit-terraform** (3.8k ★): the numbers pass, but HN returned no results, so the community check fails.

---

## Project 2: Python web app (FastAPI)

| # | Name | Category | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [FastAPI](https://github.com/fastapi/fastapi) | Framework | Excellent (4.8) | 103.3k ★, MIT, 0.162.0 on 2026-10-23 | ✗ search hit unrelated "fast API" comments (see tuning) |
| 2 | [uv](https://github.com/astral-sh/uv) | Packages and environments | Excellent (4.7) | 89.3k ★, 0.12.8 on 2026-08-31 | ✓ HN 2025-11 |
| 3 | [Ruff](https://github.com/astral-sh/ruff) | Linter and formatter | Excellent (4.7) | 49.5k ★, 0.16.6 on 2026-09-03 | ✓ HN 2025-11 |
| 4 | [pytest](https://github.com/pytest-dev/pytest) | Testing | Excellent (4.6) | 14.5k ★, 9.1.1 on 2026-06-19 | — |
| 5 | [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) | VS Code | Excellent (4.6) | 242M installs, 631 ratings, Microsoft | — |
| 6 | [Ruff extension](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) | VS Code | Very good (4.4) | 4.84M installs, 55 ratings, official Astral | — |

---

## Project 3: AWS data pipeline

| # | Name | Category | Rating | Evidence | Community |
|---|---|---|---|---|---|
| 1 | [Terraform AWS provider](https://github.com/hashicorp/terraform-provider-aws) | Infrastructure as code | Excellent (4.8) | 11k ★, v6.58.0 on 2026-08-05 | — |
| 2 | [dbt-core](https://github.com/dbt-labs/dbt-core) | Transformations | Excellent (4.5) | 13.8k ★, v1.12.4 on 2026-09-08 | ✓ HN 2026-06 |
| 3 | [AWS SDK for pandas](https://github.com/aws/aws-sdk-pandas) | Python ↔ S3/Athena/Glue | Very good (4.3) | 4.1k ★, 3.17.1 on 2026-08-03 | — |
| 4 | [AWS SAM CLI](https://github.com/aws/aws-sam-cli) | Serverless (Lambda) deploys | Very good (4.2) | 6.7k ★, v1.166.2 on 2026-09-11 | — |
| 5 | [AWS MCP servers](https://github.com/awslabs/mcp) | MCP | Very good (4.3) | 9.7k ★, release on 2026-09-22, official AWS Labs | — |
| 6 | [AWS Toolkit](https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.aws-toolkit-vscode) | VS Code | Very good (4.2) | 5.21M installs, 73 ratings, official AWS | — |

**Rejected:** Great Expectations (11.9k ★, 1.24.1 on 2026-10-22). Recent HN mentions are only job-post skill lists, and the older threads describe a "love-hate" relationship, so the community check fails.

---

## What the test changed in the skill

1. **GitHub dates.** The repo's main page doesn't show commit dates when fetched. The skill now reads `/releases` instead. GitHub leaves out the year for dates in the current year.
2. **VS Code ratings.** The marketplace page doesn't expose the average rating, and official Azure extensions have only 8 to 19 ratings despite millions of installs. The rule now also accepts the vendor's official extension when it has 1M or more installs.
3. **Reddit.** Reddit is blocked from the research tools. The skill now uses the Hacker News search API as the main community source and Reddit when it can be reached.
4. **Name collisions.** A search for "checkov" returned Star Trek comments, and "fastapi" returned generic "fast API" ones. The skill now quotes the name and adds a topic word.
5. **Safety check.** A search for incidents and CVEs is now a required step. It's the reason Trivy (38k ★) was rejected.
6. **Vendor skills.** Official tool-vendor skill repos, such as HashiCorp's, now count the same as Anthropic's.
