# patchowner

Turns the CISA KEV catalog into vulnerability notices routed to the owner of an affected item. Built; seven of eight features proven on a sample inventory, one tested with sample data; relevance is not measured and it has not been tried on an organization's own inventory.

**Score: 84 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-08; this record was updated 2026-11-08 from the [product page](https://shipitworks.com/patchowner/).

Every number on the product page names the file it came from. The lists below are copied from that page, not rewritten.

**Platform.** Command line and web (Python; runs with uv). Live demo at patchowner.com.

## What works today

- CLI replay of CISA KEV over inventory CSV -> HTML report (Proven)
- Web upload demo (patchowner serve) (Proven)
- SSVC deployer tree, default SEI policy, custom --policy CSV (Proven)
- Matching tiers, suppression, budget, routing (Proven)
- Health tab (README says ten to twelve checks) (Proven)
- Action buttons persist state (serve mode JSON; static mode browser storage) (Proven)
- Interactive policy edit recomputes cards in page (Tested with sample data)
- Live demo patchowner.com (Proven)

## Not done yet

- Feature 7 (in-page policy edit) is built, tested with sample data: its browser log on main records '9 ok, 0 failed' but no exit code line; one browser engine; the edited policy CSV does not run with `replay --policy` on main (PR #31 not merged)
- Proof logs for features 1 to 5 and 8 were recorded on 2026-11-08 at the pre-merge commit (base f1da22e plus proof files); code merged after them (PRs #96, #97 matching, #88, #93 Watch card) was not re-recorded. Feature 6 was re-recorded at ab77bb6 code (PR #116)
- patchowner.com is the build of f1da22e: site/index.html is unchanged on main since then, so it has none of the 2026-11-08 changes; site/privacy.html is on main but its deploy was not checked
- Test count on main not measured (README's 97 passed, 4 skipped is dated 2026-10-30); CI on main is green at f82c327 and ab77bb6 but what it ran was not read
- No PyPI release and no installer; running it needs uv
- CLI tests are thin: only the CSV encoding path calls cli.main directly (tests/test_cli_csv_encoding.py:27); proof logs cover the rest by hand
- Browser runs are hand-recorded with Node and Playwright, not run in CI; Safari, a phone and a screen reader not run
- Not tried on an organization's own inventory; one machine's package list was run once (proof/real-software-list.log), where 111 name hits were refused and named; relevance is not measured
- pyproject.toml says 0.1.0 while the tag is v0.3.0; CHANGELOG.md has no 0.2.0 or 0.3.0 section (changes sit under Unreleased)
- certifi PYSEC-2026-4320 unpatched (dev-only, via httpx); a11y open: no skip link, contrast not verified, no screen reader run

## What changed

- 2026-11-08: Action-buttons proof log now states its exit code and was re-recorded at current main (PR #116; tag v0.3.0). Feature 6 is proven; 7 of 8 features proven. 84/100 on our own rubric. CI on main completed success on f82c327 and ab77bb6.
- 2026-11-08: Proof logs merged for the core features (PRs #33, #34, #35, #37, #38, #39, #40, #44, #50; tag v0.2.0). Features 1, 2, 3, 4, 5 and 8 were proven (a log on main with date, commit, command, exit code); features 6 and 7 stayed built, tested with sample data at that point because their logs carried no exit code line. 83/100 on our own rubric.
- 2026-11-08: Fixes to what the report says and does (PRs #36, #53, #54, #60, #65, #66, #67, #69, #70, #72, #74, #77, #78, #79, #84, #85, #86, #88, #90, #92, #93, #47; tag v0.2.0): a refused action is no longer shown as recorded, a CSV asset name no longer runs as script in the Policy tree, keyboard focus ring and real tabs, Reopen on a suppressed notice, a bad download keeps the saved catalog.
- 2026-11-08: Matching and output changes (PRs #48 Tickets button saves open notices as a CSV, #51 upload-form labels, #95 long warning lists fold, #96 and #97 a name inside another word is likely, not exact, and a row with no vendor no longer matches inside a word; tag v0.2.0). The proof logs were recorded before #96 and #97 and were not re-run.
- 2026-11-08: Docs and housekeeping on main (PRs #32 README says ten to twelve Health checks, #99 privacy page site/privacy.html, #100 CHANGELOG.md, #107 CI on a self-hosted runner; tag v0.2.0). patchowner.com is not rebuilt; its page is still the build of f1da22e.
- 2026-11-07: Corrected the one-line description. It said "Only verified, relevant, actionable ... notices"; no measure of relevance exists and the run covers a sample inventory only. The line now says what ran and the stage.

See [CHANGELOG](CHANGELOG.md).

## Demo

[Demo video (2:32) on the product page](https://shipitworks.com/patchowner/) · [Transcript](https://shipitworks.com/patchowner/transcript/)

The demo voice is AI-generated (ElevenLabs, "Alice") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/patchowner/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.
