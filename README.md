# patchowner

Turns the CISA KEV catalog into vulnerability notices routed to the owner of an affected item. Built, tested with sample data on a sample inventory; relevance is not measured and it has not been tried on a real inventory.

**Score: 83 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-01; this record was updated 2026-11-07 from the [product page](https://shipitworks.com/patchowner/).

Every number on the product page names the file it came from. The lists below are copied from that page, not rewritten.

**Platform.** Command line and web (Python; runs with uv). Live demo at patchowner.com.

## What works today

- CLI replay of CISA KEV over inventory CSV -> HTML report
- Web upload demo (patchowner serve)
- SSVC deployer tree, default SEI policy, custom --policy CSV
- Matching tiers, suppression, budget, routing
- Health tab (README says eleven checks)
- Live demo patchowner.com

## Not done yet

- No release tag at all: git tag is empty at HEAD 1e523ef, so no version has ever been tagged
- No PyPI release and no installer; running it needs uv
- No CLI tests (cli.py is not exercised directly)
- Browser button clicks, the localStorage fallback and the in-page policy edit have no JS tests and were not run in a browser
- Live site content freshness versus the template was not checked
- README's 'eleven checks' count does not match health.py (~12 Check( sites)
- certifi PYSEC-2026-4320 unpatched (dev-only, via httpx); a11y gaps: no focus styles, no reduced-motion, tabs lack role=tab

## What changed

Nothing merged to the default branch of the private source repository in the 2026-11-07 close-out.

- 2026-11-07: Corrected the one-line description. It said "Only verified, relevant, actionable ... notices"; no measure of relevance exists and the run covers a sample inventory only. The line now says what ran and the stage. See [CHANGELOG](CHANGELOG.md).

## Demo

[Demo video (1:52) on the product page](https://shipitworks.com/patchowner/) · [Transcript](https://shipitworks.com/patchowner/transcript/)

The demo voice is AI-generated (ElevenLabs, "Alice") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/patchowner/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.
