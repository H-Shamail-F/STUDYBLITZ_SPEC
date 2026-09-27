# StudyBlitz Data Model

## 1. Principles

The data model must support:
- Official educational content
- Community study sets
- Private user material
- User progress
- Content versioning
- Source provenance
- AI processing
- Sharing
- Future study modes

Educational content and user progress must remain separate.

## 2. Core Educational Model

Conceptual structure:

```text
Subject
  |
  +--> Topic
        |
        +--> Concepts
        +--> Definitions
        +--> Explanations
        +--> Examples
        +--> Formulas
        +--> Misconceptions
        +--> Questions
        +--> Flashcards
        +--> Diagrams
        +--> References
```

A topic is the primary reusable educational unit.

## 3. Suggested Firestore Collections

```text
topics/{topicId}

studySets/{studySetId}

studySets/{studySetId}/content/{contentId}

users/{uid}

users/{uid}/progress/{contentId}

users/{uid}/sessions/{sessionId}

users/{uid}/goals/{goalId}

users/{uid}/preferences/{preferenceId}

publicStudySets/{shareCode}

contentSources/{sourceId}

contentJobs/{jobId}

contentVersions/{versionId}

subscriptions/{uid}
```

The exact structure may be adjusted after implementation analysis.

## 4. Topic

Conceptual fields:

```text
id
title
slug
subjectId
description
level
status
contentVersion
conceptIds
relatedTopicIds
references
createdAt
updatedAt
```

Possible status values:

```text
draft
review
approved
published
archived
```

## 5. Concept

```text
id
topicId
title
definition
explanation
examples
misconceptions
references
```

## 6. Flashcard

```text
id
topicId
type
front
back
explanation
mediaUrl
latex
confidenceScore
sourceReferences
```

Do not permanently store a user's changing mastery value inside the shared flashcard document.

## 7. Quiz Question

```text
id
topicId
type
prompt
options
correctAnswer
explanation
difficulty
sourceReferences
```

## 8. Image Occlusion

```text
id
topicId
imageUrl
canvasWidth
canvasHeight
masks:
  - id
    x
    y
    width
    height
    answer
```

Design the schema so AI-assisted mask detection can be added later.

## 9. User Progress

Progress belongs to the user.

Example:

```text
users/{uid}/progress/{contentId}
```

Fields may include:

```text
contentId
mastery
confidence
correctCount
incorrectCount
lastStudiedAt
nextReviewAt
reviewCount
```

Possible mastery states:

```text
new
learning
weak
developing
strong
mastered
```

## 10. Study Session

```text
id
userId
topicId
mode
startedAt
endedAt
itemsStudied
correctAnswers
incorrectAnswers
```

Avoid storing excessive raw session data unless it provides useful functionality.

## 11. Public Shared Study Set

Six-character code:

```text
publicStudySets/{shareCode}
```

Conceptual fields:

```text
shareCode
deckName
ownerId
sourceType
status
createdAt
updatedAt
contentVersion
cards
```

For large sets, use subcollections/chunking rather than one oversized document.

## 12. Source Provenance

Each official content source should retain:

```text
sourceId
url
title
domain
collectedAt
topicIds
licenseInformation
processingStatus
```

AI-generated/synthesized content should be traceable to its source set.

## 13. Content Jobs

```text
contentJobs/{jobId}
```

Conceptual fields:

```text
jobId
type
subject
targetLevel
sourceIds
status
coverage
gaps
createdAt
updatedAt
error
```

Possible statuses:

```text
queued
collecting
processing
analyzing
draft
review
approved
published
failed
```

## 14. Versioning

Official content should be versioned.

A content update must not unexpectedly destroy existing user progress.

Progress should reference stable content identifiers where possible.

## 15. Storage

Use Firestore for structured metadata and normal educational content.

Use Cloud Storage for:
- PDFs
- large images
- user uploads
- diagrams
- other large media

Do not store large binary files directly in Firestore.

## 16. Validation

All AI/imported data must pass schema validation before publication.

Pipeline:

```text
External/AI data
  |
  v
Schema validation
  |
  v
Sanitization
  |
  v
Content checks
  |
  v
Draft
  |
  v
Human review
  |
  v
Published
```
