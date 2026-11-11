# DNS at OVH and the Pages settings

State on 2026-09-26: `presk-lang.org` resolves to `51.91.236.255`, OVH's
parking address, with OVH's name servers (`dns200.anycast.me`,
`ns200.anycast.me`). Nothing is served.

## Records to enter in the OVH zone (user, OVH manager → Domains → DNS zone)

Remove the parking `A` record at the apex, then add:

| Type | Subdomain | Target | Purpose |
|---|---|---|---|
| `A` | (apex) | `185.199.108.153` | GitHub Pages |
| `A` | (apex) | `185.199.109.153` | GitHub Pages |
| `A` | (apex) | `185.199.110.153` | GitHub Pages |
| `A` | (apex) | `185.199.111.153` | GitHub Pages |
| `AAAA` | (apex) | `2606:50c0:8000::153` | GitHub Pages, IPv6 (optional) |
| `AAAA` | (apex) | `2606:50c0:8001::153` | |
| `AAAA` | (apex) | `2606:50c0:8002::153` | |
| `AAAA` | (apex) | `2606:50c0:8003::153` | |
| `CNAME` | `www` | `presk-lang.github.io.` | redirects to the apex once Pages knows the domain |
| `CNAME` | `docs` | `presk-lang.github.io.` | the manual, served by the `presk` repository's Pages site |

The addresses are GitHub's documented Pages addresses; check them against
`docs.github.com` ("Managing a custom domain for your GitHub Pages site")
on the day, since the list has been stable for years but is GitHub's to
change. Verification: `dig +short presk-lang.org A` lists the four
addresses; `dig +short docs.presk-lang.org CNAME` answers
`presk-lang.github.io.`.

## GitHub side (user)

1. Organization settings → Pages (the sidebar's "Code, planning, and
   automation" section; owners only) → "Verified domains", "Add a domain":
   add `presk-lang.org` and enter the `TXT` record GitHub gives
   (`_github-pages-challenge-presk-lang`) in the OVH zone. This stops
   anyone else from claiming subdomains of the organization's domain on
   Pages.
2. Repository `presk-lang/presk-website` → Settings → Pages: Source
   "GitHub Actions"; custom domain `presk-lang.org` (the workflow's
   `site/CNAME` keeps it; since the repository is not named
   `presk-lang.github.io`, the custom domain is what makes it serve the
   apex); wait for the DNS check, then tick "Enforce HTTPS" once the
   certificate is issued (minutes to an hour).
3. Repository `presk-lang/presk` (once its `main`, the export's
   `refs/public/main`, is pushed) → Settings → Pages: custom domain
   `docs.presk-lang.org`, source "GitHub Actions". The repository's
   workflow `.github/workflows/pages.yml` runs `cargo doc -p presk-manual
   --no-deps` and uploads `target/doc`, with a redirect `index.html` to
   `presk_manual/index.html` at the root, on every push to `main`.
   "Enforce HTTPS" likewise.

## What is not done from the agent's side

No push to GitHub, no `gh` call that creates or configures a repository,
no DNS change: the workspace rule. Everything above is the user's, in the
browser or with `gh` logged in on their machine.
