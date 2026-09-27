# STUDYBLITZ — MASTER DEVELOPMENT PROMPT

You are the primary software engineer responsible for building **StudyBlitz**, a production-ready web application for learning, practicing, reviewing, and mastering educational content.

Do not treat this as a demo, mockup, or throwaway prototype.

Build the application with a clean, scalable architecture that can grow from an initial educational website into a large study platform.

---

# 1. PRODUCT

Product name:

**StudyBlitz**

Core positioning:

> StudyBlitz is a study engine that turns structured educational content into multiple ways of learning, practicing, and remembering.

Core learning loop:

**Find / Import / Create → Learn → Practice → Review → Master**

Core architectural principle:

> **One learning dataset → many study experiences.**

A single structured educational dataset should be reusable for:

* public topic pages
* explanations
* definitions
* flashcards
* quizzes
* written recall
* image occlusion
* future study modes
* search
* related topics
* learning progress

Do not create separate disconnected content systems for each study mode.

---

# 2. TARGET USERS

Primary audiences:

* K-12 students
* secondary/high-school students
* college/university students
* teachers
* independent learners

The interface should be understandable without users knowing the internal architecture.

Do not expose technical concepts such as "knowledge graph", "content pipeline", or "AI ingestion" to normal students unless necessary.

---

# 3. HOMEPAGE

The homepage should be user-centered rather than module-centered.

Primary experience:

> **What do you want to study?**

Provide:

* topic search
* Study
* Create/import
* Join shared study set
* Continue studying
* Recent study sets
* Popular topics
* Bring your own material

Supported material entry points:

* Notes
* PDF
* Image
* Text
* Topic
* Import

The homepage must work well on mobile and desktop.

---

# 4. APPLICATION ARCHITECTURE

Use:

* React
* TypeScript
* Vite
* Firebase

Firebase services:

* Authentication
* Firestore
* Cloud Storage
* Cloud Functions
* Hosting
* App Check
* Analytics
* Emulator Suite

Use a modular architecture with reusable components and services.

Keep:

* UI
* domain logic
* data access
* authentication
* content processing
* AI integration
* storage
* billing
* advertising

properly separated.

Do not place business logic throughout random UI components.

---

# 5. DESIGN SYSTEM

Create a consistent StudyBlitz design system.

Requirements:

* clean
* modern
* educational
* responsive
* accessible
* fast
* mobile-first
* light and dark themes
* reusable components
* CSS variables/design tokens

Create reusable components for:

* buttons
* cards
* inputs
* dialogs
* menus
* navigation
* progress indicators
* loading states
* error states
* empty states
* study controls

Avoid unnecessary visual complexity.

The interface should feel like a serious study platform rather than an advertising website.

---

# 6. CONTENT MODEL

StudyBlitz has four conceptual layers.

## Layer 1 — Source material

Examples:

* StudyBlitz official research
* educational sources
* user notes
* PDFs
* images
* pasted text
* imports
* community material

## Layer 2 — Knowledge content

Examples:

* topics
* concepts
* definitions
* explanations
* questions
* answers
* formulas
* examples
* misconceptions
* diagrams
* references

## Layer 3 — Study experiences

Examples:

* flashcards
* quiz
* written recall
* true/false
* rapid exam
* image occlusion

Future experiences must be able to reuse the same underlying knowledge.

## Layer 4 — Learning data

Examples:

* confidence
* mastery
* review history
* weak concepts
* review queue
* study sessions
* goals
* exam dates

Keep educational content and individual learning progress separate.

---

# 7. OFFICIAL VS COMMUNITY CONTENT

StudyBlitz must distinguish:

### Official StudyBlitz content

Curated and reviewed educational content.

### Community Study Sets

Created by users.

Community content must NOT automatically become official StudyBlitz content.

Use publishing states such as:

* draft
* processing
* review
* approved
* published
* archived

Design the database so content can be versioned.

Updating an educational dataset must not destroy existing student progress.

---

# 8. STUDYBLITZ CONTENT ACQUISITION ENGINE

This is a core part of the long-term architecture.

StudyBlitz should eventually have an internal admin/content console for building the official educational library.

The purpose is NOT continuous AI generation for every student.

The purpose is:

> **AI-assisted research, collection, curation, structuring, gap analysis, and content preparation.**

The administrator should be able to create a content acquisition job.

Example:

```text
Subject:
Biology

Starting sources:
Source A
Source B
Source C

Target:
Common school
→ secondary
→ advanced secondary
→ college/university
```

The content engine should support this conceptual pipeline:

```text
Administrator
      ↓
Content acquisition job
      ↓
Curriculum/topic mapping
      ↓
Approved sources
      ↓
Research/collection
      ↓
Knowledge extraction
      ↓
Deduplication
      ↓
Cross-source checking
      ↓
Coverage analysis
      ↓
Gap identification
      ↓
Additional reputable sources
      ↓
Structured StudyBlitz content
      ↓
Validation
      ↓
Human review
      ↓
Published official content
```

The engine must maintain provenance.

For every collected source, store appropriate metadata such as:

* source URL
* source title
* source/domain
* collection date
* topic
* relevant section
* licensing/reuse information when available
* processing status

Do not blindly copy entire websites into StudyBlitz.

Do not reproduce copyrighted text or media verbatim unless reuse is legally permitted.

Prefer synthesizing factual knowledge into original StudyBlitz explanations while retaining source references.

Flag licensing/copyright concerns for human review.

---

# 9. COVERAGE ENGINE

The content system must be designed around coverage rather than simply collecting as much material as possible.

Example:

```text
Biology

Cell Biology       95%
Genetics            90%
Photosynthesis     100%
Ecology             80%
Biotechnology       35%
```

The system should be able to identify:

* complete topics
* partially covered topics
* missing topics
* duplicate coverage
* conflicting information
* topics requiring additional sources

Then additional research can target gaps.

Do not repeatedly collect the same information from multiple websites when adequate coverage already exists.

---

# 10. EDUCATIONAL COVERAGE STRATEGY

Build breadth first.

Priority:

### Level 1

Common school subjects:

* Mathematics
* English
* Science
* Biology
* Chemistry
* Physics
* Computer Science
* History
* Geography
* Economics

### Level 2

Advanced/secondary topics.

### Level 3

College/university foundations.

### Level 4

Specialized university subjects.

The content system must support expansion without requiring database redesign.

---

# 11. STRUCTURED AI OUTPUT

AI-generated content must be structured.

Do NOT rely on giant free-form paragraphs.

Conceptually:

```text
Topic
 ├── metadata
 ├── concepts
 ├── definitions
 ├── explanations
 ├── examples
 ├── formulas
 ├── misconceptions
 ├── flashcards
 ├── questions
 ├── diagrams
 └── references
```

AI output must pass:

1. schema validation
2. sanitization
3. content validation
4. provenance validation
5. publishing checks

AI must not have unrestricted direct write access to production content.

Preferred pipeline:

```text
AI
 ↓
Structured output
 ↓
Schema validator
 ↓
Sanitizer
 ↓
Draft
 ↓
Human review
 ↓
Published database
```

---

# 12. FIRESTORE ARCHITECTURE

Use Firestore for structured educational data and metadata.

Use Cloud Storage for:

* PDFs
* large images
* diagrams
* user uploads
* other large media

Conceptual structure:

```text
topics/{topicId}

studySets/{studySetId}

studySets/{studySetId}/content/{contentId}

users/{uid}/progress/{contentId}

users/{uid}/sessions/{sessionId}

users/{uid}/goals/{goalId}

users/{uid}/preferences/settings

subscriptions/{uid}

publicStudySets/{shareCode}
```

Do not blindly create one Firestore document/read for every flashcard.

Optimize document structure and reads.

Small datasets may be embedded/chunked.

Large datasets should be split appropriately.

A normal study session should require a small number of efficient reads rather than one network request per card.

---

# 13. USER PROGRESS

User learning data is private.

Example:

```text
One Biology deck
 ├── User A progress
 ├── User B progress
 └── User C progress
```

Educational content can be shared.

Progress must remain user-specific.

Track:

* confidence
* mastery
* correct/incorrect answers
* review history
* weak concepts
* sessions
* completion
* review scheduling

Do not store user progress inside shared educational content documents.

---

# 14. STUDY ROOM

Build a unified Study Room.

Structure:

```text
Study Room
 ├── Header
 ├── Subject/topic
 ├── Mastery
 ├── Progress
 ├── Mode selector
 ├── Active experience
 └── Controls
```

Modes should be pluggable.

Initial modes:

* Flashcards
* Quiz
* Recall

Later:

* Image Occlusion
* Rapid Exam
* adaptive modes
* other experiences

The Study Room should not need to be rewritten whenever a new study mode is added.

---

# 15. FLASHCARDS

Implement:

* front/back
* 3D flip
* images
* LaTeX
* explanation
* confidence 1–5
* progress
* keyboard shortcuts
* touch controls
* mastery tracking

Confidence:

```text
1 = Didn't know
2 = Very weak
3 = Somewhat knew
4 = Knew
5 = Easy
```

Mastery states:

```text
New
Learning
Weak
Developing
Strong
Mastered
```

Confidence must feed future review scheduling.

---

# 16. QUIZ

Initial question types:

* multiple choice
* true/false
* fill in the blank

Later:

* written answers
* adaptive questions

When an answer is wrong, show:

* correct answer
* explanation
* review concept
* study again

Question generation should eventually prefer meaningful semantic distractors rather than random unrelated answers.

---

# 17. IMAGE OCCLUSION

Initial implementation:

```text
Upload diagram
 ↓
Canvas
 ↓
Draw masks
 ↓
Assign answers
 ↓
Save
```

Later:

```text
Image
 ↓
AI detects labels
 ↓
User confirms
 ↓
Automatic occlusion cards
```

Design the data model now so AI-assisted detection can be added later without breaking manual occlusion.

---

# 18. PUBLIC TOPIC PAGES / SEO

Create indexable topic pages.

Example:

```text
/topics/photosynthesis
/topics/cell-structure
/topics/newtons-laws
```

A topic page should contain:

* title
* description
* educational explanation
* concepts
* definitions
* diagrams
* formulas where appropriate
* common questions
* references
* related topics
* Study button

The page should function both as:

1. a useful educational/reference page
2. an entry point into the Study Room

Do not make public topic pages merely temporary AI notes.

Interactive Study Room functionality can be client-side, but important public topic content must be indexable.

---

# 19. SHARING

Use a six-character study-set code.

Example:

```text
studyblitz.app/play?deck=MX49B2
```

Flow:

```text
URL
 ↓
detect code
 ↓
fetch public study set
 ↓
validate
 ↓
load
 ↓
Study Room
```

Test:

* valid code
* invalid code
* private set
* unpublished set
* deleted set
* abuse/rate limits

---

# 20. USER IMPORT

Users can provide:

* text
* notes
* PDF
* image

Pipeline:

```text
User upload
 ↓
Cloud Storage
 ↓
Extraction
 ↓
AI processing
 ↓
Structured content
 ↓
Validation
 ↓
Private/community study set
```

Do not mix private user material with official content.

---

# 21. AI RUNTIME

AI provider credentials must NEVER be exposed to the frontend.

Use:

```text
Browser
 ↓
authenticated backend
 ↓
Cloud Function/backend
 ↓
AI provider
 ↓
validated structured result
 ↓
Firestore/Storage
```

AI should NOT run for every normal study action.

Normal:

```text
Open flashcard
 ↓
Firebase
 ↓
Study locally
 ↓
Save progress
```

AI-heavy operations should primarily be:

* official content acquisition
* user material transformation
* explanations where necessary
* future intelligent study features

Implement usage limits and abuse protection.

---

# 22. ADS

Free users:

* normal top banner
* fixed bottom banner

Top advertisement:

* normal scrollable banner

Bottom advertisement:

* fixed to viewport
* always visible
* not placed over important controls/content

Reserve sufficient bottom safe space.

Never hide important study content behind the fixed advertisement.

No:

* popup ads
* intrusive study interruptions
* ads over quiz answers
* ads over flashcard controls
* misleading advertisement UI

Plus users:

* no ads
* no ad placeholder
* no unnecessary reserved ad space

---

# 23. MONETIZATION

Free is the primary product.

Plus is secondary.

Target:

```text
$2.99/month
$24.99/year
```

Main benefit:

**Remove advertisements.**

Do not cripple core learning functionality merely to force Plus subscriptions.

Do not implement a payment provider until the supported provider/business setup is confirmed.

Keep subscription logic abstract enough to support the final provider.

---

# 24. PERFORMANCE

Prioritize performance because StudyBlitz may eventually contain a large educational library.

Use:

* code splitting
* lazy loading
* browser caching
* efficient Firestore queries
* CDN delivery
* optimized images
* WebP/AVIF where appropriate
* responsive images
* avoid loading diagrams until needed
* avoid unnecessarily large JavaScript bundles

Target approximately:

**0.5–1 MB page transfer where practical.**

Do not load the entire educational library into the browser.

---

# 25. SECURITY

Implement security from the beginning.

Requirements:

* Firebase Security Rules
* authentication checks
* ownership checks
* admin authorization
* Storage Rules
* App Check
* rate limiting
* abuse prevention
* validation
* sanitized user content
* AI request limits

Use the Firebase Emulator Suite for development.

Never use permissive production rules merely to make development easier.

---

# 26. TESTING

Use:

* unit tests
* component tests
* integration tests
* Firebase Emulator Suite
* end-to-end/browser testing

Test especially:

* authentication
* permissions
* user isolation
* content publishing
* sharing
* progress
* study sessions
* AI validation
* imports
* advertisements
* Plus ad suppression
* responsive layouts

---

# 27. DEVELOPMENT MILESTONES

Implement in this order.

### M0

Product and architecture foundation

### M1

React/TypeScript/Vite project foundation

### M2

Firebase, authentication, security, emulator

### M3

Core content/data model

### M4

**Content Acquisition Engine**

### M5

Initial official educational library

### M6

SEO/public topic pages

### M7

Study Room framework

### M8

Flashcards

### M9

Quiz

### M10

Progress/mastery/review system

### M11

Sharing/community study sets

### M12

Image occlusion

### M13

User PDF/notes/image/text import

### M14

AI runtime/backend integration

### M15

Free/Plus monetization

### M16

Advertising

### M17

Teacher foundation

### M18

Production hardening/deployment

Do not skip directly to later milestones just because the UI looks attractive.

---

# 28. CODING RULES

Before modifying the project:

1. Inspect the existing repository.
2. Understand existing files and architecture.
3. Do not overwrite working functionality unnecessarily.
4. Reuse existing components when appropriate.
5. Keep changes modular.
6. Do not create duplicate systems.
7. Do not add dependencies without a reason.
8. Prefer maintainable solutions over hacks.
9. Keep types strict.
10. Handle loading/error/empty states.
11. Test important behavior.
12. Keep security rules aligned with the data model.

When a feature is complete, verify it before moving to the next milestone.

Do not merely report that code was written.

---

# 29. IMPORTANT PRODUCT PRINCIPLE

Never lose sight of this:

> **StudyBlitz is not an AI chatbot with study features.**

It is a **study platform with a structured educational knowledge base**, where AI is used primarily to help build, curate, transform, and improve that knowledge base.

The educational dataset is the foundation.

One dataset should power many study experiences.

---

# 30. FIRST TASK

Do NOT immediately build the entire application.

First inspect the repository and environment.

Determine:

* current project state
* existing files
* installed dependencies
* Firebase configuration
* current architecture
* available tooling
* whether anything already exists that should be preserved

Then create a concise implementation plan for **Milestone 0 and Milestone 1**.

Do not make major architectural changes until the repository has been inspected.

After inspection, begin with the foundation and proceed milestone by milestone.

Always keep the architecture compatible with the complete StudyBlitz vision described above.
