# Contributing to BBRF-PT

This guide describes a small, reviewable contribution process for the BBRF-PT site. Start with documentation and modest usability improvements; keep investment decisions with the project principals.

## Source of truth

**Decided.** https://eytan.com/pitches/bbrf-pt.html is the canonical source for BBRF-PT content. This repository is a *generated mirror* of that content, packaged as a portable static bundle. GitHub is not a separate source of truth: eytan.com is itself a GitHub repository, so the distinction that matters is which repository owns these pages, and that is the eytan.com repository.

What that means for contributions here:

- Investor-facing content and investment copy change on eytan.com first and are then synced into this repository. Pull requests that rewrite that content here will be redirected rather than merged.
- Mirror-side work belongs here: documentation, packaging and relative-link correctness, bounded accessibility and usability fixes, and the ENS/IPFS deployment path.
- The mirror is not a byte-for-byte copy. eytan.com serves the pitch from `/pitches/` with shared assets at the site root and so uses absolute asset paths, while this bundle must stay root-relative to work from any directory or IPFS CID. Syncing a page includes rewriting `/properties/pebble-stone/...` to `properties/pebble-stone/...`.
- The editable PDF layout sources (`*-pdf-source.html`) and the generator (`generate-bbrf-pdf.js`) live in the eytan.com repository, not here. Only the exported memoranda are committed here, so a PDF cannot be revised from this repository alone.

## Before starting

Read the [README](README.md), this guide, and any existing issue or pull request for the same change (this repository uses Issues; Discussions are disabled). Confirm the audience, language, problem, and intended outcome.

Ask before changing substantive content when the answer is uncertain, especially:

- What investors contribute, receive, or can redeem.
- Return assumptions, fees, valuation, borrowing currency, collateral policy, or risk disclosures.
- Entity status, provider appointments, acquisition status, or readiness claims.
- Which audience and language versions should change, and who will verify translations.
- Whether a contact action should open email, download a document, or book a meeting.

Do not invent missing product facts or silently resolve contradictory investment claims. Record the question and prepare the unaffected work. A documentation-only scope does not authorize site code changes.

## Keep contributions small

Use one pull request per coherent outcome. Suitable early contributions include documentation, accurate link labels, navigation to existing content, and bounded accessibility fixes. Separate restructuring, calculators, investment copy, translation rewrites, and infrastructure changes into their own proposals.

Avoid unrelated formatting churn, new dependencies without a clear need, or changes to established URLs. Preserve the static, self-hosting bundle and relative internal links so it continues to work below a directory root or IPFS path.

## Branch and pull request workflow

1. Fork the repository and start a descriptive branch from the latest upstream `main`, such as `docs/contribution-guide` or `fix/contact-labels`.
2. Make the smallest change that addresses the agreed problem. Keep local planning notes, credentials, and unrelated files out of the commit.
3. Review the complete diff and validate the affected behavior. State any checks you could not perform.
4. Open a pull request from your fork to `benzenoe/bbrf-pt-eth:main`. Use a draft for unresolved policy proposals or incomplete validation; explain what is needed before it is ready.
5. Resolve the maintainer's review feedback on the same branch. Do not merge or publish on the maintainer's behalf unless separately authorized.

Use your own GitHub identity and accurate commit attribution. Do not push contributions directly to upstream `main`, and do not merge your own pull request. `main` is intentionally left unprotected, so these are honor-system rules rather than enforced ones.

## Audience, language, and document consistency

The bundle has crypto-investor, traditional-investor, and real-estate-partner pages in English, French, and Portuguese, plus the entry page, memoranda, and pilot-property materials.

For each change, identify which copies are affected. `index.html` is a hand-maintained copy of `bbrf-pt.html`; a change to either must be applied to both in the same pull request. Keep meaning, link destinations, audience selection, and language switching consistent across the affected variants. If translation or PDF updates are deferred, name them explicitly and obtain the maintainer's agreement before merging content that would leave conflicting versions.

Do not edit investment terms merely to simplify wording. Preserve the approved meaning and obtain confirmation of substantive changes. PDF revisions cannot be made here: raise them against the eytan.com repository, which holds the editable layout sources and the generator. A regenerated PDF synced into this repository should carry a version/date and a visual review of the exported file.

## Validation proportional to the change

For documentation-only changes, check spelling, relative links, consistency with existing instructions, and the final diff. No application tests are needed for a prose-only contribution.

For site changes, inspect the relevant pages and paths:

- Desktop and narrow/mobile layouts, including long text and navigation.
- Keyboard access, visible focus, meaningful labels, and readable content.
- Audience selection, language switching, anchors, and return navigation.
- Contact links, download destinations, and the behavior promised by their labels.
- Relative links and assets when the site is served below a path prefix.
- Any affected charts or calculators, including initial state and unavailable data.

Preview locally before submitting: run `python3 -m http.server 8000` from the repository root, then run it again from the parent directory and open `/bbrf-pt-eth/` to confirm nothing depends on being at a domain root.

Include before/after screenshots for visible changes when possible. Run existing relevant checks if present; add tests only when they meaningfully protect behavior. Do not report a check as passed unless it was performed. Avoid submitting real inquiries or transactions as a test.

## Pull request description

Give the reviewer enough context to assess the final change without reading prior conversations:

- **Problem and result:** what was confusing or missing, and how the change helps.
- **Scope:** affected pages, audiences, languages, and documents.
- **Validation:** checks performed and relevant screenshots.
- **Open decisions:** specific questions, assumptions, or deferred consistency work.
- **Publication impact:** whether the change affects only documentation or requires a site release and synchronization.

For small documentation changes, a few short paragraphs are sufficient.

## Review and publishing

The maintainer (Eytan Benzeno), or someone he designates, decides acceptance and publication. A merged contribution and a verified release are normally separate outcomes, with one exception that matters here:

- **GitHub Pages is live and publishes on merge.** This repository is served from `main` at the root to https://benzenoe.github.io/bbrf-pt-eth/. Merging republishes that public site immediately, with no further approval step, so treat every merge as a publication.
- **The ENS/IPFS deployment is pending.** `bbrf-pt.eth` does not currently resolve and no automatic pinning is connected. The README runbook describes intended steps, not the present state; do not describe the on-chain site as live.

Contributors should not change hosting settings, IPFS pins, ENS records, or deployment credentials as part of a usability contribution. After an authorized release, record the source revision and verify the affected published destinations. If a regression occurs, propose a focused revert or fix through the same review process.
