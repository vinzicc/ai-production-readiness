# Vulnerable Demo App Specification

## 1. Purpose

Build a deliberately vulnerable AI-enabled SaaS application that Kevin can:

1. build and understand;
2. audit manually;
3. exploit only in a controlled local or test environment;
4. repair one finding at a time;
5. verify with repeatable tests;
6. convert into an audit checklist, sample report, and technical walkthrough.

This is a training and proof asset, not a production product.

## 2. Working Name

**PromptDesk**

A small workspace where users create private projects and generate AI-assisted content. Free users have a limited quota. Pro users receive a larger quota after a Stripe test-mode payment.

## 3. Scope Boundary

### Included

- email and password authentication;
- private user projects;
- AI text generation;
- free and Pro plans;
- Stripe Checkout in test mode;
- Stripe webhook processing;
- basic admin page;
- usage tracking;
- deliberately vulnerable baseline;
- automated reproduction and regression tests.

### Excluded

- teams and organizations;
- file uploads;
- social login;
- real payments;
- production deployment with real users;
- mobile application;
- complex UI or branding;
- compliance claims;
- full penetration testing.

## 4. Technical Stack

- Next.js App Router
- React
- TypeScript with strict mode
- Supabase Auth
- Supabase Postgres
- Supabase Row Level Security
- Stripe Checkout and webhooks in test mode
- OpenAI-compatible API abstraction
- Local mock AI provider by default
- Vitest for unit and integration tests
- Playwright for critical browser flows
- Zod for secure-version validation
- Vercel-compatible configuration

## 5. Safety Constraints

- Use only local development or an isolated test deployment.
- Use Stripe test mode only.
- Use mock AI responses by default.
- Never commit real API keys, Supabase service-role keys, Stripe secrets, or customer data.
- Any secret-leak demonstration must use an obviously fake canary value.
- Never point exploit scripts at systems not owned or explicitly authorized by Kevin.
- Keep the vulnerable baseline separate from the repaired state through commits or branches.

## 6. User Roles

### Guest

- can view landing, pricing, sign-up, and login pages;
- cannot access projects or generation endpoints.

### Authenticated Free User

- can create and manage only their own projects;
- can generate up to 5 AI outputs per billing period;
- cannot access admin functions;
- cannot modify plan or role directly.

### Authenticated Pro User

- has the same ownership rules as Free users;
- can generate up to 100 AI outputs per billing period;
- receives Pro status only from a verified Stripe event.

### Admin

- can view a minimal user and system overview;
- role is assigned only through trusted server-side data;
- cannot be created by modifying client-controlled metadata.

## 7. Core User Flows

### Flow A: Authentication

1. Guest creates an account.
2. User signs in.
3. A profile row is created.
4. User reaches the dashboard.

### Flow B: Private Project

1. User creates a project.
2. User views the project.
3. User updates or deletes the project.
4. Another user must not be able to read or modify it.

### Flow C: AI Generation

1. User opens one of their projects.
2. User submits a prompt.
3. Server verifies authentication, ownership, plan, quota, and input.
4. AI provider or mock returns text.
5. Generation and usage are recorded.

### Flow D: Upgrade

1. Free user starts Stripe Checkout.
2. Stripe test payment succeeds.
3. Verified webhook records the event exactly once.
4. Subscription state becomes active.
5. User receives Pro quota.

### Flow E: Administration

1. Admin opens the admin page.
2. Server verifies a trusted admin role.
3. Non-admin users receive access denied.

## 8. Database Structure

### `profiles`

- `id uuid primary key references auth.users(id)`
- `email text`
- `display_name text nullable`
- `role text not null default 'user'`
- `plan text not null default 'free'`
- `stripe_customer_id text nullable unique`
- `created_at timestamptz not null default now()`
- `updated_at timestamptz not null default now()`

### `projects`

- `id uuid primary key default gen_random_uuid()`
- `owner_id uuid not null references profiles(id)`
- `title text not null`
- `description text nullable`
- `created_at timestamptz not null default now()`
- `updated_at timestamptz not null default now()`

### `generations`

- `id uuid primary key default gen_random_uuid()`
- `project_id uuid not null references projects(id)`
- `user_id uuid not null references profiles(id)`
- `prompt text not null`
- `output text nullable`
- `status text not null`
- `provider text not null`
- `error_code text nullable`
- `created_at timestamptz not null default now()`

### `usage_periods`

- `id uuid primary key default gen_random_uuid()`
- `user_id uuid not null references profiles(id)`
- `period_start timestamptz not null`
- `period_end timestamptz not null`
- `generation_count integer not null default 0`
- unique constraint on `user_id, period_start`

### `subscriptions`

- `id uuid primary key default gen_random_uuid()`
- `user_id uuid not null references profiles(id)`
- `stripe_customer_id text not null`
- `stripe_subscription_id text not null unique`
- `status text not null`
- `price_id text not null`
- `current_period_end timestamptz nullable`
- `created_at timestamptz not null default now()`
- `updated_at timestamptz not null default now()`

### `stripe_events`

- `event_id text primary key`
- `event_type text not null`
- `processed_at timestamptz not null default now()`

## 9. Intentional Vulnerabilities

The first baseline intentionally contains the following flaws. They must be introduced clearly enough to reproduce, but never with real secrets or real payments.

### V-01: Broken project isolation through weak RLS

**Vulnerable behavior**

Authenticated users can select or update projects they do not own because the policy checks only whether a session exists.

**Impact**

Cross-user data exposure and modification.

**Expected secure behavior**

`owner_id = auth.uid()` is enforced for select, insert, update, and delete. Insert and update use appropriate `WITH CHECK` rules.

**Required proof**

User B can retrieve or modify User A's project before the fix and receives no rows or authorization failure after the fix.

### V-02: API trusts a client-supplied user ID

**Vulnerable behavior**

The generation route accepts `userId` in the request body and uses it for ownership or quota checks.

**Impact**

Impersonation, quota theft, or generation against another user's project.

**Expected secure behavior**

Identity comes only from the verified server session. Client-supplied identity fields are ignored or rejected.

**Required proof**

Changing `userId` succeeds before the fix and fails after the fix.

### V-03: User can self-upgrade or self-assign admin role

**Vulnerable behavior**

The client can directly update `profiles.plan` or `profiles.role`, or the app trusts user-editable authentication metadata.

**Impact**

Unauthorized premium access or admin privilege escalation.

**Expected secure behavior**

Plan and role fields are not user-writable. Trusted server logic and verified payment events control them.

**Required proof**

A normal user can become Pro or admin before the fix and cannot after the fix.

### V-04: Stripe webhook signature is not verified

**Vulnerable behavior**

The webhook endpoint parses JSON and trusts the event without `Stripe-Signature` verification against the raw body.

**Impact**

An attacker can forge a successful payment event and obtain Pro access.

**Expected secure behavior**

Webhook construction verifies the signature with the test webhook secret and rejects invalid payloads.

**Required proof**

A forged event upgrades a user before the fix and returns an error without changing state after the fix.

### V-05: Stripe webhook is not idempotent

**Vulnerable behavior**

Repeated delivery of the same event applies the state change more than once or creates duplicate records.

**Impact**

Duplicate entitlements, corrupted subscription data, or repeated side effects.

**Expected secure behavior**

`stripe_events.event_id` is recorded transactionally and duplicate events produce no repeated side effect.

**Required proof**

Submitting one event twice causes duplication before the fix and one final state after the fix.

### V-06: AI endpoint has no enforceable quota or rate limit

**Vulnerable behavior**

Any authenticated user can call the generation route repeatedly without an atomic server-side quota check.

**Impact**

API cost abuse and service degradation.

**Expected secure behavior**

The server enforces plan limits atomically and applies a simple request-rate control suitable for the demo.

**Required proof**

The sixth Free-plan generation succeeds before the fix and is rejected after the fix. Concurrent requests must not bypass the limit.

### V-07: Prompt input is not validated

**Vulnerable behavior**

The endpoint accepts missing, malformed, or extremely long prompt values.

**Impact**

Unexpected errors, excessive cost, poor reliability, and potential downstream misuse.

**Expected secure behavior**

A Zod schema enforces type, non-empty content, and a defined maximum length.

**Required proof**

Malformed and oversized inputs reach processing before the fix and return a controlled 4xx response after the fix.

### V-08: Internal error details are returned to the client

**Vulnerable behavior**

The API returns raw database or provider error objects, stack traces, or internal configuration details.

**Impact**

Information disclosure that assists further attacks and exposes implementation details.

**Expected secure behavior**

Clients receive a stable error code and safe message. Detailed context is logged only on the server with secrets redacted.

**Required proof**

A forced error exposes internal details before the fix and only a sanitized response after the fix.

### V-09: Admin page relies on client-side protection

**Vulnerable behavior**

The UI hides the admin link, but the page or data endpoint does not perform a server-side authorization check.

**Impact**

Normal users can directly visit the route or call the endpoint.

**Expected secure behavior**

Admin authorization is enforced on the server before data is returned.

**Required proof**

A normal user can access admin data before the fix and receives 403 or redirect after the fix.

### V-10: Fake secret exposed through tracked configuration

**Vulnerable behavior**

An obviously fake canary secret is placed in a tracked example file or client-exposed environment variable to demonstrate secret scanning and exposure paths.

**Impact**

Demonstrates how real credentials could be leaked. No real credential may be used.

**Expected secure behavior**

Only placeholders are committed, sensitive variables are server-only, `.env*` rules are correct, and the fake secret is removed from active files.

**Required proof**

The fake canary is discoverable before the fix and absent from tracked active configuration after the fix.

## 10. Secure Behavior Invariants

The repaired application must satisfy all of these invariants:

1. A user can read and mutate only resources they own.
2. Identity and authorization decisions come from trusted server-side context.
3. Users cannot change their own plan or privileged role.
4. Payment state changes only after a verified Stripe test event.
5. A Stripe event has at most one business effect.
6. AI usage limits are enforced server-side and atomically enough for the demo.
7. Invalid input is rejected before database or AI-provider work.
8. Client errors reveal no secrets, stack traces, SQL details, or provider internals.
9. Admin data is protected by server-side authorization.
10. The repository contains no real credentials or sensitive customer data.

## 11. Testing Strategy

### Unit Tests

- input schemas;
- plan-limit calculation;
- safe error mapping;
- role and plan transition rules;
- Stripe event mapping.

### Integration Tests

- project ownership and RLS;
- generation endpoint authentication and ownership;
- quota enforcement;
- webhook signature rejection;
- webhook idempotency;
- profile field write restrictions.

### End-to-End Tests

- sign up and sign in;
- create and edit own project;
- attempt cross-user project access;
- Free-plan generation limit;
- Stripe test upgrade flow or deterministic webhook fixture;
- normal user denied from admin page.

### Verification Rule

For every vulnerability:

1. a test or controlled reproduction must demonstrate the failure on the vulnerable baseline;
2. the patch must be minimal and explained;
3. the same test must pass after the fix;
4. normal intended behavior must still work;
5. Kevin must manually understand and verify the result before it becomes a report finding.

## 12. AI-Assisted Workflow

### Hermes

- maintains task context;
- separates build, review, reproduce, patch, and verify stages;
- prevents one agent from silently completing every role.

### Codex Builder

- implements one scoped feature or vulnerability at a time;
- records changed files and commands;
- writes tests where requested;
- does not repair intentional vulnerabilities during baseline construction.

### Mistral Reviewer

- reviews the baseline without being shown the full intended-vulnerability list during the first pass;
- reports file location, preconditions, impact, reproduction, confidence, and false-positive risk;
- critiques patches after implementation.

### Human Verification

Kevin owns:

- deciding whether a finding is real;
- reproducing the issue;
- severity judgment;
- business impact interpretation;
- accepting or rejecting a patch;
- final report wording.

## 13. Build Order

1. Initialize Next.js, TypeScript strict mode, linting, and tests.
2. Add Supabase local or test configuration and schema migrations.
3. Implement authentication and profile creation.
4. Implement project CRUD.
5. Implement mock AI generation and usage tracking.
6. Implement Stripe test checkout and webhook path.
7. Implement minimal admin page.
8. Add intentional vulnerabilities one at a time with clear commit messages.
9. Create seed users and deterministic test fixtures.
10. Freeze the vulnerable baseline with a tag or branch.
11. Run an independent audit.
12. Reproduce and document each confirmed finding.
13. Repair one finding per commit with regression tests.
14. Produce checklist items and the sample report from verified evidence.

## 14. Required Local Fixtures

- User A: Free user
- User B: Free user
- User C: Pro user
- Admin user
- at least two projects owned by different users
- deterministic mock AI response
- valid Stripe test webhook fixture
- invalid or forged Stripe webhook fixture
- duplicate event fixture

No fixture may contain a real credential.

## 15. Definition of Done for the Specification

The specification is complete when:

- the product concept is fixed;
- roles and critical flows are defined;
- database tables are defined;
- ten intentional vulnerabilities have expected secure behavior and proof requirements;
- testing and verification rules are defined;
- the build order is narrow enough for Codex to implement without inventing major product features.

## 16. Next Execution Task

Create the application skeleton and baseline infrastructure only:

- Next.js App Router;
- TypeScript strict mode;
- lint and test commands;
- environment example with placeholders only;
- folder structure;
- health page;
- no business features yet.

Acceptance criteria:

- local development starts successfully;
- typecheck passes;
- lint passes;
- one smoke test passes;
- no real secret is committed;
- README contains setup and verification commands.
