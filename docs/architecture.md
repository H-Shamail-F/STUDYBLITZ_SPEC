# StudyBlitz Architecture

## 1. Purpose

StudyBlitz is a web-based study platform for K-12, higher education, teachers, and independent learners.

The central architectural principle is:

> One structured educational dataset powers many study experiences.

The same underlying topic/content should be usable for:
- Public topic/reference pages
- Flashcards
- Quizzes
- Recall exercises
- Image occlusion
- Rapid exam mode
- Future study modes
- Search and related topics
- Learning progress

## 2. Technology Direction

Initial stack:
- React
- TypeScript
- Vite
- Firebase
- Cline + OpenRouter for development

Firebase services:
- Authentication
- Firestore
- Cloud Storage
- Cloud Functions
- Hosting
- App Check
- Analytics
- Emulator Suite

Keep the application modular so services can be replaced or expanded later.

## 3. High-Level Architecture

```text
Browser
  |
  v
React / TypeScript SPA
  |
  +--> Public topic pages
  +--> Study Room
  +--> User dashboard
  +--> Shared study sets
  +--> Admin/content console
  |
  v
Application services
  |
  +--> Authentication
  +--> Content service
  +--> Study/progress service
  +--> Sharing service
  +--> AI service
  +--> Billing service
  +--> Advertising service
  |
  v
Firebase
  +--> Firestore
  +--> Cloud Storage
  +--> Cloud Functions
  +--> Authentication
```

## 4. Content Architecture

There are three major content origins:

### Official content
StudyBlitz-curated educational material.

### Community content
Study sets created and shared by users.

### Private user material
Notes, PDFs, images, and text processed for an individual user.

These must remain logically separated.

## 5. AI Architecture

AI is primarily a content-production and transformation tool, not the core runtime for ordinary studying.

Official content pipeline:

```text
Sources
  |
  v
Research / collection
  |
  v
Extraction
  |
  v
Deduplication
  |
  v
Coverage analysis
  |
  v
Gap research
  |
  v
Structured content
  |
  v
Validation
  |
  v
Human review
  |
  v
Published content
```

User material pipeline:

```text
Upload
  |
  v
Storage
  |
  v
Extraction
  |
  v
AI structuring
  |
  v
Validation
  |
  v
Private/community study set
```

Normal flashcard/quiz use should not require an AI request.

## 6. Study Room

The Study Room is a reusable shell around pluggable study modes.

Initial modes:
- Flashcards
- Quiz
- Recall

Later:
- Image occlusion
- Rapid exam
- Adaptive study
- Additional modes

Each mode consumes the same structured educational content where possible.

## 7. Public Topic Pages

Public pages should be indexable and useful without entering the Study Room.

Example:

```text
/topics/photosynthesis
/topics/cell-structure
/topics/newtons-laws
```

A topic page should provide:
- Explanation
- Concepts
- Definitions
- Examples
- Formulas where relevant
- Diagrams where licensed/created
- References
- Related topics
- Study action

## 8. Direct Shared Deck URLs

Shared study sets use a six-character code.

Example:

```text
/play?deck=MX49B2
```

Initialization logic:
1. Parse the query string.
2. Detect `deck`.
3. Validate the code.
4. Fetch the public study set.
5. Load the study data.
6. Mount the Study Room directly.

If no deck parameter exists, load the normal application portal.

## 9. Performance Principles

- Lazy-load large features.
- Avoid loading the entire educational library.
- Optimize images.
- Cache appropriate public content.
- Minimize Firestore reads.
- Avoid one network request per flashcard.
- Use Cloud Storage for large files.
- Keep initial JavaScript bundles small.
- Reserve safe space for fixed advertisements.

## 10. Ads

Free users receive:
- Top scrollable banner ad.
- Fixed bottom banner ad.

The bottom ad must never cover important content or controls.

Plus users:
- No advertisements.
- No unnecessary ad placeholders.
- No unnecessary reserved ad space.

No popup or disruptive study-interruption advertising.

## 11. Development Rules

- Inspect existing code before changing it.
- Avoid destructive changes.
- Reuse existing components where appropriate.
- Keep domain logic out of presentation components.
- Validate external/AI data.
- Keep security rules synchronized with the data model.
- Test each milestone before proceeding.
