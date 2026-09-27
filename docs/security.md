# StudyBlitz Security

## 1. Security Principles

Security must be designed before production.

Main requirements:
- least privilege
- user data isolation
- server-side secrets
- validated external input
- authenticated administrative actions
- protected AI endpoints
- rate limiting
- secure storage rules

## 2. Authentication

Support initially:
- Google authentication
- Email/password if required by the final product

Do not expose private user content to unauthenticated users.

## 3. User Isolation

A user must only access their own:
- private study material
- progress
- sessions
- goals
- preferences
- subscription information

Shared/public content may be readable according to its publication state.

## 4. Firestore Rules

Production Firestore rules must:
- deny by default where practical
- check authentication
- check ownership
- distinguish public from private content
- protect admin-only operations
- prevent arbitrary writes to official content

Never use wide-open rules in production.

## 5. Storage Rules

Cloud Storage must distinguish:
- user uploads
- public media
- official media
- admin content

Validate:
- authenticated user
- ownership
- file size
- permitted file type
- upload path

## 6. Admin Access

Administrative content operations must require an explicit admin role.

Do not rely on hidden frontend buttons for authorization.

Authorization must be enforced server-side/Firebase Rules/Functions.

## 7. AI Security

AI API keys must never be placed in frontend JavaScript.

Use:

```text
Browser
  ↓
Authenticated backend
  ↓
AI provider
```

Protect AI endpoints with:
- authentication
- App Check where appropriate
- rate limiting
- usage limits
- request validation
- output validation

## 8. AI Output

Treat AI output as untrusted input.

Validate:
- schema
- string lengths
- URLs
- identifiers
- arrays
- nested objects
- media references

Sanitize learner-facing HTML/Markdown before rendering.

## 9. User Uploads

User-uploaded files are untrusted.

Validate:
- extension
- MIME type where available
- file size
- storage path
- ownership

Do not execute uploaded files.

Use safe processing services for PDFs/images where possible.

## 10. Public Sharing

Six-character share codes should:
- be sufficiently random
- have rate limiting
- not expose private data
- return only published public content

Do not use predictable sequential IDs as share codes.

## 11. Abuse Prevention

Protect:
- AI requests
- study-set creation
- uploads
- public sharing
- authentication endpoints
- expensive backend operations

Use quotas and rate limits.

## 12. Ads

Advertisements must not:
- obscure study controls
- capture user input intended for StudyBlitz
- interfere with authentication
- interfere with billing
- interrupt active study unnecessarily

The fixed bottom ad must have reserved safe space.

## 13. Secrets

Never commit:
- API keys
- service-account credentials
- private Firebase credentials
- payment secrets
- AI provider keys

Use environment variables and appropriate secret management.

## 14. Development

Use Firebase Emulator Suite for local testing.

Test security rules before production.

Use separate development/staging/production configuration where practical.

## 15. Security Review Before Launch

Verify:
- Firestore rules
- Storage rules
- Authentication
- admin authorization
- AI endpoints
- upload handling
- share codes
- rate limiting
- secrets
- XSS protection
- dependency vulnerabilities
