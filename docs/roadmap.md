# StudyBlitz Development Roadmap

## Project Goal

Build a scalable educational study platform where one structured knowledge base powers multiple learning experiences.

## Milestone 0 — Product and Architecture

Deliver:
- product specification
- architecture
- data model
- security plan
- content pipeline
- roadmap
- design tokens

Exit criteria:
- architecture documented
- major decisions recorded
- no unresolved critical structural conflicts

## Milestone 1 — Project Foundation

Build:
- React
- TypeScript
- Vite
- routing
- styling/design system
- themes
- reusable components
- development tooling
- testing foundation

Exit criteria:
- app runs locally
- build succeeds
- lint/type checks work
- basic responsive shell exists

## Milestone 2 — Firebase Foundation

Build:
- Firebase configuration
- Authentication
- Firestore
- Storage
- Cloud Functions
- Emulator Suite
- App Check planning
- security rules

Exit criteria:
- authenticated test user works
- database reads/writes work
- rules are tested
- local emulator workflow works

## Milestone 3 — Core Data Model

Build:
- topics
- concepts
- flashcards
- questions
- references
- study sets
- progress
- sessions
- versioning foundations

Exit criteria:
- one topic can power multiple experiences
- user progress is isolated

## Milestone 4 — Content Acquisition Engine

Build admin/content tools for:
- acquisition jobs
- source registration
- topic mapping
- collection status
- coverage tracking
- gap identification
- provenance
- draft/review/publish workflow

Exit criteria:
- a sample subject can be processed from source registration to draft content
- content provenance is preserved

## Milestone 5 — Initial Official Library

Use the acquisition process to create the first broad content set.

Order:
1. Common school subjects
2. Secondary/advanced school
3. University foundations
4. Specialized university topics

Exit criteria:
- useful initial topic library exists
- quality review process works

## Milestone 6 — Public Topic Pages

Build:
- SEO-friendly routes
- topic pages
- explanations
- references
- related topics
- Study button

Exit criteria:
- public topic content is indexable
- topic pages work on mobile and desktop

## Milestone 7 — Study Room

Build:
- study room shell
- mode selector
- progress header
- reusable controls
- loading/error states

Exit criteria:
- study modes can be added without rebuilding the shell

## Milestone 8 — Flashcards

Build:
- 3D flip
- images
- LaTeX
- confidence 1–5
- mastery
- keyboard/touch controls

Exit criteria:
- full flashcard session works
- progress persists

## Milestone 9 — Quiz

Build:
- multiple choice
- true/false
- fill blank
- scoring
- explanations
- review incorrect answers

Exit criteria:
- complete quiz session works

## Milestone 10 — Progress and Review

Build:
- mastery
- weak concepts
- review queue
- study history
- session tracking
- goals

Exit criteria:
- user can see and resume meaningful progress

## Milestone 11 — Sharing

Build:
- six-character codes
- public study sets
- direct `/play?deck=` loading
- validation
- sharing states

Exit criteria:
- shared study set opens directly into Study Room

## Milestone 12 — Image Occlusion

Build:
- image upload
- canvas
- manual masks
- answer labels
- study mode

Later:
- AI-assisted mask detection

## Milestone 13 — User Import

Build:
- text
- PDF
- image
- notes
- extraction
- AI structuring
- private study sets

## Milestone 14 — AI Runtime

Build secure backend AI integration for:
- user material processing
- content workflows
- future intelligent features

Do not expose API keys.

## Milestone 15 — Plus

Implement:
- monthly subscription
- annual subscription
- subscription state
- ad removal

Target price:
- $2.99/month
- $24.99/year

Final payment provider must be selected before production billing implementation.

## Milestone 16 — Advertising

Implement:
- top banner
- fixed bottom banner
- reserved bottom safe space
- Plus ad suppression

No intrusive popups.

## Milestone 17 — Teacher Foundation

Prepare:
- teacher accounts
- classes
- study assignments
- class codes

Avoid building a full LMS unless later required.

## Milestone 18 — Production Hardening

Complete:
- security audit
- performance optimization
- SEO audit
- accessibility
- browser testing
- mobile testing
- backup/recovery
- monitoring
- deployment
- production configuration

## Development Rule

Do not implement multiple major milestones in one uncontrolled change.

For each milestone:

```text
Inspect
  ↓
Plan
  ↓
Implement
  ↓
Test
  ↓
Review
  ↓
Commit
  ↓
Next milestone
```
