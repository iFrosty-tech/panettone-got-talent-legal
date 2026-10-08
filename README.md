# Panettone's Got Talent – legal pages

Public static pages for the Panettone's Got Talent mobile app: the privacy policy and the account-deletion page that the App Store, Google Play and the Google OAuth consent screen link to. Served by GitHub Pages from the `main` branch root.

> This repository holds only static legal pages. Never add app code, keys, tokens, environment files, logs, database dumps or any personal data. The repository is public.

## URLs

| Page | URL |
| --- | --- |
| Home | `https://ifrosty-tech.github.io/panettone-got-talent-legal/` |
| Privacy policy | `https://ifrosty-tech.github.io/panettone-got-talent-legal/privacy/` (`#it`, `#en`) |
| Account deletion | `https://ifrosty-tech.github.io/panettone-got-talent-legal/delete-account/` (`#it`, `#en`) |

The repository owner is spelled `iFrosty-tech`; GitHub Pages hostnames are always lowercase, so the URLs use `ifrosty-tech`. Both are correct.

## Fixed values

Every page is bilingual: Italian (`#it`) first, then English (`#en`). Keep both sections in sync when a value changes.

| Value | Meaning | Where |
| --- | --- | --- |
| Marco Verri | Data controller, shown as developer name on the stores | `index.html` (2), `privacy/index.html` (6), `delete-account/index.html` (2) |
| tag-tic.99@icloud.com | Privacy contact, also used for deletion requests by email | `index.html` (2), `privacy/index.html` (6), `delete-account/index.html` (2) |
| 2026-10-06 | Last updated and effective date of the privacy policy | `privacy/index.html` (4) |

## Open points

`{{TBD: …}}` marks an undecided point; the text inside says what must be decided. Replace the whole token with the final sentence in the section's language (`privacy/index.html` 10, `delete-account/index.html` 4). The pages must have no `{{TBD` left before the app is submitted to the stores.

Each point appears once in Italian and once in English:

| Point | Page and section |
| --- | --- |
| Retention of archived rooms, votes and photos (Q-07) | Privacy 6; deletion "What is kept" |
| Retention of support, rights and deletion-request emails | Privacy 6; deletion "What is kept" |
| Supabase project region and transfer safeguards | Privacy 5 |
| Whether Expo EAS Update and the off-site backup storage must be listed as recipients | Privacy 4 |
| Minimum age to use the app | Privacy 11 |

Check that nothing is left before pushing:

```sh
rg -n "\{\{" --glob "*.html" .
```

## How to update

1. Edit the HTML. Keep the Italian and English sections in sync and keep the policy consistent with the app's data inventory (`docs/architecture/security-and-privacy.md` in the app repository).
2. When the policy text changes, update the effective date in both languages.
3. Preview locally with any static server from the repository root, for example `python -m http.server`, then open `http://localhost:8000/`.
4. Commit with a Conventional Commit message and push to `main`. GitHub Pages republishes within a few minutes.

## Rules for this site

- Plain HTML and one stylesheet (`assets/style.css`). No JavaScript, external fonts, CDNs, analytics, trackers or cookies.
- Links are relative (`../assets/style.css`, `../privacy/`), so they work under the `/panettone-got-talent-legal/` path. Never use root-absolute links such as `/assets/...`.
- `.nojekyll` disables Jekyll processing, so files are served as they are.
- Colours come from the app's design tokens; body text keeps WCAG AA contrast in light and dark mode.
