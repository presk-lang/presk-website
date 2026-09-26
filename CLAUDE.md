# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

> Repository: `presk-website` — the static site of `presk-lang.org`,
> published by GitHub Pages from `presk-lang/presk-lang.github.io`.
> Created 2026-09-26 from `presk-project`.

## What this is

One static page (`site/index.html`, `site/style.css`) and the files GitHub
Pages needs (`site/CNAME`, `.github/workflows/pages.yml`). No generator, no
build, no JavaScript, no external resource: opening `site/index.html` in a
browser is the whole test. The manual lives elsewhere
(`docs.presk-lang.org`, built from the `presk` repository's `presk-manual`
crate); this site links to it.

## Rules

- **What is said about Presk is the project's own wording**: the report's
  chapters in `presk-specs` for what it is, the latest
  `presk-specs/docs/status-*.md` for where it stands (its plain-language
  section is the model), the compiler's manual for what exists. No claim
  on this site that a decision or a report does not hold, no number typed
  from memory; what fails is said to fail.
- **Nothing from `presk-project`** (transcripts, chats, archives) and
  nothing that the publication note keeps private
  (`presk-project/docs/publication-2026-09-25.md`, addendum 2026-09-26).
- **While a paper is under double-blind review**, the site may exist and
  change, but nothing is announced from it and the paper is not mentioned
  until notification; the paper never links the site.
- Links to `github.com/presk-lang/...` name repositories that exist and are
  public at the time of the change; a link to a private or absent
  repository is removed, not left as a promise.
- PDFs placed under `site/` are copies of built documents of `presk-specs`,
  named with their date; the source of truth stays there.
- Git: no remote until the user creates the GitHub repository and adds
  `origin`. The agent never pushes to GitHub. Once the remote exists, a
  branch and a pull request per change; the user merges. `git status` and
  `git log --oneline -5` before editing.

## Where things are

| Item | Location |
|---|---|
| The page | `site/index.html`, `site/style.css` |
| Custom domain | `site/CNAME` (`presk-lang.org`) |
| Deployment | `.github/workflows/pages.yml` (Pages, source "GitHub Actions") |
| DNS records and Pages settings | `docs/dns-ovh.md` |
| Publication decisions and what may be public | `presk-project/docs/publication-2026-09-25.md` |
