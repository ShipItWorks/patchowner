# patchowner

Turns the CISA KEV catalog into vulnerability notices routed to the owner of an affected item. Built; seven of eight features proven on a sample inventory, one tested with sample data; relevance is not measured and it has not been tried on an organization's own inventory.

**Score: 84 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-12; this record was updated 2026-11-18 from the [product page](https://shipitworks.com/patchowner/).

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

- Feature 7 (in-page policy edit) is built, tested with sample data: its logs on main (proof/policy-edit.log, proof/policy-csv-roundtrip.log, both 2026-11-08, commit 855620e) ran the example inventory only, in one browser engine (Chromium), and were not re-run on the PR #120 merged tree
- Proof logs for features 1 to 5 and 8 were recorded on 2026-11-08 at the pre-merge commit (base f1da22e plus proof files); code merged after them (PRs #96, #97 matching, #88, #93 Watch card) was not re-recorded. Feature 6 was re-recorded at ab77bb6 code (PR #116); no feature log was re-recorded on the PR #120 merged tree (land log, 2026-11-10)
- patchowner.com served site/index.html as last changed by 2bf24a8 (#99, 2026-11-08) at its last recorded fetch (proof/live-demo.log, 2026-11-08T15:21:36Z); that page is not rebuilt from the merged template, so the PR #120 changes are not on it; site/privacy.html is on main but its deploy was not checked
- On 2026-11-18 a review ran pytest at commit 167ffcd with the KEV catalog present: 787 passed, 127 skipped (the README's 97 passed, 4 skipped is dated 2026-10-30); CI on main completed success at bc77d9e (2026-11-10), f82c327 and ab77bb6, but what it ran was not read
- No PyPI release and no installer; running it needs uv
- CLI tests are thin: only the CSV encoding path calls cli.main directly (tests/test_cli_csv_encoding.py:27); proof logs cover the rest by hand
- Browser runs are hand-recorded with Node and Playwright, not run in CI; Safari, a phone and a screen reader not run
- Not tried on an organization's own inventory; one machine's package list was run once (proof/real-software-list.log), where 111 name hits were refused and named; relevance is not measured
- pyproject.toml says 0.1.0 while the tag is v0.4.0; CHANGELOG.md has no 0.2.0, 0.3.0 or 0.4.0 section (changes sit under Unreleased)
- certifi PYSEC-2026-4320 unpatched (dev-only, via httpx); a11y open: no skip link, contrast not verified, no screen reader run

## What changed

- 2026-11-18: A review at commit 167ffcd found EPSS input (from a file you supply; it reorders notices within one urgency level) and ticket and issue export built, with their tests passing, so both targets were removed from Where it's going. The same review ran pytest: 787 passed, 127 skipped. No feature label or score changed.
- 2026-11-11: Merged into the product: the report can now give each owner a one-page notice to check and print or save as a PDF, and the browser test server picks a new port when the first one is taken. These were checked by path and by the pull request text, not run here, so no feature label or score changed (PRs #126 and #131). Scorecard row: "CLI replay of CISA KEV over inventory CSV -> HTML report" (works true, Proven) covers the report as a whole; the one-page notice and the test-server change are not scored (no row covers them).
- 2026-11-11: Merged into the product: open notices can be saved as files for other tools (a ticket file and issue files), with tests that open the report in a browser. No feature label or score changed (PRs #121, #124 and #122).
- 2026-11-10: Land PR #120 merged into main as bc77d9e (16 lane PRs included); no feature label changed this round. Tagged v0.4.0 at bc77d9e.
- 2026-11-08: Action-buttons proof log now states its exit code and was re-recorded at current main (PR #116; tag v0.3.0). Feature 6 is proven; 7 of 8 features proven. 84/100 on our own rubric. CI on main completed success on f82c327 and ab77bb6.
- 2026-11-08: Proof logs merged for the core features (PRs #33, #34, #35, #37, #38, #39, #40, #44, #50; tag v0.2.0). Features 1, 2, 3, 4, 5 and 8 were proven (a log on main with date, commit, command, exit code); features 6 and 7 stayed built, tested with sample data at that point because their logs carried no exit code line. 83/100 on our own rubric.

See [CHANGELOG](CHANGELOG.md).

## Demo

[Demo video (2:06) on the product page](https://shipitworks.com/patchowner/) · [Transcript](https://shipitworks.com/patchowner/transcript/)

The demo voice is AI-generated (ElevenLabs, "Bella") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/patchowner/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.
