---
name: initowsky
description: Initialize a `.dev-ai/` knowledge framework. Analyzes repository, documents tech stack/architecture, and captures coding standards without executing local build tools.
---

# Initowsky

## Overview
Initialize `.dev-ai/` by inspecting the repository, confirming analysis with the user, and generating a durable documentation set. 
Focus: Evidence-driven analysis, concrete file paths, observed patterns.

## Workflow

### 1. Analyze the repository deeply
Scan the repository to summarize:
- Primary language, frameworks, build tools.
- Repository shape (monorepo, service split, etc.).
- Data layer (DB, ORM, API style).
- State management, Auth, Logging, Observability.
- Testing stack and CI/CD signals.
*Inspect manifests (package.json, build.gradle, etc.) and source roots.*

**Output:** "Technical DNA" summary with file references.
**Stop.** Ask user to confirm/correct analysis.

### 2. Gather missing project context
Ask for:
- Project name & 1-2 sentence description.
- Main business goals.
- Coding pet peeves or strict requirements.

### 3. Generate the `.dev-ai/` structure
Create:
- `.dev-ai/docs/INDEX.md` (Master map)
- `.dev-ai/docs/project/`: `tech-stack.md`, `vision.md`, `architecture.md`
- `.dev-ai/docs/standards/`: `global/`, `frontend/`, `backend/`, `testing/`

### 4. Discover coding standards
Infer and document naming conventions, error handling, folder structures, and testing patterns from existing code. 
*Prefer observed patterns with examples over abstract rules.*

### 5. Finalize the bootstrap
Update `README.md` or `CLAUDE.md` to point to `.dev-ai/docs/INDEX.md`.
**Finish with:** Tree view of `.dev-ai/` and the phrase: `Ready to work`.

## Guardrails
- **NO LOCAL BUILDS:** Do not execute local build, compilation, or package tools (e.g., `./gradlew`, `npm install`, `docker-compose`). Analysis must be strictly based on static code inspection.
- **CODE OVER ASSUMPTIONS:** Use repository evidence first; infer only when incomplete.
- **ABSENCE IS DATA:** State clearly when a layer (e.g., backend) is absent.
- **STAY COMPACT:** Keep docs navigable and high-signal for future AI agents.