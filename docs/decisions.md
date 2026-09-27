# StudyBlitz Architecture Decisions

This document records important decisions so future development does not accidentally reverse them.

## ADR-001 — One Dataset, Multiple Study Modes

Decision:
A structured educational dataset powers multiple study experiences.

Reason:
Avoid duplicated content and allow new study modes to reuse existing material.

Status:
Accepted.

## ADR-002 — AI Is Primarily a Content/Transformation Tool

Decision:
AI is not required for ordinary flashcard and quiz sessions.

AI is primarily used for:
- official content acquisition
- research assistance
- curation
- user material transformation
- future intelligent features

Reason:
Reduces runtime cost and makes normal studying fast and predictable.

Status:
Accepted.

## ADR-003 — Official Content Requires Review

Decision:
AI-generated or externally collected content does not automatically become official content.

Lifecycle:

```text
Collected
→ Processing
→ Draft
→ Review
→ Approved
→ Published
```

Reason:
Educational accuracy, source verification, licensing, and quality control.

Status:
Accepted.

## ADR-004 — Source Provenance Is Required

Decision:
Official content should retain source information.

Reason:
Allows verification, attribution, maintenance, and auditing.

Status:
Accepted.

## ADR-005 — Do Not Blindly Republish Scraped Material

Decision:
External websites are research inputs, not automatic republishing sources.

Reason:
Public accessibility does not automatically grant republication rights.

Prefer original StudyBlitz synthesis and appropriately licensed media.

Status:
Accepted.

## ADR-006 — Breadth-First Educational Library

Decision:
Build common educational subjects before highly specialized university topics.

Reason:
Provides useful coverage to the largest number of learners and exposes gaps early.

Status:
Accepted.

## ADR-007 — Official, Community, and Private Content Are Separate

Decision:
Keep:
- Official StudyBlitz content
- Community study sets
- Private user material

logically separated.

Reason:
Different trust, privacy, publishing, and security requirements.

Status:
Accepted.

## ADR-008 — User Progress Is Separate From Shared Content

Decision:
Progress is stored per user and references stable content identifiers.

Reason:
Many students can use the same content while maintaining independent mastery.

Status:
Accepted.

## ADR-009 — Firebase Is the Initial Backend

Decision:
Use Firebase for:
- Authentication
- Firestore
- Storage
- Functions
- Hosting
- App Check
- Analytics

Reason:
Fast initial development and a scalable managed backend.

Status:
Accepted.

## ADR-010 — Fixed Bottom Advertisement

Decision:
Free users have a fixed bottom banner advertisement.

The application must reserve safe space so content is never hidden behind it.

Plus users receive no advertisements.

Status:
Accepted.

## ADR-011 — Plus Is Mainly Ad Removal

Decision:
The free product remains useful.

Plus primarily removes advertisements.

Initial target pricing:
- $2.99/month
- $24.99/year

Status:
Accepted.

## ADR-012 — Six-Character Share Codes

Decision:
Public study sets use six-character share codes.

Example:

```text
/play?deck=MX49B2
```

Reason:
Easy to share verbally and visually.

Status:
Accepted.

## ADR-013 — Admin Content Console

Decision:
The official content pipeline should eventually have an authenticated admin console.

Reason:
Content acquisition is an ongoing editorial process and should not require direct database manipulation.

Status:
Accepted.

## ADR-014 — Cline Development Workflow

Decision:
Development is currently performed in VS Code using Cline with OpenRouter models.

Development should be milestone-based and controlled.

Recommended loop:

```text
Inspect
→ Plan
→ Implement one milestone
→ Test
→ Review
→ Commit
```

Status:
Accepted.

## ADR-015 — Do Not Over-Automate Too Early

Decision:
The first official content library can be created using external AI research tools and human review.

The fully automated StudyBlitz acquisition engine can be implemented progressively.

Reason:
Avoid building complex automation before the content schema and quality workflow are proven.

Status:
Accepted.
