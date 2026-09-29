# App Launch Checklist

A pre-launch checklist for shipping a complete consumer app — mobile, web, or both.

It covers the parts that sit *around* your core product: the login flow, the legal
docs, the paywall, the ads, the referral loop, the store requirements. It also covers the
operational parts: notifications, the admin dashboard and role-based access, observability,
security, testing, and incident response. These features are boring to build, easy to
postpone, and expensive to discover missing during app review, a legal complaint, or an
outage after launch.

**[→ Open the checklist](list.md)**: 27 sections, ~759 items.
**[→ What's new in v2](CHANGES-v2.md)**: the 453 items and 10 sections added since v1.

## What's in it

| # | Section | Covers |
|---|---------|--------|
| 1 | Authentication | Signup, login, passkeys, 2FA, consent records, account deletion |
| 2 | Onboarding | Intro slides, permission priming, consent before tracking |
| 3 | Profile | Photo, bio, privacy controls, block & report, EXIF stripping |
| 4 | Settings | Notification prefs, consent center, data export, security |
| 5 | Color Themes & UI | Light/dark/system, accessibility, RTL, i18n, no dark patterns |
| 6 | Referral System | Codes, deep links, two-sided rewards, fraud caps, FTC/TCPA rules |
| 7 | Ads | Placements, frequency caps, certified CMP, ATT, app-ads.txt |
| 8 | Monetization | Paywall, trials, auto-renewal law, taxes, entitlements, webhooks |
| 9 | Notifications | Notification service, push, email (SPF/DKIM/DMARC), SMS, preferences |
| 10 | Legal & Compliance | ToS/Privacy coverage, re-acceptance with proof, privacy laws, children, consumer law, IP, accessibility |
| 11 | Content Moderation | Report, block, filter, CSAM reporting, DMCA, DSA, UK OSA |
| 12 | Support & Feedback | FAQ, ticketing, legal request handling, rate prompt |
| 13 | Core App Quality | Offline mode, error states, idempotency, force update, feature flags |
| 14 | Backend & Infra | IaC, migrations, queues, backups, DR, zero-downtime deploys |
| 15 | Analytics | Tracking plan, no PII, consent gating, KPI dashboard |
| 16 | Web Presence | Landing page vs. full web app, legal pages, security headers, status page |
| 17 | Admin Dashboard & RBAC | Roles, permission matrix, audit log, impersonation, DSAR queue, teams |
| 18 | Observability & Monitoring | Logs, metrics, tracing, error tracking, SLOs, alerts, dashboards |
| 19 | Security Hardening | Threat model, OWASP, scanning, MFA everywhere, pen test |
| 20 | Privacy Engineering | Data map, retention jobs, privacy request tooling, vendor register |
| 21 | Testing & QA | Unit/integration/E2E, authz matrix, consent, a11y, CI gates |
| 22 | Incident Response | Breach playbook, on-call, runbooks, restore drills |
| 23 | Business & Company Setup | Entity, taxes, store accounts, DSA trader status, insurance |
| 24 | AI Features | Disclosure, vendor terms, prompt injection, evals, cost caps |
| 25 | Documentation & Handoff | README, `.env.example`, ADRs, ownership register |
| 26 | Launch Prep | Store assets, privacy manifest, review notes, staged rollout, go/no-go |
| 27 | Post-Launch Operations | Update cadence, yearly legal review, expiry tracking, shutdown plan |

## How to use it

- Copy `list.md` into your project and tick items off as you go.
- Not every item applies to every app. Skip what doesn't fit, but skip it
  deliberately rather than by forgetting. Write down why.
- Some sections branch. Section 16 asks you to pick a route (landing page or full
  web app) before working through it.
- Items and sections that say "if" are conditional: user-generated content,
  SMS, teams/organizations, AI features, children, regulated industries.
- Already worked through v1? Read [CHANGES-v2.md](CHANGES-v2.md) instead of the whole list.
- Using an AI coding agent? Give it the prompt below together with `list.md`.

## Prompt for an AI coding harness

Paste this into Claude Code, Cursor, Codex, Aider, or any other coding agent, with
`list.md` placed in the project (or pasted below the prompt). The agent first tailors the
checklist to your app by removing what doesn't apply and adding what's missing. It then
builds the remaining items one at a time, with tests, verifying each before moving on.

````text
You are taking this app from its current state to launch-ready. Your master plan is the
App Launch Checklist in `list.md` (if it's not in the repo, it is pasted below this prompt).
Work through the four phases below in order. Do not skip or merge phases.

## Phase 1: Understand the app
Read the codebase, README, configs, dependency manifests, and any docs. Copy the checklist
to `docs/launch-checklist.md` and write an "App Profile" at the top of it:
- What the app does and who it's for.
- Platforms: iOS, Android, web app, landing page, API, desktop.
- Stack: language, framework, hosting, database, auth, payments, email/push/SMS providers.
- Business model: free, ads, subscriptions, one-time purchases, B2B/teams.
- Risk flags: user-generated content, social features, teams/orgs, AI features, possible
  child users, sensitive data (health, finance, precise location, biometrics).
- Launch markets (countries and US states) and languages.
- What already exists, what's partial, and what's missing.
Anything the code can't tell you goes under "Open questions", each with the assumption
you're making. Ask me only questions whose answers would change what you build, all in
one message.

## Phase 2: Remove what doesn't apply
Go through every checklist item:
- Doesn't apply to this app: remove it from the working list and add it to an
  "Out of scope" appendix at the bottom with a one-line reason (for example, "No ads: no
  ad SDK and none planned"). Never drop an item silently.
- Already done: mark it `[x]` only after checking the code, and add evidence (file path,
  test name). If it's only partly done, leave it `[ ]` and note what's missing.
Keep these unless the app truly can't have them. If you remove one, explain why in writing:
- Legal: Terms of Service, Privacy Policy, stored proof of consent, versioned legal docs
  with a forced re-acceptance flow on material changes (each acceptance recorded as proof),
  account deletion (in-app and on the web), data export, accessibility statement, cookie consent (web),
  subscription disclosures and easy cancellation (paid apps).
- Notifications: a central notification service, in-app notification center, email with
  SPF/DKIM/DMARC, per-category preferences, unsubscribe, mandatory security alerts.
- Admin dashboard with role-based access control: roles, permission matrix, server-side
  authorization, audit log, user management, privacy-request queue.
- User-facing dashboard/home screen, with views that depend on the user's role.
- Observability: structured logs, error tracking, metrics, tracing, uptime and synthetic
  checks, alerts with runbooks, dashboards, public status page.
- Landing page / web presence with legal pages at stable public URLs.
- Security hardening, automated tests in CI, backups with a tested restore, an incident
  response and breach plan.

## Phase 3: Add what's missing, then order it
Add items the checklist lacks for THIS app and mark each one `(added)`:
- Core product features and flows specific to the app's domain.
- Laws, regulations, and platform rules specific to its industry and markets (for example
  HIPAA for health, PCI DSS for card payments, FERPA for schools, local consumer law).
- Setup and failure handling for every third-party service the app actually uses.
- Anything found in Phase 1: TODOs, FIXMEs, stubs, broken or half-built flows.
Then group the remaining work into milestones, ordered by dependency and risk:
 1. Foundations: repo hygiene, environments, secrets, CI, test setup, logging, error tracking.
 2. Auth, roles/RBAC, audit log.
 3. Core product features.
 4. Profile, settings, notifications, data export, account deletion.
 5. Monetization, ads, and referrals, if any.
 6. Admin dashboard, observability dashboards, alerts, status page.
 7. Legal docs, consent flows, privacy engineering, accessibility.
 8. Landing page and web presence.
 9. Security hardening, load tests, launch prep, post-launch runbooks.
Show me the tailored, ordered checklist. If I told you to run autonomously, carry on.
Otherwise wait for my go-ahead.

## Phase 4: Build one item at a time
Repeat for each unchecked item, top to bottom within the current milestone:
 1. Make a short plan: files to change, tests to write.
 2. Implement it completely: no stubs, no placeholder TODOs, no mock data in production paths.
 3. Write tests at the right level: unit for logic, integration for API/database, E2E for
    user journeys, authorization tests for anything behind a role. Untested code is not done.
 4. Run the full verification suite: lint, type-check, ALL tests (not just the new ones),
    and a production build. For UI work, run the app and walk through the flow, including
    dark mode, a small screen, and accessibility labels.
 5. If anything fails, fix the root cause. Never skip, delete, or weaken a test to get green.
 6. Mark the item `[x]` with evidence (files, test names) and commit it on its own:
    `checklist: <item>`. Only group small, tightly related items into one commit.
 7. Add an entry to `docs/launch-progress.md`: date, item, what changed, how it was
    verified, follow-ups.
If an item needs something only a human can provide (API keys, accounts, store consoles,
DNS, payment setup, a business or legal decision, lawyer review), mark it
`[!] BLOCKED: <what's needed>`. Build everything you can around it (code, config, an entry in
`.env.example`, docs) and move on. Keep a running "Needs from a human" list at the top of
the progress log.

## Rules
- Legal text: draft the Terms, Privacy Policy, and other legal pages from what the app
  actually does (its data map, SDKs, vendors), and mark each "DRAFT: requires review by a
  qualified lawyer". Never invent company facts (entity name, address, DPO, registration
  numbers); use clearly marked placeholders. Never claim compliance or certification
  (GDPR, WCAG, SOC 2, HIPAA) that hasn't been verified.
- The Privacy Policy, App Store privacy labels, Play Data Safety form, and privacy manifest
  must match the data the code actually collects. Recheck them whenever you add an SDK.
- Security: no secrets in the repo, authorization checked on the server, all input
  validated, least privilege everywhere.
- Prefer libraries the project already uses and match the existing code style. Add a new
  dependency only when there's a clear reason, and note it in the progress log.
- Every commit leaves the app building and all tests passing. Don't break existing features.
- Never mark an item done without verifying it.
- After each milestone, report what's done, what's blocked, and what's next.

## Finish
When every item is `[x]`, out of scope, or blocked, run the full suite one last time. Then
write `docs/launch-readiness.md` covering: done, blocked (with owner), out of scope (with
reasons), known risks, and the steps a human must take before launch (lawyer review,
store consoles, DNS, credentials, penetration test, insurance).
````

## The non-optional ones

Most of the list is judgment. These are hard requirements: missing them gets apps
rejected from the stores or exposes you to legal claims.

**App stores**
- **In-app account deletion**: required by both Apple and Google.
- **Web-accessible deletion page**: Google Play requires deletion to be reachable
  without installing the app.
- **Sign in with Apple**: required if you offer any other third-party login.
- **Report, block, filter, and 24h moderation**: required by Apple for any app with
  user-generated content.
- **Privacy Policy at a public URL**: required by both stores.
- **Store privacy labels**: App Store nutrition labels and Play Data Safety form.
- **Apple privacy manifest**: required-reason APIs and third-party SDK manifests.
- **EU trader status**: must be declared to distribute to EU users.
- **No incentivized reviews**: never reward users for rating the app.

**Law**
- **European Accessibility Act**: in force since June 2025 for EU consumer apps.
- **Proof of consent**: keep a record of which Terms/Privacy version each user accepted
  and which marketing, analytics, and ad consents they gave or withdrew.
- **Re-acceptance when Terms change**: announce material changes in advance, make users
  accept the new version before continuing, and store an append-only record of each
  acceptance (version, content hash, timestamp, IP, device) as proof.
- **Privacy Policy that matches reality**: a policy that differs from what the app and
  its SDKs actually collect is a deception risk.
- **Subscription disclosures and easy cancellation**: auto-renewal laws (US ROSCA,
  California and other states, EU consumer law) require clear terms, affirmative consent,
  and online cancellation.
- **Cookie and ad consent in the EU/UK**: no non-essential tracking before consent. Ads
  served there need a Google-certified consent platform.
- **Children's privacy**: COPPA (US) and the UK Children's Code if children can use the app.
- **CSAM reporting**: US services hosting user uploads must report to NCMEC.
- **Breach notification**: 72 hours to the regulator under GDPR, and user notice under US
  state laws.
- **Email and SMS rules**: CAN-SPAM, Gmail/Yahoo bulk-sender rules, TCPA consent for texts.

## Note on the legal sections

The checklist tells you *which documents to have and what to check*, not what they should
say. Sections 10, 11, 20, 23, and 24 are prompts for a conversation with a lawyer, not a
substitute for one. This is especially true for GDPR, COPPA, auto-renewal law, arbitration
clauses, and accessibility conformance claims. Laws and store policies change often, so
confirm current requirements and effective dates for each market before launch, and
re-check at least once a year (Section 27).
