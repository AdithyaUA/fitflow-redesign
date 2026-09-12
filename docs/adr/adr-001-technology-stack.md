\# ADR-001: Adopt a Flutter Client with a NestJS + FastAPI Polyglot Backend



\## Status

Accepted



\## Context

FitFlow must deliver a seamless iOS/Android/web experience with real-time tracking, AI-personalized workout/nutrition plans, and social features, to be built and maintained by a mid-sized team under budget and compliance (HIPAA/GDPR) constraints.



\## Decision

\- \*\*Frontend:\*\* Flutter as the single cross-platform framework.

\- \*\*Backend:\*\* NestJS for the API gateway and core business services; a dedicated Python/FastAPI microservice for AI/ML workloads.

\- \*\*Database:\*\* PostgreSQL as the system of record; Redis for caching and real-time pub/sub; MongoDB/DynamoDB for high-volume activity logs.

\- \*\*Authentication:\*\* Auth0 for authentication and authorization.



\## Alternatives Considered

\- React Native (frontend)

\- Kotlin Multiplatform (frontend)

\- Native Swift/Kotlin per platform

\- A single Node.js or Python monolith backend

\- Firebase Auth or AWS Cognito for authentication

\- Firestore or DynamoDB as the sole database



\## Consequences (Positive)

\- Single frontend codebase reduces development and maintenance cost.

\- Separating the AI microservice lets the data-science team iterate independently in Python.

\- PostgreSQL gives strong consistency and compliance maturity for health data.

\- Auth0 reduces the compliance burden of building authentication in-house.



\## Consequences (Trade-offs)

\- The team must maintain two backend languages (TypeScript and Python) instead of one.

\- Flutter apps that need deep platform-specific hardware access will occasionally require native platform-channel code.

\- Auth0 costs scale with monthly active users and should be monitored as FitFlow grows.

