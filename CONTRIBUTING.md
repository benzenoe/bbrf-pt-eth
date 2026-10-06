# Contributing to BBRF-PT

This guide proposes a small, reviewable contribution process for the BBRF-PT site. Start with documentation and modest usability improvements; keep investment decisions with the project principals.

## Status and source of truth

**Proposed policy — awaiting Eytan's acceptance.** The current [README](README.md) identifies eytan.com as the content source and this repository as its on-chain mirror. That remains the documented process until the maintainer explicitly approves a transition.

The proposed model is:

- `benzenoe/bbrf-pt-eth` becomes the canonical, version-controlled source for site content and assets.
- Contributors submit changes through pull requests to `main`; Eytan or a maintainer he designates reviews and merges them.
- Published copies, including eytan.com and the on-chain site, are synchronized from an approved repository revision rather than edited independently.
- Before switching, the maintainer identifies the current authoritative copy, reconciles any newer content, confirms publishing destinations and ownership, and updates the README's source-of-truth and deployment instructions.
- The transition is complete only when the maintainer records that decision and the README reflects the agreed process. Adding this guide alone does not change hosting, automation, or publication behavior.

## Before starting

Read the README, this guide, and any existing discussion or pull request for the same change. Confirm the audience, language, problem, and intended outcome. For work with a contributor sponsor, resolve the sponsor's scope questions before submitting site code for Eytan's review.

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
5. Resolve Eytan's review feedback on the same branch. Do not merge or publish on the maintainer's behalf unless separately authorized.

Use your own GitHub identity and accurate commit attribution. Do not push contributions directly to upstream `main`.

## Audience, language, and document consistency

The bundle has crypto-investor, traditional-investor, and real-estate-partner pages in English, French, and Portuguese, plus the entry page, memoranda, and pilot-property materials.

For each change, identify which copies are affected. Check `index.html` and the corresponding English landing page for divergence. Keep meaning, link destinations, audience selection, and language switching consistent across the affected variants. If translation or PDF updates are deferred, name them explicitly and obtain the maintainer's agreement before merging content that would leave conflicting versions.

Do not edit investment terms merely to simplify wording. Preserve the approved meaning and obtain confirmation of substantive changes. PDF revisions should include their editable source when available, a version/date, and a visual review of the exported file.

## Validation proportional to the change

For documentation-only changes, check spelling, relative links, consistency with existing instructions, and the final diff. No application tests are needed for a prose-only contribution.

For site changes, inspect the relevant pages and paths:

- Desktop and narrow/mobile layouts, including long text and navigation.
- Keyboard access, visible focus, meaningful labels, and readable content.
- Audience selection, language switching, anchors, and return navigation.
- Contact links, download destinations, and the behavior promised by their labels.
- Relative links and assets when the site is served below a path prefix.
- Any affected charts or calculators, including initial state and unavailable data.

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

Eytan, or a maintainer he designates, decides acceptance and publication. A merged contribution and a verified release are separate outcomes. The README describes hosting setups that may publish on push; confirm the actual trigger before a merge or release, rather than assuming a merge has no deployment effect.

Contributors should not change hosting settings, IPFS pins, ENS records, or deployment credentials as part of a usability contribution. After an authorized release, record the source revision and verify the affected published destinations. If a regression occurs, propose a focused revert or fix through the same review process.
