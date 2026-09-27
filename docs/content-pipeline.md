# StudyBlitz Content Pipeline

## 1. Purpose

The Content Pipeline builds and maintains the official StudyBlitz educational library.

AI is used primarily for:
- Research assistance
- Collection
- Extraction
- Classification
- Deduplication
- Cross-source comparison
- Gap analysis
- Structured content generation

AI is not required for ordinary student flashcard or quiz sessions.

## 2. Core Principle

Do not simply scrape and republish entire websites.

Use external educational sources as research inputs and preserve provenance.

Copyrighted text and media must not be republished unless reuse is permitted.

Prefer original StudyBlitz explanations synthesized from verified information.

## 3. Master Acquisition Workflow

```text
Administrator
    |
    v
Create acquisition job
    |
    v
Define subject + target levels
    |
    v
Provide starting sources
    |
    v
Build curriculum/topic map
    |
    v
Collect relevant source material
    |
    v
Extract knowledge
    |
    v
Deduplicate
    |
    v
Cross-check
    |
    v
Calculate coverage
    |
    v
Identify gaps
    |
    v
Research additional reputable sources
    |
    v
Repeat coverage analysis
    |
    v
Generate structured StudyBlitz content
    |
    v
Validate
    |
    v
Human review
    |
    v
Publish
```

## 4. Coverage Strategy

Build breadth-first.

### Level 1
Common school subjects:
- Mathematics
- English
- Science
- Biology
- Chemistry
- Physics
- Computer Science
- History
- Geography
- Economics

### Level 2
Advanced secondary/high-school content.

### Level 3
College/university foundations.

### Level 4
Specialized university subjects.

The system should prioritize missing high-value/common topics before obscure advanced topics.

## 5. Source Collection

A content job can start with multiple approved sources.

For each source, record:
- URL
- title
- domain
- collection date
- relevant subject/topic
- available licensing information
- extraction status

Respect:
- robots.txt and applicable site rules
- terms of service
- copyright
- rate limits
- access restrictions

Do not bypass technical access controls.

## 6. Knowledge Extraction

Extract structured knowledge such as:
- concepts
- definitions
- explanations
- examples
- formulas
- processes
- questions
- answers
- misconceptions
- relationships between concepts
- references

Do not treat every paragraph as an independent piece of knowledge.

## 7. Deduplication

When multiple sources discuss the same concept:

```text
Source A ----Source B -----+--> Unified concept
Source C ----/
```

Keep the useful source references while avoiding duplicate learner-facing content.

## 8. Cross-Checking

Important factual content should be cross-checked when practical.

Flag:
- contradictions
- unsupported claims
- unclear source material
- outdated information
- licensing uncertainty

Do not silently resolve significant factual conflicts without recording the basis for the decision.

## 9. Coverage Map

Each subject/topic should have a coverage state.

Example:

```text
Biology

Cell Biology       95%
Genetics            90%
Photosynthesis     100%
Ecology             80%
Biotechnology       35%
```

Coverage should help decide where additional research is needed.

## 10. Gap-Filling

If approved starting sources do not sufficiently cover a topic:

1. Identify the exact missing knowledge.
2. Search for additional reputable educational sources.
3. Record new sources.
4. Process the new material.
5. Recalculate coverage.
6. Continue until the configured target is met.

Do not endlessly search when adequate coverage has already been achieved.

## 11. StudyBlitz Content Generation

Generate original structured content:

```text
Topic
Concepts
Definitions
Explanations
Examples
Formulas
Misconceptions
Flashcards
Questions
References
```

The same dataset should power multiple study experiences.

## 12. Human Review

Official content lifecycle:

```text
collected
  ↓
processing
  ↓
draft
  ↓
review
  ↓
approved
  ↓
published
```

AI should not automatically make all material public.

## 13. Licensing and Copyright

For every source:
- preserve the source URL
- record known license information
- flag uncertain reuse rights
- do not copy copyrighted text verbatim without permission
- do not copy copyrighted images without permission
- prefer public-domain, openly licensed, or StudyBlitz-created media

Source attribution must be retained where required.

## 14. AI Output Contract

AI should return structured data matching a strict schema.

Never trust raw AI output directly.

```text
AI output
  ↓
JSON/schema validation
  ↓
Sanitization
  ↓
Content validation
  ↓
Draft
```

Invalid output should be rejected and retried or flagged.

## 15. Content Quality

Prefer:
- accurate
- clear
- concise
- educational
- age-appropriate
- source-traceable
- internally consistent
- reusable

Avoid:
- filler
- duplicated explanations
- unsupported claims
- copied source prose
- unnecessary verbosity
- fake citations

## 16. Future Automation

The initial content library can be built using external research tools and manual review.

Later, StudyBlitz can expose an authenticated backend workflow:

```text
Admin Console
    ↓
Content Job
    ↓
AI/Web Research
    ↓
Structured result
    ↓
Validation
    ↓
Draft
    ↓
Review
    ↓
Publish
```

AI provider keys must remain server-side.
