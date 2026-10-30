# Technology inventory

Reviewed: 2026-07-20. This is a historical snapshot. See the 2026-10-29 correction below for current scope and update procedures.

## Scope and result

The AJ01 product is a content and configuration scaffold. It has no identified application runtime, product package manifest, dependency lockfile, or application build script. The separate shared `.agents/skills/` workspace contains code and manifests outside the product scope.

The inventory below distinguishes technologies evidenced by the repository from technologies that were checked and are not currently used. A version marked `not pinned` means the repository uses the format or platform but does not declare an implementation version.

## Technologies in use

| Technology | Current version in this solution | Latest stable version checked | Evidence and update path |
|---|---:|---:|---|
| Git | `2.55.0.windows.2` in the current local checkout | `2.55.0.windows.3` | Repository history and local version-control workflow. Upgrade the developer installation; Dependabot cannot update a workstation-installed Git binary. |
| Markdown | Not pinned. Documents use Markdown syntax. | CommonMark `0.31.2` | `README.md`, `AGENTS.md`, and project documentation. Markdown has no project lockfile here. |
| YAML | Not pinned. `gpt_manifest.yaml` uses YAML; GitHub Actions workflow files will also use YAML. | YAML `1.2.2` | `gpt_manifest.yaml` and the planned `.github/dependabot.yml`. |
| GitHub repository hosting | Platform service, no repository version | Continuously hosted service | `origin` points to GitHub and the repository identity is documented in `AGENTS.md`. |
| Custom GPT workflow | Platform workflow, no local version | Continuously hosted OpenAI platform | README documents manual Custom GPT creation and Knowledge upload. This repository does not contain the live GPT implementation. |

## Technologies checked but not currently used

| Technology | Repository finding |
|---|---|
| TypeScript | No product dependency or compiler configuration identified. |
| JavaScript | No product application or product Node package manifest identified. The separate skills workspace contains code. |
| Python | No Python application or Python project metadata. The repository contains copied skill-support scripts under `.agents/`, but they are repository tooling content, not part of the GPT-AJ01 solution runtime. |
| Node.js, npm, pnpm, Yarn | No product package manifest or lockfile identified. Separate skills contain package manifests. |
| Vite | No Vite configuration or package dependency. |
| Tailwind CSS | No Tailwind configuration, stylesheet, or package dependency. |
| React or Next.js | No application source or package dependency. |
| Docker | No Dockerfile or container configuration. |
| GitHub Actions | No workflow existed at review start. The dependency-update configuration added with this review enables automated tracking for future workflow action references. |

## Findings

1. There are no application dependencies to upgrade today.
2. Git for Windows is one patch release behind the latest stable release checked on 2026-07-20.
3. The repository does not pin Markdown or YAML parser versions because it stores documents and configuration rather than executing a parser locally.
4. When an application layer is added, its manifest and lockfile must be committed and its ecosystem and location configured for Dependabot. Runtime versions may require separate tracking.

## Sources checked

- [Git for Windows releases](https://github.com/git-for-windows/git/releases)
- [CommonMark current specification](https://spec.commonmark.org/current/)
- [YAML 1.2.2 specification](https://yaml.org/spec/1.2.2/)
- [GitHub Actions workflow documentation](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
- [Renovate GitHub Action](https://github.com/renovatebot/github-action)

## Current correction and maintenance procedure

Reviewed: 2026-10-29. The scope is AJ01 product content in this standalone repository, not the separate shared `.agents/skills/` workspace, FoundRy, Replit, or external live services. New capability development is routed to FoundRy. The manifest's `1.0.0` is product metadata, not a technology version.

The workstation uses Git for Windows `2.56.0.windows.3`. The [latest stable release checked](https://github.com/git-for-windows/git/releases/tag/v2.56.0.windows.4) is `2.56.0.windows.4`, which includes a security fix. Git is not pinned by the project and is maintained on the workstation. [CommonMark](https://spec.commonmark.org/) lists `0.31.2`; [YAML](https://yaml.org/spec/1.2.2/) lists `1.2.2`. The repository does not pin parsers or assert conformance to either specification. GitHub and Custom GPT are provider-managed services without a project-pinned version.

TypeScript, JavaScript, Python, Node.js, Vite, Tailwind, React, and Docker are not evidenced as product dependencies. Their installed project versions therefore cannot be compared. The separate skills workspace contains Python and JavaScript-related material and seven tracked `package.json` files. Those are outside the product audit under the owner's scope decision.

The committed Dependabot policy schedules weekly GitHub Actions checks. No product workflows are currently present. The npm and pip examples are comments, not active monitoring. A policy alone does not prove a hosted check ran or that an update was adopted.

When a product dependency is introduced:

1. Commit its manifest and lockfile in the canonical development repository. Record runtime requirements and add appropriate build and regression checks.
2. Add a Dependabot entry for each ecosystem and manifest directory, following the [GitHub configuration guide](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/configure-version-updates). Apply it in FoundRy if that is the actual dependency home; this repository's policy does not cover other repositories.
3. Once the configuration reaches the default branch, check the repository's Dependabot status, investigate errors, and confirm a successful check. No successful hosted run was verified for this audit.
4. Review update pull requests and compatibility notes, run applicable checks, and merge after review. Dependabot proposes updates; it does not guarantee compatibility or automatic adoption.
5. Review workstation tools, unpinned runtimes, platform services, and format specifications separately. Dependabot does not update installed Git or a hosted Custom GPT.

This is a dated inventory, not a continuous monitoring service.
