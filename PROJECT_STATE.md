# AI PRODUCTION READINESS — PROJECT STATE

> Dynamic project data.

> Update this file when decisions, evidence, metrics, blockers, or priorities change.

> Last updated: 2026-06-29

## 1. Project Metadata

* Owner: Kevin
* Source of truth: `vinzicc/ai-production-readiness/PROJECT_STATE.md`
* Repository visibility: Public — change to Private before storing client-sensitive material
* Strategic focus period: 2026-06-30 to 2027-06-30
* Current stage: Stage 0 — global cashflow validation and minimum proof
* Status: Active
* Primary objective: obtain a paid deposit by 2026-07-13 and complete one legitimate paid project by 2026-07-29
* Target type: aggressive operational target, not a guarantee

## 2. North Star

Build a durable AI-native business that helps founders make AI-built applications safer, more reliable, testable, and ready for production.

Short-term goal:

* generate legitimate cashflow through narrow, fixed-scope technical services sold to a global English-speaking market.

Long-term goal:

* convert repeated checks, fixes, and failure data into recurring assurance software and business equity before 2028.

Strategic rule:

* the 12-month commitment prevents impulsive industry switching;
* it does not justify delaying revenue.

## 3. Fixed Thesis

* Industry: AI software development
* Core problem: AI-built apps become functional faster than they become production-ready
* Initial buyers:
  * solo founders;
  * indie hackers;
  * AI development agencies;
  * small product teams.
* Initial outcome:
  * reduce security risk;
  * reduce reliability risk;
  * detect launch blockers;
  * improve production readiness.
* Initial business model:
  * fixed-scope launch-blocker check;
  * narrow remediation sprint;
  * later recurring maintenance.
* Long-term direction:
  * continuous checks;
  * repository monitoring;
  * pre-deployment assurance;
  * human-verified automated findings.

## 4. Current Buyer Hypothesis

Primary market:

Global, English-speaking market.

Primary buyer:

Solo founder or small SaaS team that has built an AI-assisted web application and is preparing to launch, accept users, store customer data, connect payments, or resolve a specific production blocker.

Initial narrow buyer subtype:

* communicates in English;
* uses Next.js or React with TypeScript;
* uses Supabase as the initial preferred backend;
* deploys or plans to deploy on Vercel;
* expects to launch within 30 days;
* has implemented authentication, customer data, payments, or an AI feature;
* is willing to provide controlled repository access or a screen-share.

Initial geographic priority:

1. United States and Canada
2. United Kingdom and Western Europe
3. Australia and New Zealand
4. English-speaking founders in other regions

Relevant trigger events:

* announcing an upcoming launch;
* opening beta access;
* connecting Stripe;
* adding authentication;
* moving from prototype to production;
* preparing to store real customer data;
* asking whether Supabase RLS is secure;
* experiencing a failed deployment, auth problem, payment mismatch, or AI endpoint issue;
* expressing uncertainty about AI-generated code;
* seeking a technical cofounder or engineer before launch.

Buyer hypothesis status: Unvalidated

## 5. Current Offers

### Offer A — 48-Hour AI-Built SaaS Launch Blocker Check

Positioning:

Find launch-blocking security and reliability issues in AI-built SaaS applications before real users, customer data, or payments are exposed.

Use when the buyer is approaching launch but does not know the main technical risk.

Scope:

* one repository;
* one deployment or controlled reproduction environment;
* one Supabase database where applicable;
* Next.js or React with TypeScript;
* approximately 10,000 lines of code or less;
* maximum three verified findings;
* fixed exclusions;
* the 48-hour clock begins only after deposit, intake, access, and scope confirmation.

Review areas may include:

* authentication and authorization;
* Supabase RLS or database permissions;
* exposed secrets;
* Stripe webhook and entitlement flow;
* deployment and one critical user flow;
* AI endpoint quota, validation, fallback, or error handling.

Deliverables:

* concise severity-ranked findings;
* supporting evidence or reproduction steps;
* limited verdict: Proceed, Proceed with Caution, or Stop;
* prioritized next action;
* short English-language walkthrough video.

Founding validation price:

* US$150 fixed price;
* US$75 deposit before work starts;
* US$75 final payment before the complete report and walkthrough are delivered;
* limited to the first three completed founding clients.

### Offer B — 48-Hour Launch Blocker Fix Sprint

Use when the buyer already has one specific blocker.

Scope:

* one defined problem;
* one supported stack;
* one scoped fix;
* explicit acceptance criteria.

Deliverables:

* reproduced issue;
* scoped fix;
* before-and-after evidence;
* regression test when practical;
* changed-file summary.

Founding validation price:

* starts at US$500;
* 50% deposit before work starts;
* final quote depends on confirmed scope.

### Important Boundaries

These services are not:

* formal penetration tests;
* compliance certifications;
* exhaustive security reviews;
* guarantees that no vulnerability exists;
* suitable for high-risk regulated systems during the initial stage.

Do not claim an application is fully secure.

## 6. Supported Stack

Initial focus:

* Next.js
* React
* TypeScript
* Supabase
* Vercel
* Stripe
* OpenAI API
* Anthropic API
* GitHub

Secondary support only when the problem is narrow and verifiable:

* Firebase

Stack status: Initial hypothesis; narrow further after real repository evidence

## 7. Initial Review Areas

* Authentication
* Authorization
* User roles
* Supabase RLS
* Database permissions
* Secrets and environment variables
* Public API routes
* Input validation
* CORS
* Rate limiting
* Stripe and webhook verification
* Dependency risks
* Deployment configuration
* Error handling
* Logging
* Monitoring
* Critical user-flow tests
* AI-output validation
* AI-feature fallback behavior

## 8. Current Evidence

### Stronger Evidence

* AI-assisted software creation is growing.
* Developers report trust and debugging concerns around AI-generated output.
* Existing providers sell AI-built app production-readiness and security-review services.
* Major developer-security companies are building products around AI-generated code assurance.

### Missing Evidence

* Kevin has not received a repository submission.
* Kevin has not completed a technical buyer conversation for this offer.
* Kevin has not received a deposit.
* Kevin has not completed a paid project.
* Kevin has no case study or testimonial in this niche.
* Kevin has not validated that global founders will pay US$150 for the entry check.
* Kevin has not validated an international payment workflow.

Market status:

Problem evidence exists, but Kevin's global positioning, offers, and willingness to pay remain unvalidated.

## 9. Current Assets

* AI development tooling: Hermes connected to Codex and Mistral
* Intended use: implementation, independent review, test generation, and patch critique
* Tooling status: Available, but workflow and verification standard are not yet validated
* Vulnerable demo app specification: Completed in `demo-app/SPEC.md`
* 14-day cashflow plan: Completed in `execution/14_DAY_CASHFLOW_PLAN.md`
* Minimum proof case 1 — Supabase RLS: Not started
* Minimum proof case 2 — Stripe webhook: Not started
* Full PromptDesk implementation: Deferred until it no longer delays selling
* English sample finding: Not started
* English technical walkthrough: Not started
* English offer page: Not started
* Global prospect tracker: Not started
* Global prospect list: Not started
* International payment method: Not verified
* Case study: None
* Testimonials: None
* Internal scanner: None
* Recurring clients: None

## 10. Metrics

### Acquisition

* Qualified global prospects contacted: 0
* Trigger-based messages sent: 0
* Follow-ups sent: 0
* Positive replies: 0
* Technical conversations: 0
* Repository or screen-share reviews: 0
* Repository submissions: 0

### Revenue

* Deposits: 0
* Paid checks: 0
* Paid fix sprints: 0
* Completed paid projects: 0
* Total revenue: US$0
* Monthly recurring revenue: US$0

### Delivery

* Reviews delivered: 0
* Fix sprints delivered: 0
* Average delivery time: N/A
* Verified findings: 0
* False positives recorded: 0
* Critical fixes completed: 0

### Proof

* Minimum proof cases completed: 0
* Testimonials: 0
* Case studies: 0
* Referrals: 0
* Repeat customers: 0

## 11. Current Blockers

1. No minimum proof case exists.
2. No English sample finding or walkthrough exists.
3. No qualified global prospect pipeline exists.
4. Global buyer willingness to pay is unknown.
5. International payment capability is not verified.
6. Kevin has not yet demonstrated a repeatable delivery method.
7. Kevin needs a reliable method to evaluate AI-generated technical output.
8. Repository-access trust is unproven.
9. Family cashflow cannot depend entirely on an unvalidated offer.

## 12. Current Priority

Secure global cashflow without leaving the AI Production Readiness industry.

Parallel work order:

1. Build one minimum Supabase RLS proof case.
2. Convert it into an English sample finding and five-minute walkthrough.
3. Verify an international payment method and USD invoicing workflow.
4. Publish a simple English offer page and global prospect tracker.
5. Build a list of 50 trigger-qualified global prospects.
6. Begin trigger-based outreach immediately after the minimum proof exists.
7. Maintain a bridge-income lane until project revenue becomes dependable.
8. Accept only tightly scoped work within verified capability.
9. Use real delivery evidence to improve the checklist and PromptDesk.

Daily allocation until revenue becomes dependable:

* 60% prospecting, applications, and paid work;
* 30% technical proof and delivery capability;
* 10% research and administration.

## 13. Immediate Next Action

Complete minimum proof case one in English: Supabase RLS cross-user data access.

Deadline:

* 2026-07-02 23:59 Asia/Jakarta.

Required result:

* User A owns a project record;
* User B can read User A's project under the intentionally weak policy;
* the failure is reproduced in a controlled environment;
* the RLS policy is corrected;
* the same attempt fails after the fix;
* User A can still access the intended record;
* a regression test or repeatable script exists;
* Kevin can explain the root cause without relying on AI output;
* the business impact is explained in clear English.

After verification:

* write one concise English sample finding;
* record an English walkthrough of no more than five minutes;
* verify the payment workflow;
* create the simple English offer page;
* begin global outreach.

Do not build the full PromptDesk application before this proof and outreach step.

## 14. Fourteen-Day Targets

By 2026-07-13:

* one verified RLS proof case;
* one English sample finding;
* one short English walkthrough;
* one simple English offer page;
* one verified international payment method;
* at least 50 qualified global prospects contacted;
* at least five real technical conversations;
* at least one repository or screen-share review;
* at least one US$75 paid deposit.

By 2026-07-29:

* one legitimate paid project completed;
* payment collected in full;
* delivery evidence documented;
* one testimonial requested;
* offer adjusted using observed objections and delivery data.

## 15. Funnel Diagnosis and Kill Criteria

After 50 qualified global prospects, two follow-ups where appropriate, and at least five real conversations:

* no replies: change message or channel;
* replies but no calls: improve urgency or offer clarity;
* calls but no repository access: improve trust and access safety;
* repository access but no deposit: change proof, price, scope, or risk reversal;
* deposit but delivery failure: narrow scope and strengthen capability.

Do not change industry before identifying the failed funnel stage.

Do not continue the same message and channel unchanged after the threshold is met.

## 16. Qualification and Safety Rules

Accept a project only when:

* the stack is supported;
* the problem can be reproduced or investigated safely;
* expected output is explicit;
* access can be provided without unsafe credential handling;
* the client accepts the service boundaries;
* the deposit is paid.

Reject or defer when:

* the system is high-risk regulated software;
* the client requests unauthorized security testing;
* the problem requires expertise Kevin cannot verify;
* production access is unsafe or uncontrolled;
* scope cannot fit the promised delivery window.

Repository and access rules:

* prefer read-only or least-privilege access;
* use a controlled reproduction environment whenever possible;
* never request credentials through plain chat;
* do not store client-sensitive material in this public repository;
* document authorization before testing any non-demo system.

## 17. Stage-Gate Criteria

### Cashflow Validation Gate

Required:

* 50 qualified global prospects;
* at least five technical conversations;
* one repository or screen-share review;
* one deposit or clear funnel diagnosis.

### First Delivery Gate

Required:

* one paid project completed;
* payment collected;
* findings or fixes verified;
* scope and delivery time documented;
* testimonial requested.

### Service Standardization Gate

Required:

* at least five completed paid projects;
* repeated failure patterns;
* delivery checklist based on real evidence;
* known false-positive patterns;
* evidence of willingness to pay for recurring checks.

### Service to Productization

Do not begin external SaaS productization before:

* at least five completed paid projects;
* repeated failure patterns;
* evidence that checks are deterministic;
* evidence that buyers value recurring detection;
* a clear reason existing tools do not fully solve the problem.

## 18. Decision Log

### 2026-06-29

Decision:

Commit to AI-Built App Production Readiness as the core 12-month strategic focus.

Reason:

It combines current AI adoption, visible production risk, low starting capital, technical skill development, service-based cashflow, and long-term product potential.

Status: Active

### 2026-06-29

Decision:

Use a service-first model before building SaaS.

Reason:

Kevin currently lacks customer proof, repository data, technical failure patterns, and distribution.

Status: Active

### 2026-06-29

Decision:

Use first-principles thinking, reverse thinking, and evidence-based adaptation.

Reason:

Avoid copying trends, overclaiming expertise, or changing industries whenever an initial tactic fails.

Status: Active

### 2026-06-29

Decision:

Use PromptDesk as a proof laboratory, not as a prerequisite for starting outreach.

Reason:

A full demo build would delay revenue. Minimum verified proof is sufficient to begin cashflow validation.

Status: Active

### 2026-06-29

Decision:

Adopt a two-entry service ladder: Launch Blocker Check for uncertain risk and Launch Blocker Fix Sprint for a known problem.

Reason:

It combines low-friction diagnosis with a more direct result-based service while keeping scope narrow enough for Kevin's current proof level.

Status: Active

### 2026-06-29

Decision:

Run a 14-day cashflow validation period with a parallel bridge-income lane.

Reason:

Family cashflow is urgent, and an unvalidated business offer cannot be the sole protection against zero household income.

Status: Active

### 2026-06-29

Decision:

Use a global-first, English-speaking go-to-market strategy while keeping the initial buyer, stack, and launch trigger narrow.

Reason:

The global market offers a higher pricing ceiling and a larger concentration of AI-assisted SaaS founders, but requires stronger proof, English communication, repository-access trust, and international payment capability.

Status: Active

## 19. Assumptions to Test

* Global founders fear launching fragile AI-built apps.
* Triggered founders understand the value of a narrow blocker check.
* They will grant safe repository or screen-share access to a new provider.
* They are willing to pay US$150 for a limited check.
* Buyers with a known blocker will pay at least US$500 for a scoped fix.
* A narrow check or fix can be delivered within 48 hours after intake and access are complete.
* The supported stack produces repeated failure patterns.
* Some findings can later be automated.
* Agencies may become a stronger buyer than solo founders.
* English-language proof and communication are strong enough to establish trust.
* The international payment workflow does not create significant sales friction.

## 20. After June 2027 Parking Lot

Do not execute these during the current commitment unless they directly strengthen the core project:

* AI trading bots
* Generic AI automation agency
* GEO services
* Lead scraping
* Reconciliation business
* Social-media agency
* Unrelated SaaS ideas
* General-purpose agent platform
* Crypto as the primary business

## 21. Weekly Review Template

* Week ending:
* Main objective:
* What was completed:
* What was not completed:
* Technical evidence collected:
* Market evidence collected:
* Qualified global prospects contacted:
* Technical conversations:
* Repository or screen-share reviews:
* Deposits:
* Revenue generated:
* Main blocker:
* Funnel stage failing:
* Decision made:
* Priority for next week:
* PROJECT_STATE sections that need updating:

## 22. Changelog

### 2026-06-29

* Migrated `PROJECT_STATE.md` to GitHub as the operational source of truth.
* Documented Hermes, Codex, and Mistral as available development and review tooling.
* Completed `demo-app/SPEC.md` for PromptDesk.
* Added `execution/14_DAY_CASHFLOW_PLAN.md`.
* Changed Stage 0 from build-first capability development to 14-day cashflow validation and minimum proof.
* Replaced the broad initial review with a two-entry service ladder.
* Deferred full PromptDesk implementation so it cannot delay outreach.
* Added explicit bridge-income, funnel-diagnosis, qualification, and kill criteria.
* Switched go-to-market to global-first and English-speaking.
* Narrowed the initial buyer to AI-assisted SaaS founders using Next.js or React, TypeScript, Supabase, and Vercel.
* Changed founding validation pricing to US$150 for the check and US$500 starting price for the fix sprint.
* Added English proof assets, international payments, global prospecting, and repository-access trust as explicit requirements.
* Repository currently public; client-sensitive material must not be stored until visibility is changed to private.
