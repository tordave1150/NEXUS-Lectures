# AGENTS.md — Public Online Second Brain Publishing Agent

## 1. Mission

Maintain and publish this folder as a public Online Second Brain using:

- Obsidian-compatible Markdown as the source of truth
- Quartz 5 as the static-site generator
- GitHub as the Git remote and deployment source
- Vercel as the production host

The required delivery pipeline is:

`Obsidian content -> Quartz build -> Git commit/push -> Vercel Git deployment`

Codex must preserve the knowledge base, keep the website reproducible from Git, and verify the deployed result before declaring the work complete.

## 2. Public-content assumption

The user has explicitly confirmed that all user-authored files in this folder are intended to be public and contain no personal information.

Therefore:

- Treat all Markdown notes and their referenced public assets as publishable by default.
- Do not require `publish: true` or a per-note privacy review.
- Do not remove a note merely because it lacks frontmatter.
- Preserve the full public topic/folder structure unless a technical limitation requires a change.
- Do not add authentication, a private-content pipeline, or access control unless the user later requests it.

This public-content assumption does not authorize publishing credentials or machine-generated local state. Never commit or publish:

- `.env` or `.env.*`
- API keys, access tokens, private keys, passwords, or credential files
- `.git/`, `node_modules/`, build caches, operating-system metadata, or temporary files
- Obsidian workspace/session state such as `.obsidian/workspace.json` and `.obsidian/workspace-mobile.json`
- Vercel local linkage data such as `.vercel/`

Run a lightweight secret check before the first push and whenever credential-like files are added. Do not perform a broad personal-information audit unless the user changes the public-content assumption.

## 3. Instruction precedence and scope

- This file governs the repository rooted at the directory containing it.
- Preserve any more specific `AGENTS.md` or `AGENTS.override.md` instructions found in subdirectories.
- If existing project instructions conflict with this publication workflow, report the conflict before changing content or deployment behavior.
- Treat the user's explicit request in the current conversation as authoritative over this file.

## 4. Non-negotiable operating rules

1. Inspect before editing. Determine whether this is already a Quartz repository, an Obsidian vault, a Git repository, or some combination of them.
2. Preserve user content and unrelated changes. Never overwrite, delete, or mass-rename notes without a recoverable Git checkpoint and clear need.
3. Never use force push, destructive Git reset, or history rewriting.
4. Preserve Obsidian syntax, including wikilinks, embeds, callouts, tags, properties, and relative asset references.
5. Preserve relative paths and filename case. Vercel builds on Linux, so case-mismatched links that work on Windows may fail in production.
6. Do not create a second copy of the knowledge vault inside itself.
7. Do not use a symlink whose target is outside the Git repository; Vercel cannot build content that is absent from the clone.
8. Keep generated output reproducible. Do not manually edit files under `public/`.
9. Do not commit `public/` unless the current official Quartz template intentionally tracks it.
10. Use the repository's existing package manager and lockfile. For a standard Quartz 5 repository, use npm and retain `package-lock.json`.
11. Do not add an alternative web framework when Quartz already satisfies the requirement.
12. Do not change DNS, purchase a domain, or enable paid Vercel features unless explicitly requested.

## 5. Expected repository shape

The preferred post-setup structure for NEXUS Lectures is:

```text
repository-root/
├── AGENTS.md
├── content/                 # Public Obsidian notes and referenced assets
│   ├── index.md             # Website landing page
│   ├── 00_INDEX.md
│   ├── 01 Sources/
│   ├── 02 Concepts/
│   ├── 03 Methods/
│   ├── 04 Models/
│   ├── 05 Metrics/
│   ├── 06 Code Examples/
│   ├── 07 MOCs/
│   └── 99 References/
├── quartz.config.yaml       # baseUrl: lectures.jsdp-nexus.com
├── quartz.layout.yaml
├── quartz.lock.json
├── package.json
├── package-lock.json
├── vercel.json
├── .gitignore
└── ...                      # Quartz source and configuration files
```

`content/` is the publishable Obsidian content root. The user may open `content/` directly as an Obsidian vault after migration.

If this repository already has a valid Quartz structure, retain it. Do not reorganize solely to match the example.

## 6. Required execution phases

For a request to set up or publish the site, complete the phases below in order. Maintain a short plan and update it as work progresses.

### Phase 0 — Determine authorization

Classify the user's request:

- If the user asks only for a review, explanation, or plan, perform read-only inspection and do not create repositories, push commits, or deploy.
- If the user explicitly asks to set up, publish, push, connect, or deploy, repository creation, Git push, and Vercel deployment are within scope.
- Creating a GitHub repository or Vercel project requires the target account/organization and project name. Infer these only from an unambiguous existing remote or authenticated project context; otherwise ask one concise question.
- Never request passwords, API keys, access tokens, or recovery codes in chat. Use existing authenticated tools or let the user complete provider login in the provider's own interface.

### Phase 1 — Preflight inspection

From the project root, inspect without modifying:

```bash
pwd
rg --files -g 'AGENTS.md' -g 'AGENTS.override.md' -g '!node_modules' -g '!.git'
git status --short --branch
git remote -v
git branch --show-current
node --version
npm --version
```

Also check for:

- `package.json`
- `quartz.config.yaml`
- `quartz.layout.yaml`
- `quartz.lock.json`
- `content/`
- `.obsidian/`
- existing Markdown notes and attachments outside `content/`
- existing `vercel.json`
- existing `.vercel/` local linkage
- an existing GitHub remote

Do not fail merely because Git, Node, npm, GitHub CLI, or Vercel CLI is missing. Report the missing dependency and use the safest supported alternative.

### Phase 2 — Protect the starting state

Before structural changes:

1. Review `git status` and distinguish user changes from Codex changes.
2. If Git is already initialized, do not modify or discard unrelated uncommitted work.
3. If the folder is not tracked by Git and publication was requested, initialize it with a `main` branch:

```bash
git init -b main
```

4. Create a baseline commit only if the user requested implementation/publication and the current content is ready to be tracked.
5. If a baseline commit is not safe because unrelated changes are ambiguous, stop and ask before restructuring.

### Phase 3 — Install or reconcile Quartz 5

Use the latest stable Quartz 5 instructions from the official Quartz documentation. Do not silently install Quartz 4 or an older template.

#### When Quartz is already installed

- Inspect `package.json` and Quartz configuration.
- Do not reinitialize the site.
- Run the repository's documented install and build commands.
- Upgrade Quartz only when requested or when the current version cannot build. Treat an upgrade as a separate change and verify it carefully.

#### When Quartz is not installed

Use the official Quartz 5 template or official repository. Prefer the template for a new repository. For an existing content folder, stage the framework without overwriting user notes.

Current Quartz 5 baseline requirements and commands:

```bash
node --version                 # Must be Node.js 22 or later
npm i
npx quartz create
npx quartz plugin install --from-config
npx quartz build --serve
```

During `npx quartz create`, select:

- Template: `obsidian`
- Content strategy: `copy` when importing the existing public vault
- Base URL: the intended Vercel hostname without `https://`

If the final Vercel hostname is not known yet, use the expected project hostname, for example `lectures.jsdp-nexus.com`, then correct it after the first deployment if necessary.

Do not run an interactive initializer blindly. Inspect its prompts and ensure it cannot overwrite the existing content. If safe non-interactive execution is unavailable, pause at the prompt that materially requires the user to choose.

### Phase 4 — Reconcile the public Obsidian content

The final website content must live under `content/`.

1. If the existing vault is already under `content/`, use it in place.
2. If public notes are at the repository root or another folder, migrate or copy them into `content/` while preserving their relative hierarchy.
3. Do not copy the following into `content/`:
   - Git metadata
   - Quartz source/configuration
   - package dependencies
   - `.vercel/`
   - temporary/export/build folders
   - Obsidian workspace/session state
4. Retain useful Obsidian configuration only when it is needed for authoring and safe to track. Prefer a focused `.gitignore` over deleting local configuration.
5. Preserve attachments and their relative paths.
6. Preserve valid `[[wikilinks]]`, `![[embeds]]`, standard Markdown links, headings, callouts, tags, and YAML properties.
7. Do not rewrite note content, summaries, or knowledge claims merely to make the site build.
8. Create `content/index.md` only if no suitable landing page exists. Its purpose is to orient readers and link to the major topic areas; it must not invent knowledge or duplicate full notes.
9. Do not create duplicate Vault or topic trees.

### Phase 5 — Configure Quartz

Inspect and minimally update `quartz.config.yaml` and `quartz.layout.yaml`.

Required outcomes:

- Site title clearly identifies the Online Second Brain.
- `baseUrl` matches the production hostname and excludes `https://`.
- Markdown, Obsidian wikilinks, backlinks, tags, search, explorer/navigation, and graph view work where supported by the selected Quartz template.
- Locale and date formatting are appropriate for the existing content. Preserve bilingual Thai/English content.
- Existing folder and tag organization remains navigable.
- No analytics, comments, external fonts, or third-party trackers are enabled without user approval.

Keep configuration changes small. Do not redesign the theme unless the user asks for visual customization.

### Phase 6 — Add Vercel configuration

Create or reconcile `vercel.json` at the repository root:

```json
{
  "cleanUrls": true
}
```

If `vercel.json` already contains other valid settings, merge `cleanUrls` instead of replacing unrelated configuration.

Ensure `.gitignore` excludes at least local dependencies, local Vercel state, secrets, temporary files, and generated files according to the official Quartz template. Do not replace a good existing `.gitignore` wholesale.

### Phase 7 — Local installation and build verification

For an existing clone with a lockfile, prefer reproducible installation:

```bash
npm ci
npx quartz plugin install
npx quartz build
```

If the configuration references plugins not recorded in the lockfile, reconcile intentionally:

```bash
npx quartz plugin install --from-config
npx quartz build
```

Verify that:

- The command exits successfully.
- `public/index.html` exists.
- Representative note pages were generated.
- Referenced images and attachments exist in the output.
- Build output contains no unresolved-link or missing-asset errors that affect published content.
- No source note was unexpectedly omitted.

Then preview locally when possible:

```bash
npx quartz build --serve
```

Inspect at minimum:

- Home page
- One Thai note
- One English or mixed-language note, when available
- One note with wikilinks/backlinks
- One note with an image or attachment
- Search
- Folder navigation
- Graph view
- A missing URL/404 response

Do not leave a long-running preview process behind after verification.

### Phase 8 — Pre-push quality and secret check

Before the first public push:

1. Inspect tracked candidates with `git status --short` and `git diff --check`.
2. Confirm `.env*`, `.vercel/`, credentials, private keys, dependency folders, caches, and local workspace files are untracked.
3. Search filenames and text for obvious credential patterns without printing secret values into chat or logs.
4. Check for accidentally duplicated content trees.
5. Check for case-only path mismatches that may fail on Linux.
6. Re-run the production build after any fix.

The user's public-content confirmation means note-by-note PII screening is not required. Secret and credential protection remains mandatory.

### Phase 9 — Commit and push to GitHub

If a correct GitHub remote already exists, preserve it. Never replace an existing remote without confirming it targets the wrong repository.

If no remote exists and GitHub CLI is authenticated, the recommended new-repository flow is:

```bash
gh auth status
gh repo create OWNER/REPOSITORY --public --source=. --remote=origin --push
```

Use the owner and repository name confirmed by the user or unambiguously available from project context.

If the GitHub repository was created through the website, connect it with:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git remote -v
git push -u origin CURRENT-BRANCH
```

For an existing Quartz repository whose `origin` points to the official Quartz repository, use `git remote set-url origin REMOTE-URL` only after confirming that this is the intended correction.

Use clear commits, for example:

```text
Set up Quartz 5 public knowledge site
Publish updated Online Second Brain notes
Fix broken links and Vercel build configuration
```

Before pushing:

- Show the final staged scope.
- Do not include unrelated user changes.
- Do not force push.
- Do not bypass repository protection.

Quartz's supported sync command may be used after the repository is configured:

```bash
npx quartz sync --no-pull   # First push when appropriate
npx quartz sync             # Routine later updates
```

If using `npx quartz sync`, inspect its intended commit/pull/push behavior first and do not let it absorb unrelated changes.

### Phase 10 — Connect GitHub to Vercel

The Vercel project must be connected to the GitHub repository so later pushes trigger deployments.

Preferred dashboard flow:

1. Open Vercel Dashboard.
2. Select **Add New -> Project**.
3. Import the GitHub repository containing the Quartz project.
4. Use a lowercase, hyphenated project name.
5. Set:
   - Framework Preset: `Other`
   - Root Directory: `./`
   - Build Command: `npx quartz plugin install && npx quartz build`
6. Use the Git repository's actual default/production branch. Do not assume it is `main` or `v5`; inspect it.
7. Deploy.

If the Vercel UI requests an output directory and does not detect it, use `public`.

CLI-assisted flow is acceptable when the Vercel CLI is available and authenticated:

```bash
npx vercel@latest link
npx vercel@latest git connect
```

Use the CLI's current help output and official Vercel documentation for exact flags. The goal is Git integration, not a one-off CLI-only deployment.

If authentication is required:

- Use provider-managed browser login.
- Never ask the user to paste a Vercel or GitHub token into chat.
- Pause for manual login only when the provider requires it, then continue after authentication succeeds.

### Phase 11 — Verify the production deployment

Do not stop at a successful build log. Verify the deployed website directly.

Required checks:

- Vercel deployment status is Ready/Successful.
- Production URL returns HTTP 200.
- Home page renders correctly on desktop and a narrow/mobile viewport.
- At least three representative note URLs open directly.
- Clean URLs work without `.html`.
- Internal links, backlinks, navigation, tags, search, and graph view work.
- Images and attachments load.
- Thai and English text render correctly.
- No obvious client-side errors appear.
- A nonexistent page shows the intended 404 behavior.
- Sitemap/RSS URLs work when those Quartz features are enabled.
- The deployed revision matches the intended Git commit.

If the first Vercel hostname differs from `baseUrl`, update `baseUrl`, rebuild, commit, push, and verify the replacement deployment.

### Phase 12 — Custom domain, only when requested

When the user requests a custom domain:

1. Confirm the exact apex domain or subdomain.
2. Update Quartz `baseUrl` without `https://`.
3. Add the domain to the correct Vercel project.
4. Present the required DNS records or apply them only when the user has explicitly authorized access to the DNS provider.
5. Wait for Vercel to report a valid configuration.
6. Rebuild/redeploy if configuration changed.
7. Verify HTTPS, canonical URLs, direct note URLs, sitemap, and RSS.

Never replace an existing production site on the same domain without explicit confirmation.

## 7. Routine content-update workflow

After initial setup, use this cycle for every publishing update:

1. Inspect `git status` and pull/reconcile remote changes safely.
2. Add or update notes under `content/` while preserving the existing vault taxonomy.
3. Reconcile duplicates and links according to the Online Second Brain knowledge-ingestion rules, when applicable.
4. Run:

```bash
npm ci
npx quartz plugin install
npx quartz build
```

5. Inspect the affected pages locally when the update changes structure, assets, links, or layout.
6. Review `git diff` and `git diff --check`.
7. Commit only the intended changes.
8. Push the production branch, normally with `npx quartz sync` or standard Git commands.
9. Confirm that Vercel created a deployment from that commit.
10. Verify the affected live pages.

For feature or theme changes, prefer a non-production branch so Vercel creates a Preview Deployment. Merge to the production branch only after preview verification.

## 8. Troubleshooting order

When deployment fails, diagnose in this order:

1. Read the first meaningful error in the local or Vercel build log.
2. Confirm Node.js is version 22 or later.
3. Run `npm ci` from the repository root.
4. Run `npx quartz plugin install` and confirm `quartz.lock.json` is current.
5. If plugins are missing from the lockfile, use `npx quartz plugin install --from-config` intentionally.
6. Run `npx quartz build` locally and reproduce the failure.
7. Confirm Vercel Root Directory is `./` and the build command is correct.
8. Confirm `vercel.json` is valid JSON and includes `"cleanUrls": true`.
9. Check filename case, wikilink targets, asset paths, YAML syntax, and unsupported files.
10. Confirm every required content file is tracked and pushed to GitHub.
11. Confirm `baseUrl` matches the active hostname.
12. Clear/redeploy only after identifying a cache-related reason; do not use redeploy as a substitute for diagnosis.

Do not hide broken notes, links, or assets merely to make the build green. Fix the underlying issue or report the exact blocker.

## 9. Definition of done

The publication task is complete only when all applicable items are true:

- Public notes and assets are organized under the Quartz content root without duplication or loss.
- Quartz 5 configuration is valid and minimal.
- Local production build succeeds.
- `vercel.json` enables clean URLs.
- Secret/local-state exclusions are in place.
- Intended changes are committed and pushed to the correct GitHub repository.
- Vercel is connected to that GitHub repository.
- The production deployment is successful and tied to the intended commit.
- Representative pages, links, search, graph/navigation, assets, and bilingual text are verified live.
- The working tree contains no unexplained Codex-created changes.

## 10. Final handoff format

Lead with the outcome. Report:

- Production URL
- GitHub repository and production branch
- Deployed commit identifier
- Local build result
- Live verification result
- Important files created or changed
- Any remaining warnings or user actions, such as domain DNS changes

Do not claim deployment success without opening and checking the live site. If blocked by authentication, account selection, repository ownership, DNS access, or provider permissions, state exactly what the user must do and resume from that point afterward.

## 11. Authoritative references

Before a major setup, migration, or troubleshooting change, verify commands against current primary documentation:

- Codex `AGENTS.md`: https://developers.openai.com/codex/agent-configuration/agents-md
- Quartz 5 installation: https://quartz.jzhao.xyz/getting-started/installation
- Quartz 5 hosting/Vercel: https://quartz.jzhao.xyz/hosting
- Quartz 5 configuration: https://quartz.jzhao.xyz/configuration
- GitHub local repository import: https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github
- Vercel Git deployments: https://vercel.com/docs/git
- Vercel CLI Git integration: https://vercel.com/docs/cli/git

If current official instructions conflict with commands in this file, follow the current official instructions, preserve the project's content and intent, and document the deviation.
