stepsCompleted: [1]
inputDocuments: []
workflowType: 'research'
lastStep: 1
research_type: '{{research_type}}'
research_topic: '{{research_topic}}'
research_goals: '{{research_goals}}'
user_name: '{{user_name}}'
date: '{{date}}'
web_research_enabled: true
source_verification: true
---

# Research Report: {{research_type}}

**Date:** {{date}}
**Author:** {{user_name}}
**Research Type:** {{research_type}}

---

## Research Overview

[Research overview and methodology will be appended here]

---

<!-- Content will be appended sequentially through research workflow steps -->

## Technical Research Scope Confirmation

**Research Topic:** architecture and stack for Afterlight
**Research Goals:** pick a stack (broad overview first)

**Technical Research Scope:**

- Architecture Analysis - design patterns, frameworks, system architecture
- Implementation Approaches - development methodologies, coding patterns
- Technology Stack - languages, frameworks, tools, platforms
- Integration Patterns - APIs, protocols, interoperability
- Performance Considerations - scalability, optimization, patterns

**Research Methodology:**

- Current web data with rigorous source verification
- Multi-source validation for critical technical claims
- Confidence level framework for uncertain information
- Comprehensive technical coverage with architecture-specific insights

**Scope Confirmed:** 2026-03-01

## Technology Stack Analysis

### Programming Languages

For a modern, consumer-facing web app like Afterlight that handles user-generated memories (text, photos, audio) and prioritizes a smooth UI, the dominant choice today is **TypeScript on top of JavaScript**, primarily because:

- It integrates naturally with the React/Next.js ecosystem used in several recent virtual-memorial style projects.
- It offers type safety that helps keep a growing codebase maintainable.
- It runs both in the browser and on the server (via Node.js), simplifying the mental model for full‑stack work.

Python, Ruby, and Go remain viable for the backend in alternative architectures, but if we want tight integration with a React/Next.js front end and easy deployment on platforms like Vercel, **TypeScript + Node.js** is the most straightforward and well-supported option.

_Popular Languages: TypeScript/JavaScript (primary), with Python/Ruby/Go as secondary backend options_

_Emerging Languages: Deno/TypeScript runtimes and Rust-backed services in performance-critical paths_

_Language Evolution: Strong trend toward typed JavaScript (TypeScript) for web apps of this type_

_Performance Characteristics: Adequate for a memorial app’s read-heavy traffic profile; hotspots can be offloaded to specialized services if needed_

_Source: https://dev.to/chrisbuildsonline/building-1000-candles-a-digital-memorial-that-taught-me-about-scale-optimization-and-remembrance-3ok3_

### Development Frameworks and Libraries

Recent digital memorial and remembrance projects frequently choose **React with Next.js** for the frontend framework:

- **Next.js (React)** provides server-side rendering / static generation, good SEO for public memorial pages, and a mature routing & data‑fetching story.
- **Tailwind CSS** or similar utility-first frameworks are commonly used to quickly build soft, accessible UIs.
- For richer visuals (e.g., candle animations, constellations), projects sometimes add **Three.js / React Three Fiber** and animation libraries such as **Framer Motion**.

For Afterlight, a pragmatic base is:

- **Next.js + React + TypeScript** for the app.
- **Tailwind CSS** (or another utility CSS system) for styling.
- Optional: Framer Motion for subtle transitions; Three.js only if we later decide to add more immersive visuals.

_Major Frameworks: Next.js (React), with Tailwind CSS and optional Framer Motion / Three.js_

_Micro-frameworks: Lightweight component libraries (e.g., Headless UI) can be layered on as needed_

_Evolution Trends: Strong consolidation around React/Next.js for consumer web apps_

_Ecosystem Maturity: Very high; extensive documentation, examples, and community support_

_Source: https://sibsforever.medium.com/the-architecture-of-sibsforever-org-e36f717c944_

### Database and Storage Technologies

Virtual memorial apps combine **structured data** (rooms, threads, candles, permissions) with **unstructured media** (photos, audio). Current practice and tooling favor:

- A **relational database** like **PostgreSQL** for core entities and relationships (users, rooms, threads, candles).
- **Object storage** for media (images, audio), often accessed through a CDN for performance.
- In some serverless deployments, **serverless Postgres** providers (e.g., Neon, Supabase, Turso/SQLite variants) are used to simplify operations.

For Afterlight’s initial scope:

- Use **PostgreSQL** as the primary database.
- Use platform-provided **object storage + CDN** (e.g., Vercel Blob / S3-equivalent) for photos and audio.

_Relational Databases: PostgreSQL as primary choice_

_NoSQL Databases: Could be used for analytics or event logs later, but not required for MVP_

_In-Memory Databases: Redis or similar could later support caching, sessions, or rate‑limiting_

_Data Warehousing: Not needed at MVP, kept in mind for future grief‑research/analytics features_

_Source: https://github.com/lahiruC22/eternal-flames_

### Development Tools and Platforms

Given the stack above, common and well-supported tooling includes:

- **IDE/Editor**: VS Code with TypeScript support and Next.js tooling.
- **Version Control**: Git (GitHub, GitLab, or similar).
- **Build & Dev Tools**: Next.js build pipeline, package manager (pnpm/yarn/npm), ESLint, Prettier.
- **Testing**: Jest / Vitest for unit tests; Playwright or Cypress for end-to-end tests; React Testing Library for component behavior.

These tools are widely adopted and integrate cleanly with a Next.js + TypeScript project, which reduces setup friction and improves long-term maintainability.

_IDE and Editors: VS Code (recommended for TypeScript/Next.js)_

_Version Control: Git with hosted platform (e.g., GitHub)_

_Build Systems: Next.js built‑in tooling with Node-based package manager_

_Testing Frameworks: Jest/Vitest, React Testing Library, and an E2E tool like Playwright_

_Source: General ecosystem documentation and tool vendor docs (Next.js, Jest, Playwright)_

### Cloud Infrastructure and Deployment

For a small-to-mid-scale SaaS with spiky but not extreme traffic and a global, read‑heavy pattern (people visiting memorial pages and occasionally uploading media), current best practice for a Next.js‑based app is:

- **Vercel** as primary hosting platform for the Next.js frontend and serverless API routes.
- **Database-as-a-Service** (e.g., managed Postgres such as Supabase, Neon, or a cloud provider’s Postgres offering).
- **Object Storage + CDN** for media (e.g., Vercel Blob, or S3-compatible storage behind a CDN).

Alternatives like AWS (with Lambda + API Gateway + RDS + S3) or GCP/Azure provide more control but more operational overhead; for Afterlight’s expected early stage, a Vercel‑centric setup minimizes DevOps burden.

_Major Cloud Providers: Vercel for app hosting; managed Postgres and storage from a compatible provider_

_Container Technologies: Optional; full Kubernetes orchestration is not needed initially_

_Serverless Platforms: Vercel Functions / Edge Functions suitable for most backend logic_

_CDN and Edge Computing: Built-in via Vercel edge network and storage integrations_

_Source: https://dev.to/chrisbuildsonline/building-1000-candles-a-digital-memorial-that-taught-me-about-scale-optimization-and-remembrance-3ok3_

### Technology Adoption Trends

Recent practice in digital memorial and similar consumer web apps suggests:

- Strong preference for **React/Next.js + TypeScript** for frontends.
- Widespread adoption of **PostgreSQL** and **serverless Postgres** services.
- Growing use of **serverless/edge hosting** platforms (Vercel, Netlify) to reduce operational load.
- Focus on **performance optimizations** like cursor-based pagination, smart polling, and CDN-backed media.

For Afterlight, this points toward a recommended baseline stack of:

- **Frontend**: Next.js + React + TypeScript + Tailwind CSS.
- **Backend**: Next.js API routes (Node/TypeScript), with potential migration to dedicated services if needed later.
- **Data**: PostgreSQL for structured data; object storage for media.
- **Hosting**: Vercel (or equivalent) plus managed Postgres provider.

_Migration Patterns: Movement from bespoke monoliths to managed platforms and serverless Postgres_

_Emerging Technologies: Edge functions and serverless databases for low-latency global access_

_Legacy Technology: Traditional LAMP stacks and on‑prem hosting used less often for new builds of this type_

_Community Trends: Strong ecosystem investment in React/Next.js and managed Postgres services_

## Integration Patterns Analysis

### API Design Patterns

For Afterlight’s recommended stack (Next.js + Node/TypeScript + Postgres), a straightforward and maintainable choice is to expose a **REST-style HTTP API** for any programmatic access, while using **Next.js route handlers / server actions** for the main web application. REST works well for:

- Clear resource modeling around rooms, threads, and candles.
- Simpler integration with future mobile clients or partner services.
- Easy debugging and onboarding for typical web developers.

GraphQL can be added later if you want more flexible client querying across rooms/threads/candles, but it is not essential for an MVP. gRPC/RPC-style APIs are generally overkill for this class of product unless you later split into many internal services.

_RESTful APIs: Recommended primary pattern for external and internal HTTP integration_

_GraphQL APIs: Optional for future multi-client flexibility_

_RPC and gRPC: Not required initially; suitable only if you later move to many microservices_

_Webhook Patterns: Useful for outbound events (e.g., “new candle created”) if you integrate with email providers or partner apps_

_Source: General REST/GraphQL best-practice docs and typical SaaS integration patterns_

### Communication Protocols

The core of Afterlight can run entirely over **HTTPS (HTTP/1.1 or HTTP/2)**, which is sufficient for normal browsing and form submissions. For more interactive features (live “someone just lit a candle” updates), you can:

- Start with **short polling / revalidation** (Next.js data revalidation or periodic fetches).
- Later upgrade to **WebSockets or Server-Sent Events (SSE)** if you want near‑real‑time updates within rooms or threads.

Message queues or lower-level protocols (AMQP, MQTT, etc.) become relevant only if you add heavier background processing or large-scale event fan‑out later.

_HTTP/HTTPS Protocols: Primary channel for all web interactions_

_WebSocket Protocols: Optional for live updates in rooms/threads_

_Message Queue Protocols: Reserved for future background processing or analytics pipelines_

_gRPC and Protocol Buffers: Not needed for initial single‑service deployment_

_Source: Standard web app communication patterns for Next.js/Node-based SaaS_

### Data Formats and Standards

For an app like Afterlight, **JSON over HTTP** is the natural default:

- Browser clients and mobile apps handle JSON natively.
- It aligns with Next.js route handlers and most Node libraries.

Binary formats such as Protocol Buffers or MessagePack are rarely required at this scale and complexity; any performance benefit is outweighed by added complexity. Media files (images, audio) are stored as binary blobs in object storage and referenced by URLs in the JSON payloads.

_JSON and XML: JSON as primary; XML not required_

_Protobuf and MessagePack: Not needed for MVP; candidate only for specific performance hotspots_

_CSV and Flat Files: Useful for exports or backups, not for primary APIs_

_Custom Data Formats: Avoided initially to keep integrations straightforward_

_Source: Common RESTful API design guidelines_

### System Interoperability Approaches

At launch, Afterlight can be a **single web application** exposing HTTP endpoints rather than a distributed set of services. For interoperability and future integrations:

- Use a **logical API layer** (Next.js route handlers) that behaves like an API gateway for the app itself.
- Add an **API key–based or OAuth‑based external API** later if partners or third‑party apps need to access room and candle data.
- Avoid heavy enterprise patterns like ESBs or full-blown service meshes at this stage.

_Point-to-Point Integration: Direct HTTPS calls to the app’s public API endpoints_

_API Gateway Patterns: Handled pragmatically via Next.js routing and, if needed later, a dedicated API gateway in front of the app_

_Service Mesh / ESB: Not required for an MVP on a single platform_

_Source: Modern small‑SaaS architecture guides using managed platforms_

### Microservices Integration Patterns

For an MVP, Afterlight should remain a **modular monolith** (one deployable app with well‑separated modules for auth, rooms, threads, candles, media) rather than microservices. If the product grows significantly, potential future steps include:

- Extracting **media processing** or **email/invite sending** into separate services or background workers.
- Introducing a lightweight message queue for more robust asynchronous processing.

At that point, you might apply patterns like API gateway, service discovery, and circuit breaker; but they are premature now.

_API Gateway Pattern: Implicitly satisfied via the web app, with potential future dedicated gateway_

_Service Discovery / Circuit Breaker / Saga: Reserved for a future microservice phase if growth demands it_

_Source: Microservices vs monolith trade-off discussions and SaaS case studies_

### Event-Driven Integration

Even within a monolithic deployment, **event-driven ideas** can be used internally:

- When a candle is created, emit a domain event that can:
  - trigger notification emails,
  - update search indices,
  - drive analytics dashboards.

Initially, this can be implemented as simple function calls or lightweight job queues; adopting full Kafka/RabbitMQ-style infrastructure is likely unnecessary until scale demands it.

_Publish-Subscribe Patterns: A good fit for decoupling side effects from core flows as the system grows_

_Event Sourcing / CQRS: Generally overpowered for this product; only consider if you need full event history modeling_

_Message Broker Patterns: Optional future enhancement for analytics, notifications, or heavy background work_

_Source: Event-driven design literature for small web apps_

### Integration Security Patterns

Given the sensitivity of memorial content, integration security is important even at MVP:

- Use **cookie-based sessions or OAuth‑style flows** for user authentication, implemented with a library like NextAuth or a similar solution.
- Protect any external API endpoints with **OAuth 2.0 / JWT** or at minimum **API keys** tied to accounts.
- Enforce **HTTPS everywhere**, with **at-rest encryption** handled by the managed database/storage provider.

_OAuth 2.0 and JWT: Recommended for any third-party API access_

_API Key Management: Simple pattern for initial partner integrations_

_Mutual TLS: Not required for public web clients; reserved for service-to-service traffic in more complex architectures_

_Data Encryption: Rely on managed Postgres/storage encryption at rest plus HTTPS in transit_

_Source: OWASP and cloud provider security best practices_

