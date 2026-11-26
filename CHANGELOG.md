# Changelog

All notable work on SiteMatch is recorded here.

## Unreleased — 2026-11-26

### Changed
- The GitHub organization was renamed from DVRK-ORG to **Vullki**. `LICENSE` now reads `Vullki`, and the links below point to `github.com/Vullki/sitematch` (old `DVRK-ORG` links still redirect).
- `README.md` opens with a hero banner and shows the scoring model and the verification steps as images (`docs/images/`).
- This changelog now carries the full 1.0.0 history instead of the short summary.

## 1.0.0 — 2026-11-08

First public package. Published at [github.com/Vullki/sitematch](https://github.com/Vullki/sitematch) (public, branch `main`; the organization was then named DVRK-ORG).

### Starting point

The original skill was a private draft (~157 lines). It already ranked websites by functional similarity (purpose, category, features, audience, content, monetization), required live verification, and accepted either a reference URL or a natural-language description. It did not yet have personalization, depth modes, a release kit, or a public home.

### Review and research

- Full editorial review of the original `SKILL.md`, `agents/openai.yaml`, and `assets/icon.svg`.
- Comparison against an independent UX and release review (P1–P3 findings and six eval prompts).
- Competitive scan of public agent-skill hosts and GitHub `SKILL.md` files. The field is not empty: one close editorial peer is Similar Sites by Content; several other skills wrap Exa or Similarweb-style APIs. SiteMatch is positioned as an evidence-led, constraint-aware skill for finding and comparing website alternatives — not as the first, only, or “better than Similarweb” option.

### Skill text

- Personalization (§2.5): similarity stays about the reference; personal fit is scored separately from known preferences (this request, earlier conversation, memory, or labeled inference). Sources are disclosed. Hard constraints filter eligibility; soft preferences do not bend the similarity score.
- Requested differences no longer punish a candidate: cheaper or free options drop monetization from the similarity weights; a feature the reference lacks is treated as a requirement, not an unrelated extra.
- Reply and search in the user’s language and named region; at least one discovery route follows that language or region.
- Quick / Standard / Deep depth modes, with a typical research budget and a “first delivery uses live search” rule.
- Trust check for clone and “free download” risks.
- Comparison table: `# | Site | Similarity | Price | Best for | Key difference`, plus a Fit for you column only when personalization is active. Prices must not be invented.
- Score bands (Very close / Close / Partial), ties under 5 points, and component values in Deep mode.
- Intent presets (switching, competitor research, niche discovery, acquisition scouting) with explicit weight precedence: this-turn instructions beat an inferred preset, which beats the defaults.
- Follow-up handling that reuses verified evidence (“more”, “more like #N”, new constraints, A vs B).
- Description rewritten to say what the skill finds, then the real trigger phrases (“sites like X”, “alternatives to X”, “X but free”, replacements, competitors, niche discovery, acquisition scouting).
- Short anti-jobs: not a traffic-graph, backlink, or SEO-audit tool; no invented domains, URLs, prices, traffic, features, or verification results; no sign-up or purchase actions.
- Frontmatter: `license: MIT` and a `compatibility` note that live web search and page retrieval are required.

### Release kit

- `README.md` — what it is, what it is not (no traffic graphs), verified install paths for Claude Code (`~/.claude/skills/sitematch/`) and claude.ai (Customize → Skills, ZIP with the folder as root), invocation examples without invented results.
- `LICENSE` — MIT. Copyright line named the organization (then `DVRK-ORG`, now `Vullki`), not a personal legal name.
- `evals/prompts.md` — six prompts from the review: Notion URL, Gulf handmade-jewelry description, free Premiere alternatives, Arabic Canva alternatives, ambiguous “Mercury”, and a dead or blocked reference.
- `agents/openai.yaml` — short description updated to mention function and personal fit.
- `assets/icon.svg` — carried forward unchanged.

### Publish

- 2026-11-08: created the public repository (then `DVRK-ORG/sitematch`, now `Vullki/sitematch`) and pushed `main` with the full package (`SKILL.md`, README, LICENSE, this changelog, evals, icon, and `agents/openai.yaml`).

### Still open

- The six eval prompts are documented but have not yet been run live against real sites.
- The icon’s origin and license were not independently verified before publish. Confirm it is original or permissively licensed if that still needs checking.
