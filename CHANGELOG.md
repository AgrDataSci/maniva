# Changelog

This file records every release and every correction. Corrections never replace past content silently. Each entry under Corrections says what changed, why, and which commit changed it. See [`PROVENANCE.md`](PROVENANCE.md) for the policy.

Changes made before this file existed are recorded in the [commit history](https://github.com/AgrDataSci/maniva/commits/main).

## Unreleased

### Added

- Parquet first for any question that spans more than one trial, after a feedback report from a ChatGPT session on sweetpotato traits in West Africa (25 Nov 2026). `SKILL.md`, `AGENTS.md` rule 13 and `llms.txt` now choose the data source by the question, name crop, country and region questions as pooled, and set a fallback order. Parquet first, raw trial files second, then an upload of the three Parquet tables. The session asked the user for JSON uploads, never reached the Parquet tables until the user asked, and gave literature-based rankings before any data. `SKILL.md` rule 6 and `AGENTS.md` rule 13 now say to go to the data first when the user asks what the data show.
- Agents can pool tricot trials through the three Parquet tables (plots, sites, variables) that tricot-data builds on its `dev` pre-release (24 Nov 2026). `SKILL.md`, `AGENTS.md` rule 13 and `llms.txt` add them as the one exception to fetching trial files by raw link, with the build date and the concept DOI to cite. The README table says the data come in JSON and Parquet and that the tricot-data skill is available.
- maniva-reports joins the analysis layer (23 Nov 2026). `SKILL.md` routes every request for a report (technical report, annual report for CGIAR or PRMS, key result story, donor or CGSpace report) to it and carries its rules, PDF and Word delivery, numbers only from files the analysis wrote, every CGIAR reporting field printed, suggested tags labelled as suggestions with SDG 17, and the AI colophon. `AGENTS.md`, `llms.txt`, the README table and diagram, the citation abstract and the website analysis layer, in every language, name it too.
- Mathieu Rouard and Valentin Guignon (Bioversity International) join the authors in `CITATION.cff`, the README and the website citation.
- Three rules in `AGENTS.md` and `SKILL.md` after a feedback report from a ChatGPT session on Ethiopian forage trials (7 Nov 2026). Fetch trial data only from raw links and stop to ask for an upload when that fails, label every claim by its origin and cite only papers with a card or a resolved DOI, and report a computed result only with its code, n and uncertainty. The session read the forage files through a GitHub connector, got empty content and filled the gap with unverified citations and estimates it had not computed.
- A rule to answer questions on women and men, or other designed groups, with part A of the user-group use case in tricot-analysis-workflows, which tests the group within sites.

- On the "Use maniva" page, a fallback link to `AGENTS.md` for assistants that cannot open the GitHub page, in every language.
- A rule in `AGENTS.md` that assistants answer from maniva files only and label any other source, including the web or organisational documents, as outside maniva. Feedback from an M365 Copilot session showed web and private organisational sources mixed into answers.
- The website in Latin American Spanish, French and Brazilian Portuguese, at `/es/`, `/fr/` and `/pt/`, with a language switcher and `hreflang` links on every page. `tools/build-site.py` builds every language from the English pages and the translation files in `site/i18n/`, and warns when an English text has no translation or a translation no longer matches the English.
- `docs/design/agent-access-and-scale.md`, a design note on the size of the suite today and after the next tricot data release, and what that means for AI assistants. It proposes an agent layer generated from the trial JSON (a markdown card, CSV files and a summary table per trial), with a worked example on one okra trial, and four safeguards for growth. It is under discussion and not yet an adopted standard.
- `docs/design/germplasm-integration.md`, a design note on how maniva identifies germplasm across data domains. It sets identity on the germplasm with variety names as aliases, names the source of truth for each type of material, and lists the points open for discussion with partners. It is under discussion and not yet an adopted standard.
- The README diagram shows the data layer by domain, with on-farm testing available and breeding, agronomy, environmental and socio-economic data under development, joined to the analysis workflows through shared keys.

### Corrections

- The tricot-data row in `SKILL.md` and the tricot-data line in `llms.txt` pointed to `data/aa-available-datasets.csv`, which no longer exists. They now point to `datasets.csv` and the tricot-data `SKILL.md`, and the row says the skill is available.

### Changed

- New maniva logo (26 Nov 2026). The mark is now a cassava stem cutting planted in a field, with a furrow that ends in a burgundy data point, in green `#34512F` and burgundy `#6B4044`. It replaces the leaf with network veins, because a cassava leaf on its own can be mistaken for a hemp leaf. All files in `docs/logo` (SVG, PNG and PDF, standard and reversed) carry the new mark under the same file names, so existing links keep working. `docs/logo/README.md` and `metadata/naming.md` record the change. The copies of the logo in the layer repositories (`docs/maniva-logo.svg` in tricot-knowledge-base, tricot-data, tricot-protocols, tricot-analysis-workflows, template-repo-data-analysis, maniva-reports and environment-data) took the new mark the same day.
- The logo is now a seal (27 Nov 2026). The cutting drawn on 26 November stands inside a ring, on a straight ground line that ends in the burgundy data point, in the same green `#34512F` and burgundy `#6B4044`. All 18 files in `docs/logo` are rebuilt under the same names, and the website, its icon and the share card follow. `docs/logo/README.md` and `metadata/naming.md` record the change. The copies in the layer repositories are not yet updated.
- In the horizontal logo the name now sits mid-height beside the mark, where it sat on the ground line before, and the mark is 1.3 times the height of the name, down from 1.8 (26 Nov 2026). The six horizontal files in `docs/logo` are rebuilt.
- The home page opens with a new first screen, after the design team's concept (26 Nov 2026). It shows the logo, the title "An open commons of evidence, protocols, data and analysis for agricultural research", the four layers in numbers, the link to paste with three numbered steps and an example question, and a short statement of what maniva does, in every language. The menu is now "How to use", "Data sources" and "About". The website takes its palette from the new logo and shows the new mark in the header, the footer, the icon and the share card.
- The first screen of the home page is more compact and scales with the window height, so the link to paste shows before any scrolling on laptop screens. On phones the link comes before the four layers.
- The numbers on the home page come from `site/counts.json`, which names the layer repository behind each count. They were checked against the layer repositories on 26 Nov 2026 (511 trials, 41 crops and 20 countries in `tricot-data`, 72 cards in `tricot-knowledge-base`, 19 protocols in `tricot-protocols`, 12 use cases and 9 decision records in `tricot-analysis-workflows`). The sentence "more than 30 crops in more than 25 countries" left the home page, because the open data hold 41 crops in 20 countries.

- The website no longer says ChatGPT, Claude, Gemini and Copilot all work. It says maniva works best with assistants that can open several files from GitHub in one conversation, and that Copilot and Gemini often stay at the main page. Feedback sessions with both showed they could not follow links into the layers.
- The guide's intro no longer says it takes about 20 minutes, which read as the time to get an answer, in every language.
- The home page shows the link to paste right under the headline, and the headline and leaf scale with the screen height, so the link is visible without scrolling on laptop screens.
- The two-column hero now applies only to wide screens. The first version of the change also applied it to phones, which squeezed the headline into a narrow column.
- On phones the leaf is smaller, so the link sits higher on the first screen.
- The French text uses a non-breaking space before question marks, so the mark never wraps onto its own line.
- On the website, the "Test the alpha" offer is now "Give feedback", so it no longer repeats the "Test it" menu item, and the menu text is larger.
- The "Work with us" section is now "Collaborate", in the order Try maniva, Contribute data, Partner or fund. "Try maniva" links to the test guide.
- The test guide's last step now holds the report prompt, with a copy button, so testers have it before they open the feedback form.
- Jacob van Etten's profile in "Talk to the team" now gives his focus areas next to his role as Director, Digital Inclusion.
- The website menu has one "Use it" item instead of "Use it" and "Test it". The guide is now "Use maniva" at `site/use.html`, replacing `site/test.html`, and the short three-step section on the home page links to it.
- The profiles of Kauê de Sousa and Marie-Angélique Laporte in "Talk to the team" now open with their roles, like Jacob van Etten's.

## 1.0.0 (2026-11-06)

First release, archived on Zenodo. The four layers (knowledge base, protocols, data, analysis) are linked from one entry point, maniva is titled an open commons of evidence, protocols, data and analysis for agricultural research, with tricot as its first domain, and the citation, naming and history policies are in place.

### Added

- A website in `site/`, published to GitHub Pages at https://agrdatasci.github.io/maniva/ by the `pages` workflow. It explains the four layers, routes example questions to them, shows the live version from `version.json`, and links the forms to propose data and send feedback.
- A "Test maniva" page (`site/test.html`) that walks alpha testers through five steps, from sharing the link to sending feedback, with example questions checked against the published layers.
- A "Talk to the team" section on the website, with institutional contacts for Kauê de Sousa, Marie-Angélique Laporte and Jacob van Etten, who agreed to be listed as contacts in the tricot-knowledge-base people file.
- `PROVENANCE.md`, the policy against rewriting history and the instructions to verify it.
- `tools/verify-history.sh`, a script that compares the history of `main` and every tag with the snapshots held by Software Heritage.
- The `verify-history` workflow, which runs that script on every push, release and week, and asks Software Heritage to archive the current state.
- Rulesets in `.github/rulesets` that block force pushes, branch deletion and tag changes.
- A naming rule in `AGENTS.md`, `SKILL.md` and `llms.txt`. maniva and tricot are always lowercase, and tricot stands for triadic comparison of technology options.
- `metadata/layer-guidance.md`, with the traceability chain, documentation checklist and FAIR safeguards for every layer.

### Changed

- The title is "maniva. An open commons of evidence, protocols, data and analysis for agricultural research" everywhere, matching `CITATION.cff` and the Zenodo record. It replaces the working descriptor "AI-ready documentation for tricot" in `README.md`, `SKILL.md`, `AGENTS.md`, `llms.txt`, `metadata/naming.md` and the website title. "AI-ready" stays as a keyword. tricot is presented as the first domain, and climate and household data as next.
- `README.md` leads with the problem maniva solves, the worked example and how to use it. The tricot background opens the repositories section, and "Why maniva?" sits near the end as one paragraph. The website follows the same order.
- The website offers one way to use maniva, pasting the maniva link into an AI assistant with web access. The README keeps the other routes for technical users.
- The R packages and the analysis template sit under the analysis layer, in the README diagram and table, the routing table in `SKILL.md` and `llms.txt`. The template was previously described as cross-cutting.
- `CITATION.cff` has the title "maniva. An open commons of evidence, protocols, data and analysis for agricultural research", a rewritten abstract, the website URL and an updated keyword list. The authors are Kauê de Sousa, Marie-Angélique Laporte, Brayden Youngberg, Almendra Cremaschi, Rachel Chase and Jacob van Etten. The README and website citations match it.
- `metadata/naming.md` states the decision and its reasons first, then the tests and the names set aside.
- `PROVENANCE.md` states its main claim in the opening, flags the protections that are still pending right after the commitments, and folds "Independent verification" into "Check it yourself".

### Removed

- `proposals/five-layer-architecture.md`, a discussion draft superseded when the integration layer was folded into the analysis layer. Its guidance moved to `metadata/layer-guidance.md`, and the full draft remains in the history at commit `e2927e5`.

### Corrections

- Marie-Angélique Laporte's given name in `CITATION.cff` repeated her surname (`Marie-Angélique Laporte`), so citations showed it twice. It now reads `Marie-Angélique`.
