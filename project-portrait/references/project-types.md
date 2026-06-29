# Project Type Adaptation Guide

Use this guide after identifying the project type. Select only the sections that match the repository. Mixed repositories may need more than one section, but avoid loading irrelevant assumptions into the final documents.

## Universal Evidence

Always collect:

- repository layout and package/workspace boundaries
- entry points and exported surfaces
- configuration and environment assumptions
- major dependencies and runtime platforms
- tests, examples, documentation, and CI signals
- important generated/build/vendor folders to exclude from counts
- confirmed unknowns and weak evidence

## Frontend App

Explore:

- routes/pages/screens
- component hierarchy and shared UI primitives
- state management and data fetching
- forms, validation, errors, loading states
- build setup and environment variables
- accessibility, responsiveness, and performance-sensitive areas
- test coverage for components, hooks, routes, and user flows

Recommended document adaptations:

- `03`: component architecture, routing model, state/data flow, API boundaries, build/runtime model
- `02`: user interaction flows and state transitions
- `04`: pages, feature modules, shared components, hooks/stores, API clients
- `05`: interaction design, state consistency, performance, accessibility, maintainability
- `06`: UX consistency, render cost, bundle size, testability, accessibility gaps

Do not force database, async scheduler, or backend deployment sections unless the frontend repository actually owns them.

## Backend Service

Explore:

- API routes, handlers, middleware, controllers
- service/domain layer and orchestration
- persistence models, migrations, repositories, transactions
- background jobs, queues, schedulers, workers
- external integrations and callbacks
- authentication, authorization, validation, errors
- observability, resilience, rate limits, retries, idempotency

Recommended document adaptations:

- `03`: request lifecycle, data model, service boundaries, external systems, deployment/runtime
- `02`: request/job/event flows
- `04`: routes, services, repositories, models, integrations, workers
- `05`: consistency, resilience, domain modeling, scaling tradeoffs
- `06`: reliability, observability, schema evolution, API boundaries, operational risks

## Full-Stack App

Explore frontend and backend together, then identify cross-boundary contracts:

- route/page to API mapping
- request/response schemas
- authentication/session flow
- shared types or generated clients
- deployment split and environment boundaries

Recommended document adaptations:

- `03`: client/server topology and contracts
- `02`: end-to-end user flows across UI, API, persistence, and external systems
- `04`: separate frontend modules, backend modules, and shared contracts
- `05`: contract stability, data consistency, auth/session handling, developer workflow
- `06`: contract generation, integration tests, deployment observability, boundary simplification

## Test Project or Test Framework

Explore:

- test runner and command entry points
- test suites, fixtures, factories, helpers, mocks
- environment setup and teardown
- reporting, coverage, snapshots, golden files
- flakiness controls, timeouts, retries, parallelism
- CI integration and developer feedback loop

Recommended document adaptations:

- `03`: test architecture, fixture model, execution model, reporting pipeline
- `02`: test execution flow from command to result
- `04`: suites, fixtures, helpers, mocks, reporters, CI scripts
- `05`: isolation strategy, determinism, fixture design, speed, maintainability
- `06`: flaky test reduction, fixture simplification, coverage gaps, feedback speed

Do not force business-user scenarios. The "user" may be a developer, CI system, or library maintainer.

## Algorithm or Machine Learning Project

Explore:

- input data and preprocessing
- algorithm stages, model definitions, training/inference paths
- evaluation metrics, benchmarks, validation strategy
- reproducibility controls: seeds, versions, configs, artifacts
- complexity, performance, memory behavior
- notebooks versus production scripts

Recommended document adaptations:

- `03`: algorithm design, data flow, training/inference/evaluation lifecycle
- `02`: data-to-result flow and important branches
- `04`: data processing, model/algorithm modules, evaluation, utilities
- `05`: modeling choices, complexity tradeoffs, reproducibility, evaluation quality
- `06`: benchmark rigor, data quality, reproducibility, performance, model lifecycle

Mark claims about accuracy, latency, or quality as `待确认` unless backed by benchmarks or tests.

## SDK or Library

Explore:

- public API surface and package exports
- core abstractions and extension points
- error model and compatibility guarantees
- examples, docs, tests, generated artifacts
- dependency footprint and supported runtimes
- versioning and release configuration

Recommended document adaptations:

- `03`: package architecture, public API, extension model, compatibility boundaries
- `02`: consumer usage flows
- `04`: exported modules, internal modules, adapters, utilities
- `05`: API design, abstraction boundaries, backward compatibility, ergonomics
- `06`: examples, docs, type safety, compatibility tests, release discipline

Do not invent product/business context. Focus on consumers and integration use cases.

## CLI or Developer Tool

Explore:

- command entry points and subcommands
- argument parsing and config precedence
- filesystem/network effects
- exit codes, logging, prompts, errors
- platform assumptions
- tests and golden outputs

Recommended document adaptations:

- `03`: command architecture, configuration model, execution pipeline
- `02`: command invocation to side effect/result
- `04`: commands, parsers, executors, output formatters, adapters
- `05`: ergonomics, safety, determinism, composability
- `06`: error messages, dry-run support, platform coverage, shell integration, test fixtures

## Data Pipeline

Explore:

- sources, sinks, schemas, transforms
- DAG/task orchestration and scheduling
- data quality checks and failure handling
- lineage, backfills, idempotency, partitions
- storage formats and retention
- monitoring and alerting

Recommended document adaptations:

- `03`: pipeline topology, schema flow, scheduling, state and retries
- `02`: data lifecycle from source to sink
- `04`: connectors, transforms, validators, loaders, orchestration code
- `05`: data quality, idempotency, backfill strategy, lineage
- `06`: observability, schema evolution, replayability, quality gates

## Infrastructure or DevOps Project

Explore:

- resources, environments, modules, stacks
- plan/apply/deploy flow
- secrets and configuration boundaries
- rollback and drift handling
- monitoring, alerts, policies
- CI/CD pipeline and permissions

Recommended document adaptations:

- `03`: resource topology, environment model, deployment workflow, state management
- `02`: change lifecycle from commit/config to deployed resources
- `04`: modules, stacks, scripts, policies, pipeline jobs
- `05`: safety controls, environment isolation, rollback, drift detection
- `06`: observability, policy coverage, rollback, dependency management, least privilege

## Monorepo or Mixed Project

Explore:

- workspace/package graph
- shared contracts and generated code
- independent versus coupled deployment units
- common tooling and CI boundaries
- cross-package dependencies and ownership

Recommended document adaptations:

- `03`: repository topology first, then per-subsystem architecture
- `02`: choose representative cross-boundary flows
- `04`: summarize packages by ownership and role
- `05`: dependency management, contract stability, build/test scalability
- `06`: workspace boundaries, incremental builds, shared contract discipline

For very large monorepos, document the relevant slice first and explicitly list what was out of scope.
