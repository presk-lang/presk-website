# presk-website

The site served at `presk-lang.org`: a static page in `site/`, published
by GitHub Pages from `github.com/presk-lang/presk-website` through the
workflow in `.github/workflows/pages.yml`. The canonical repository is on
the GitLab (`origin`, `git.sophia.minesparis.psl.eu:presk/presk-website`);
GitHub (remote `github`) is the mirror Pages builds from, pushed by the
user.

- `site/index.html` — the landing page. No build step, no JavaScript, no
  external fonts or scripts: the page is the file.
- `site/CNAME` — the custom domain, read by GitHub Pages.
- `site/style.css` — the page's style.
- `docs/dns-ovh.md` — the records to enter in the OVH DNS zone, and the
  Pages settings.
- `CLAUDE.md` — guidance for coding agents.

Prepared 2026-09-26. To publish: the user pushes `main` to `github`,
enables Pages on `presk-lang/presk-website` (source: GitHub Actions) with
the custom domain `presk-lang.org`, and enters the DNS records. The manual at
`docs.presk-lang.org` is not built here: it is the `presk` repository's own
Pages site, built from its `presk-manual` crate.

The context, and what may and may not be public while the paper is under
review, is in `presk-project/docs/publication-2026-09-25.md`, addendum of
2026-09-26.
