# patchowner

Turns the CISA KEV catalog into vulnerability notices routed to the owner of an affected item. Built; ten of thirteen features proven, three tested with sample data; relevance is not measured on real data and no organization has used it.

**Score: 87 / 100** on my own [rubric](https://shipitworks.com/how-we-score/). Stage: Release candidate. Scored 20 Nov 2026 at commit 44d7928, from the [product page](https://shipitworks.com/patchowner/).

Every number on the product page names the file it came from.

**Platform.** Command line and web (Python; runs with uv). Live demo at patchowner.com.

## What works today

- CLI replay of CISA KEV over inventory CSV -> HTML report (Proven)
- Web upload demo (patchowner serve) (Proven)
- SSVC deployer tree, default SEI policy, custom --policy CSV (Proven)
- Matching tiers, "may not apply" labels (every match sent), budget, routing (Proven)
- Health tab (README says ten to twelve checks) (Proven)
- Action buttons persist state (serve mode JSON; static mode browser storage) (Proven)
- Interactive policy edit recomputes cards in page (Tested with sample data)
- Live demo patchowner.com (Proven)
- Ticket and issue export (replay --tickets, --issues; page Tickets and Issues buttons) (Proven)
- EPSS file as an input to priority (replay --epss) (Proven)
- One-page notice per owner (print or save as PDF) (Proven)
- Version check against NVD (replay --nvd, off by default) (Tested with sample data)
- patchowner watch: notices new since the last run, one .eml per owner (Tested with sample data)

## Not done yet

- Three features are tested with sample data only: the in-page policy edit (example inventory; the earlier card left a move to Proven to the owner), `replay --nvd` (on the example inventory 0 notices fell outside NVD's range, so that path was not reached on any data the scorer ran; the 48 labelled rows carry no versions) and `watch` (example inventory; a withdrawn entry, --baseline and --every were not run, and there is no proof/ log for it)
- Colour contrast does not meet WCAG AA: 10 of 32 text pairs in the report are below 4.5:1, including every urgency tag in dark mode and the dark-mode eyebrow at 1.60:1; no skip link; no screen reader was run
- Not used by any organization: the one real inventory run is San Francisco's published list (floor b1); relevance is measured only on 48 synthetic labelled rows that were used to write the name rules, and proof/real-software-list.log (2026-11-08) predates those rules
- No PyPI release, no GitHub release and no installer; running it needs uv; the source repository is private
- Docs drift at 44d7928: README still says "Only verified, relevant, actionable" and "97 passed, 4 skipped on 2026-10-30", its layout omits watch, SECURITY.md says nothing about the optional NVD call, and watch emails still say "PatchOwner"
- Most proof/ logs (77 of 87) were recorded at 34e7d97, not at 44d7928; five change-records stay at older commits pending the owner (WO-09 items 14 and 16), and proof/python-egress-strace.log (2026-11-08) does not cover --nvd or watch
- Browser runs use Playwright's engines and phone profiles: Safari itself, Edge, a real phone and a screen reader speaking were not run
- No import into a real ticket or issue tool was run, and no one-page sheet was printed on paper or read by an owner
- certifi PYSEC-2026-4320 unpatched in the dev dependencies (via httpx); the runtime set has no known advisory

## What changed

- 2026-11-18: A review at commit 167ffcd found EPSS input (from a file you supply; it reorders notices within one urgency level) and ticket and issue export built, with their tests passing, so both targets were removed from Where it's going. The same review ran pytest: 787 passed, 127 skipped. No feature label or score changed.
- 2026-11-11: Merged into the product: the report can now give each owner a one-page notice to check and print or save as a PDF, and the browser test server picks a new port when the first one is taken. These were checked by path and by the pull request text, not run here, so no feature label or score changed (PRs #126 and #131). Scorecard row: "CLI replay of CISA KEV over inventory CSV -> HTML report" (works true, Proven) covers the report as a whole; the one-page notice and the test-server change are not scored (no row covers them).
- 2026-11-11: Merged into the product: open notices can be saved as files for other tools (a ticket file and issue files), with tests that open the report in a browser. No feature label or score changed (PRs #121, #124 and #122).
- 2026-11-10: Land PR #120 merged into main as bc77d9e (16 lane PRs included); no feature label changed this round. Tagged v0.4.0 at bc77d9e.
- 2026-11-08: Action-buttons proof log now states its exit code and was re-recorded at current main (PR #116; tag v0.3.0). Feature 6 is proven; 7 of 8 features proven. 84/100 on our own rubric. CI on main completed success on f82c327 and ab77bb6.
- 2026-11-08: Proof logs merged for the core features (PRs #33, #34, #35, #37, #38, #39, #40, #44, #50; tag v0.2.0). Features 1, 2, 3, 4, 5 and 8 were proven (a log on main with date, commit, command, exit code); features 6 and 7 stayed built, tested with sample data at that point because their logs carried no exit code line. 83/100 on our own rubric.

See [CHANGELOG](CHANGELOG.md).

## Demo

[Watch it work](https://shipitworks.com/patchowner/) on the product page · [Transcript](https://shipitworks.com/patchowner/transcript/)

The demo voice is AI-generated (ElevenLabs, "Bella") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/patchowner/) is the source of truth, and the score above is the one to trust.

## How I work

I say only what I can back. I say what is not finished before anyone asks. I name people, companies and tools to give credit. I collect as little data as possible. Built with Claude, by Anthropic: Claude helps write the code and wrote this README. Directed, tested and owned by Robert Sweetman in Stoughton, Massachusetts.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.
