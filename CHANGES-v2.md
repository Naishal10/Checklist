# What's New in v2

Version 2.0 · 2026-09-29 · compared against v1 (commit `bb0b469`)

This file lists **only the items added in v2**, grouped the same way as [list.md](list.md).
The full checklist in [list.md](list.md) already includes all of them. Use this file to
catch up if you already worked through v1.

## Summary

- **v1:** 17 sections, 306 items.
- **v2:** 27 sections, 788 items: **482 new items** and **10 new sections**.
- **Nothing was removed.** Every v1 item is still in `list.md`, worded the same.
- **Renumbered:** Launch Prep moved from Section 17 to **Section 26**, so it now comes after
  the new operational sections. Sections 1–16 keep their numbers.
- **Main themes:** proving legal compliance (consent records, re-acceptance of updated Terms with stored proof, privacy law coverage, children,
  consumer and auto-renewal law, hosted-content duties, IP), the notification system, the
  admin dashboard with role-based access, observability, security hardening (including input limits and rate limiting), testing, incident
  response, company setup, AI features, and post-launch operations.

| Section | New items | Note |
|---|---:|---|
| 1. Authentication | 28 |  |
| 2. Onboarding | 5 |  |
| 3. Profile | 6 |  |
| 4. Settings | 7 |  |
| 5. Color Themes & UI | 9 |  |
| 6. Referral System | 8 |  |
| 7. Ads | 9 |  |
| 8. Monetization | 22 |  |
| 9. Notifications | 28 |  |
| 10. Legal & Compliance | 76 |  |
| 11. Content Moderation (if user-generated content) | 12 |  |
| 12. Support & Feedback | 7 |  |
| 13. Core App Quality | 8 |  |
| 14. Backend & Infra | 15 |  |
| 15. Analytics | 9 |  |
| 16. Web Presence | 27 |  |
| 17. Admin Dashboard & Role-Based Access | 37 | New section |
| 18. Observability & Monitoring | 23 | New section |
| 19. Security Hardening | 45 | New section |
| 20. Privacy Engineering & Data Governance | 12 | New section |
| 21. Testing & QA | 21 | New section |
| 22. Incident Response & Business Continuity | 9 | New section |
| 23. Business & Company Setup | 12 | New section |
| 24. AI Features (if the app uses AI) | 13 | New section |
| 25. Documentation & Handoff | 9 | New section |
| 26. Launch Prep | 14 |  |
| 27. Post-Launch Operations | 11 | New section |

---

## 1. Authentication
*28 new items*

### Sign Up
- [ ] Passwords checked against known-breached password lists (e.g., HaveIBeenPwned k-anonymity API).
- [ ] Proof of acceptance stored: Terms + Privacy version, timestamp, IP/device, and method (clickwrap record).
- [ ] Consents kept separate: accepting Terms never implies marketing, analytics, or ad consent.
- [ ] Neutral age screen that doesn't hint at the "right" answer and blocks retries after an underage answer.
- [ ] Verifiable parental consent flow if users under 13 (or under the local age of digital consent) are allowed.
- [ ] Phone signup shows consent and carrier-rate text; OTP messages stay transactional only.
- [ ] Reserved usernames blocked (admin, support, staff, brand names) and Unicode lookalikes normalized.
- [ ] Disposable-email detection where fraud or abuse risk warrants it.

### Log In
- [ ] Passkeys (WebAuthn / platform passkeys).
- [ ] Throttling per IP and per account, with progressive delays.
- [ ] Idle and absolute session timeouts appropriate to data sensitivity.
- [ ] Every auth event (login, failure, logout, 2FA change) written to the security audit log.
- [ ] Account recovery for users who lost email, phone, or 2FA access, with identity checks by support.
- [ ] SSO (SAML/OIDC) if you sell to teams or businesses.

### Password Management
- [ ] Reset request shows the same message whether or not the account exists.
- [ ] Outstanding reset tokens invalidated when the password changes.

### Security
- [ ] Step-up re-authentication for sensitive actions (change email/phone, payment, disable 2FA, delete account).
- [ ] Email change verifies the new address and notifies the old one with a "this wasn't me" lock link.
- [ ] Refresh token rotation with reuse detection.
- [ ] Session ID rotated on login and invalidated server-side on logout.
- [ ] MFA mandatory for all staff and admin accounts (see Section 17).

### Account Deletion
- [ ] Deletion reaches every processor (analytics, email, CRM, payment customer record, support desk, AI vendors).
- [ ] Deleted data ages out of backups within a documented window and is never restored into live systems.
- [ ] Records the law requires you to keep (invoices, tax, fraud) are kept minimal and disclosed in the Privacy Policy.
- [ ] Deletion finishes within the legal deadline (e.g., GDPR: one month) and is tracked.
- [ ] Store-billed subscriptions: tell users to cancel in Apple/Google and link there (you can't cancel them for the user).
- [ ] Deletion recorded in the audit log without keeping the deleted personal data.
- [ ] Content the user shared with others handled per policy (deleted, anonymized, or shown as "Deleted user").

---

## 2. Onboarding
*5 new items*

- [ ] No analytics, ad, or tracking SDK fires before the required consent is given (EU/UK and similar).
- [ ] ATT pre-prompt explains tracking before the iOS system prompt, shown only if you actually track.
- [ ] Onboarding progress saved so users resume where they left off.
- [ ] Onboarding steps instrumented as a funnel.
- [ ] Onboarding fully usable with a screen reader and large text.

---

## 3. Profile
*6 new items*

- [ ] EXIF/GPS metadata stripped from uploaded images.
- [ ] Uploaded photos scanned for nudity and CSAM before public display, if profiles are public.
- [ ] Email and phone hidden from the public profile by default.
- [ ] Username change rules: cooldown, and old handles held back to prevent impersonation.
- [ ] Verified badge criteria documented; badges never sold in a misleading way.
- [ ] "Report impersonation" path.

---

## 4. Settings
*7 new items*

- [ ] Consent center: view and withdraw each consent (analytics, ads, personalization, marketing) as easily as it was given.
- [ ] "Do Not Sell or Share My Personal Information" and "Limit the Use of My Sensitive Personal Information" (CPRA) where applicable.
- [ ] Time zone setting (drives reminders, quiet hours, and email timing).
- [ ] Security section: 2FA, passkeys, active sessions, login history.
- [ ] Connected apps / integrations with revoke access.
- [ ] Links to Terms, Privacy, Cookies, Licenses, Accessibility Statement, and Delete Account.
- [ ] In-app accessibility settings (text size, reduce motion, captions) where the OS doesn't cover them.

---

## 5. Color Themes & UI
*9 new items*

- [ ] Color is never the only signal (errors, status, charts).
- [ ] Touch targets at least 44×44 pt (iOS) / 48×48 dp (Android).
- [ ] Logical focus order; fully operable by keyboard and switch control.
- [ ] Every form field has a visible label; errors are announced to assistive tech.
- [ ] Captions or transcripts for video and audio content.
- [ ] Nothing flashes more than 3 times per second.
- [ ] All strings externalized for translation; plurals, dates, numbers, and currency localized.
- [ ] Documented component library reused everywhere (buttons, inputs, modals, toasts, empty states).
- [ ] No dark patterns: no confirmshaming, hidden costs, pre-checked boxes, or hard-to-find cancel flows.

---

## 6. Referral System
*8 new items*

- [ ] No rewards for app store ratings or reviews (Apple and Google both prohibit incentivized reviews).
- [ ] Incentivized shares and endorsements disclosed per the FTC Endorsement Guides.
- [ ] Invites are user-initiated only; the app never messages a user's contacts automatically (TCPA, CAN-SPAM, store rules).
- [ ] Contact-book upload needs explicit permission and is disclosed in the Privacy Policy.
- [ ] Terms cover reward expiry, revocation, and fraud clawback.
- [ ] Cash or cash-equivalent rewards checked for tax reporting (e.g., US 1099 thresholds) and KYC needs.
- [ ] Prize contests or leaderboards follow sweepstakes law (official rules, no purchase necessary, eligibility, void where prohibited).
- [ ] Admin tools to review, approve, and reverse rewards (Section 17).

---

## 7. Ads
*9 new items*

- [ ] app-ads.txt / ads.txt published on the developer website listed in the stores.
- [ ] Google-certified consent platform (IAB TCF v2.2) for EEA, UK, and Swiss traffic.
- [ ] US state privacy signals (GPP string, Global Privacy Control) passed to ad partners; restricted data processing for opted-out users.
- [ ] Sensitive ad categories blocked to fit your audience (gambling, alcohol, dating, politics).
- [ ] If children are in the audience: Google Play Families policy and only Families-certified ad SDKs.
- [ ] Ads clearly labeled "Ad" or "Sponsored"; never disguised as content or placed where accidental taps are likely.
- [ ] Every ad SDK listed in the Privacy Policy, App Store privacy labels, Play Data Safety, and Apple privacy manifest.
- [ ] SKAdNetwork IDs configured in Info.plist.
- [ ] Verified with a network inspector that no ad data leaves the device before consent.

---

## 8. Monetization
*22 new items*

### Consumer Law & Disclosures (new)
- [ ] Price, currency, billing period, renewal price, and trial terms shown before the purchase button.
- [ ] Auto-renewal laws met: clear terms, affirmative consent, confirmation email, online cancellation as easy as signup (US ROSCA, California and other state auto-renewal laws).
- [ ] Annual or pre-renewal reminders where state law requires them.
- [ ] Price increases announced in advance, using the stores' price-consent flows.
- [ ] EU/UK 14-day withdrawal right handled: express consent and acknowledgment before digital content starts immediately.
- [ ] EU "withdrawal function" (button) for online contracts with EU consumers (Directive 2023/2673, applies from June 2026).
- [ ] VAT/GST/sales tax collected and remitted on web sales (Stripe Tax, or a Merchant of Record such as Paddle).
- [ ] Invoices meet local rules (seller details, tax IDs, reverse-charge VAT for B2B).
- [ ] Current store rules followed on linking to web or external purchases, per region (US, EU DMA, and others differ).
- [ ] Loot boxes or other random paid items disclose their odds (Apple requires this).
- [ ] Payments blocked for sanctioned countries and persons (OFAC, EU, UK lists).

### Payments Engineering (new)
- [ ] Raw card data never touches your servers; hosted checkout or fields keep you in PCI DSS SAQ A scope.
- [ ] Strong Customer Authentication / 3-D Secure for EU and UK cards.
- [ ] One entitlement service is the single source of truth for "is this user premium".
- [ ] Store server notifications processed (App Store Server Notifications v2, Google Play RTDN): renew, cancel, refund, revoke, grace, billing retry.
- [ ] Refunds and chargebacks revoke entitlements automatically.
- [ ] Payment webhooks signature-verified and idempotent.
- [ ] Upgrade, downgrade, and proration between tiers.
- [ ] Dunning emails for failed payments.
- [ ] Regional pricing / price localization.
- [ ] Documented process for disputes and chargebacks.
- [ ] Every purchase flow tested in sandbox: buy, renew, cancel, refund, restore, grace, expire.

---

## 9. Notifications
*28 new items*

### Notification Service (new)
- [ ] One central notification service sends through push, email, SMS, in-app, and web push.
- [ ] Templates per event and channel: localized, variable-driven, previewable.
- [ ] User preferences and consent checked server-side before every send.
- [ ] Mandatory security/transactional messages kept separate from optional ones and never used for marketing.
- [ ] Queue with retries, backoff, and a dead-letter queue; sends are idempotent (no duplicates).
- [ ] Rate limits, batching, and digests so users aren't spammed.
- [ ] Sends scheduled in the recipient's time zone.
- [ ] Delivery, open, click, bounce, and failure metrics tracked.
- [ ] Real-time updates for the in-app center (WebSocket/SSE) if the app needs them.
- [ ] Admin announcements/broadcasts with audience targeting, scheduling, test send, and approval (Section 17).

### Push (new)
- [ ] Device tokens registered, refreshed, and removed on logout or when the provider reports them invalid.
- [ ] Android 13+ POST_NOTIFICATIONS permission and a notification channel per category.
- [ ] iOS notification categories; provisional and time-sensitive delivery used only where it fits.
- [ ] No sensitive data in push payloads or lock-screen previews.
- [ ] If permission was denied, an in-app prompt explains how to turn it on in OS settings.

### Email (new)
- [ ] Transactional email provider set up (Postmark, SES, SendGrid, Resend, etc.).
- [ ] SPF, DKIM, and DMARC configured for every sending domain.
- [ ] Transactional and marketing mail sent from separate streams or subdomains.
- [ ] Bounces and complaints handled with a suppression list.
- [ ] One-click unsubscribe headers (List-Unsubscribe + RFC 8058) for Gmail/Yahoo bulk-sender rules.
- [ ] Physical postal address and clear sender identity in marketing email (CAN-SPAM).
- [ ] Opt-outs honored promptly (CAN-SPAM: within 10 business days) and synced across every tool.
- [ ] Double opt-in for marketing lists in the EU (expected in Germany).
- [ ] Templates tested in major clients and dark mode, with a plain-text version.

### SMS (if used) (new)
- [ ] Prior express written consent for marketing texts (TCPA), with the consent logged.
- [ ] STOP and HELP keywords handled automatically.
- [ ] US A2P 10DLC or toll-free verification registered.
- [ ] Texts sent only in allowed hours in the recipient's time zone (8am–9pm federally; some states are stricter).

---

## 10. Legal & Compliance
*76 new items*

- [ ] Acceptable Use Policy.
- [ ] Copyright/DMCA policy with a DMCA agent registered at the US Copyright Office (renew every 3 years), if users can upload content.
- [ ] Imprint/Impressum if you target Germany or Austria.
- [ ] Public subprocessor list, kept current.
- [ ] Security page with a vulnerability disclosure policy.
- [ ] Internal procedure for law-enforcement and government data requests.
- [ ] Past versions of every legal doc archived and retrievable.
- [ ] A lawyer reviewed the Terms, Privacy Policy, refund, and subscription terms before launch, and the sign-off is recorded.

### Terms of Service Coverage (new)
- [ ] Legal entity name, address, and contact.
- [ ] Eligibility and minimum age.
- [ ] License you grant users, and the license you get for their content.
- [ ] Prohibited conduct and your right to suspend or terminate accounts.
- [ ] Payment, renewal, refund, and cancellation terms.
- [ ] Warranty disclaimer and limitation of liability.
- [ ] Indemnity, if appropriate.
- [ ] Governing law, venue, and dispute resolution (arbitration and class-action waivers only with counsel; they don't hold everywhere).
- [ ] How the terms change and how users are told.
- [ ] Accepted by clickwrap (an active checkbox or button), never browsewrap.

### Privacy Policy Coverage (new)
- [ ] Categories of data collected, their sources, and purposes.
- [ ] Legal basis for each purpose (GDPR).
- [ ] Who data is shared with or sold to (categories and subprocessors), including SDKs.
- [ ] Retention period for each data category.
- [ ] International transfers and safeguards (SCCs, EU-US Data Privacy Framework).
- [ ] User rights and how to use them, including appeals where US state laws require.
- [ ] How children's data is handled.
- [ ] Cookies and tracking technologies, and how to opt out.
- [ ] Contact details, DPO, and EU/UK representative if applicable.
- [ ] Notice at Collection (CCPA) at or before each point where data is collected.
- [ ] Policy audited against the data map and every SDK so it matches what the app really does (a mismatch is an FTC deception risk).

### Policy Updates & Re-Acceptance (Proof on File) (new)
- [ ] Every legal doc is versioned: version ID, effective date, content hash, and the full text stored unchanged.
- [ ] Each change classified as material or minor, with the decision and reason recorded (counsel decides what counts as material).
- [ ] Material changes announced ahead of the effective date (e.g., 30 days) by email and in-app notice, with a plain-language summary of what changed.
- [ ] On the next app or web visit after a material Terms change, a blocking screen shows the summary and full text, with an unticked checkbox and an "I agree" button.
- [ ] Privacy Policy changes: notify users; ask for fresh opt-in consent when data is used for a new purpose or shared in a new way (notice alone isn't enough).
- [ ] Server-side enforcement: the API rejects protected requests from users who haven't accepted the current required version (not just a client-side popup).
- [ ] Acceptance record for every acceptance, at signup and on each update: user ID, document type, version ID, content hash, timestamp (UTC), IP, device/user agent, app version, locale, and method (checkbox, button, API).
- [ ] Acceptance records are append-only: never overwritten or deleted with ordinary data, and kept for the retention period counsel sets (usually the account lifetime plus the limitation period).
- [ ] Declining is handled: explain the consequences, let the user export their data and close the account, and apply any grace period consistently.
- [ ] Users who don't respond before the effective date are prompted at next login; paid subscribers are never cut off without the notice their contract requires.
- [ ] Accepted version and date visible to the user in Settings, with a link to that exact version.
- [ ] Admin view: acceptance rate per version, a lookup of any user's acceptance history, and a proof export (PDF/JSON) for disputes (Section 17).
- [ ] Publishing a new version happens through the admin dashboard with approval and an audit log entry, not by editing a live page.
- [ ] Tests cover: new version triggers the prompt, API blocks until acceptance, the record is written with the correct version/hash, decline flow works, old versions stay retrievable.

### Privacy Laws (new)
- [ ] Launch markets listed, and each market's privacy law checked (GDPR, UK GDPR, CCPA/CPRA and other US states, PIPEDA/Quebec Law 25, LGPD, India DPDP, Australia Privacy Act, etc.).
- [ ] Records of Processing Activities (GDPR Art. 30).
- [ ] DPIA for high-risk processing (large-scale sensitive data, profiling, children, precise location).
- [ ] EU/UK representative appointed if you have no office there but target users there (GDPR Art. 27).
- [ ] DPO appointed if required.
- [ ] Global Privacy Control (GPC) honored as an opt-out signal.
- [ ] Sensitive data (health, biometrics, precise location, sexual orientation, etc.) processed only with opt-in consent; check Washington's My Health My Data Act and Illinois BIPA.
- [ ] No sensitive data sent to ad or analytics pixels (FTC GoodRx and BetterHelp cases).
- [ ] Breach notification plan with regulator and user deadlines (Section 22).
- [ ] DPA signed with every vendor that handles personal data.
- [ ] Cookie consent in EU/UK: no non-essential cookies before consent, "Reject all" as prominent as "Accept all", consent logged.

### Children & Age (new)
- [ ] Documented decision: directed at children, mixed audience, or adults only.
- [ ] COPPA, including the 2025 amendments: verifiable parental consent, separate consent before sharing with third parties, data retention limits.
- [ ] UK Age Appropriate Design Code (Children's Code) if UK children may use the app.
- [ ] State app-store age-verification and kids' online safety laws checked; platform age signals used where required (Apple Declared Age Range, Google Play Age Signals).
- [ ] Store age-rating questionnaires answered accurately.

### Consumer Protection & Marketing (new)
- [ ] Marketing claims can be backed up; no fake reviews or hidden paid endorsements (FTC Consumer Reviews and Testimonials Rule).
- [ ] No dark patterns in consent, signup, or cancellation (FTC, EU DSA Art. 25, CPRA).
- [ ] Influencer and affiliate relationships disclosed.
- [ ] Sweepstakes and contests have official rules.

### Regulated Areas (check each one) (new)
- [ ] Health: HIPAA if you work with covered entities, FTC Health Breach Notification Rule, FDA software-as-a-medical-device check.
- [ ] Finance: money transmission licenses, KYC/AML, securities, and lending/credit laws.
- [ ] Education: FERPA and student-privacy laws if schools use the app.
- [ ] Gambling, alcohol, cannabis, firearms, dating, or location tracking: store policies and local laws.
- [ ] Export controls (encryption answers in App Store Connect) and sanctions screening (OFAC, EU, UK).
- [ ] Call or audio recording consent laws, if the app records.

### Intellectual Property (new)
- [ ] Trademark search done for the app name and logo; registration filed in key markets.
- [ ] Fonts, images, icons, sounds, and music licensed for commercial use in an app.
- [ ] Open source licenses audited (no copyleft conflicts, attributions shipped) and an SBOM generated.
- [ ] IP assignment signed by every contributor: employees, contractors, and co-founders.
- [ ] Rights to AI-generated code and assets checked against each AI vendor's terms.

### Accessibility / Disability Compliance
- [ ] Accessibility claims in marketing and in the statement match the actual audit results.
- [ ] Automated accessibility checks run in CI (Section 21).

---

## 11. Content Moderation (if user-generated content)
*12 new items*

- [ ] Written enforcement ladder (warn, restrict, suspend, ban), applied consistently.
- [ ] Ban-evasion detection (device, payment, and email patterns).
- [ ] Moderator tools live in the admin dashboard with RBAC and an audit log (Section 17).
- [ ] Moderator wellbeing: blurred previews, rotation, support.
- [ ] Self-harm and crisis content routes users to help resources.
- [ ] Moderation SLAs tracked against Apple's 24-hour expectation.

### Legal Duties for Hosted Content (new)
- [ ] CSAM: hash-matching on uploads (e.g., PhotoDNA) and mandatory reports to NCMEC (US, 18 U.S.C. §2258A); evidence preserved as the law requires, not just deleted.
- [ ] DMCA notice-and-takedown, counter-notice, and repeat-infringer policy.
- [ ] EU Digital Services Act if you have EU users: notice-and-action form, statement of reasons to affected users, points of contact, complaint handling, transparency reports (micro and small companies are exempt from some duties).
- [ ] EU Terrorist Content Online Regulation: removal within 1 hour of an authority's order.
- [ ] UK Online Safety Act: illegal-content and children's-access risk assessments, reporting and complaints, age checks where required.
- [ ] Evidence preservation and legal hold for reported illegal content.

---

## 12. Support & Feedback
*7 new items*

- [ ] Ticketing system with SLAs and tags (Zendesk, Intercom, Help Scout, or a shared inbox with a tracker).
- [ ] Saved replies for legal requests (data export or deletion, law enforcement, DMCA), each routed to a named owner.
- [ ] Support staff see only what they need: PII masked, access logged (Section 17).
- [ ] Status page linked from the help center.
- [ ] Store reviews monitored and answered.
- [ ] Support channels are accessible (not phone-only, not blocked by CAPTCHA).
- [ ] Support contact details match the store listings and legal docs.

---

## 13. Core App Quality
*8 new items*

- [ ] Double-submit protection and idempotent retries for every write.
- [ ] A session that expires mid-action doesn't lose the user's input.
- [ ] Local database migrations on app update tested.
- [ ] Time zones and daylight saving handled correctly (store UTC, display local).
- [ ] Minimum supported app version enforced server-side.
- [ ] Performance budgets (startup, screen load, bundle size) enforced in CI.
- [ ] Graceful degradation when a third-party service (payments, email, maps, AI) is down.
- [ ] Background work and sync respect battery and OS limits.

---

## 14. Backend & Infra
*15 new items*

- [ ] Infrastructure as code (Terraform, Pulumi, CDK); no environment exists only as console clicks.
- [ ] Versioned, reviewed database migrations using zero-downtime patterns.
- [ ] Background job queue with retries, backoff, and a dead-letter queue.
- [ ] Scheduled jobs (retention cleanup, renewals, reminders) monitored with heartbeats.
- [ ] Idempotency keys on payment, webhook, and other retry-prone endpoints.
- [ ] Liveness/readiness health endpoints and graceful shutdown.
- [ ] Autoscaling, and load tested to 3× the expected peak.
- [ ] Disaster recovery: RPO/RTO defined, encrypted cross-region backups, restore drills on a schedule.
- [ ] Data residency honored if you promise EU (or other regional) hosting.
- [ ] No real production PII in dev or staging; seed or anonymized data only.
- [ ] If multi-tenant: data isolation between tenants enforced and tested.
- [ ] API schema (OpenAPI/GraphQL) documented and kept in sync.
- [ ] Zero-downtime deploys (rolling, blue/green, or canary) with one-click rollback.
- [ ] Cloud cost budgets and alerts.
- [ ] Cloud, email, storage, and CDN accounts owned by the company, not a person.

---

## 15. Analytics
*9 new items*

- [ ] Tracking plan document (event, properties, owner, purpose, legal basis).
- [ ] No PII (emails, names, phone numbers, free text) in event properties.
- [ ] Analytics gated behind consent where required, with consent state passed to every tool.
- [ ] Retention period set in each analytics tool to match the Privacy Policy.
- [ ] IP truncation/anonymization turned on.
- [ ] Revenue events sent from the server (the source of truth), not only from the client.
- [ ] Business KPI dashboard: DAU/MAU, activation, conversion, MRR/ARR, LTV, CAC, churn, refunds.
- [ ] Analytics data deleted or anonymized when a user deletes their account.
- [ ] Analytics vendors covered by DPAs and listed as subprocessors.

---

## 16. Web Presence
*27 new items*

### Required Either Way
- [ ] Domain on auto-renew with registrar lock and 2FA; expiry monitored.
- [ ] Security headers: HSTS, CSP, frame-ancestors, X-Content-Type-Options, Referrer-Policy, Permissions-Policy.
- [ ] /.well-known/security.txt with a security contact.
- [ ] Imprint/Impressum page if you target Germany or Austria.
- [ ] Refund, Cookie Policy, Community Guidelines, and Subprocessor pages where applicable.
- [ ] Global Privacy Control honored, with a "Do Not Sell or Share" footer link where required.
- [ ] Cookie banner: "Reject all" as prominent as "Accept all", nothing pre-ticked, consent logged, easy to reopen.
- [ ] Contact and waitlist forms protected from spam and showing consent text.
- [ ] Website meets WCAG 2.2 AA (EAA and ADA exposure covers the site too).
- [ ] Core Web Vitals in the "good" range.
- [ ] Uptime monitoring for the site and every legal page.
- [ ] Public status page (e.g., status.yoursite.com).
- [ ] Automated check that every legal URL returns 200.

### Route B: Landing Page Only
- [ ] Clear call to action above the fold and repeated down the page.
- [ ] Pricing shows the full price, billing period, and renewal terms.
- [ ] About/company section naming the legal entity.
- [ ] Press kit (logo, screenshots, short bio, press contact).
- [ ] Structured data (JSON-LD) for Organization and SoftwareApplication.
- [ ] Waitlist uses double opt-in and says how the email will be used.
- [ ] Conversion events (store clicks, signups) tracked, respecting consent.
- [ ] Testimonials are real, used with permission, and disclose any incentive.

### Route A: Full Web App
- [ ] Admin dashboard with role-based access (Section 17) is required once anyone other than you supports users.
- [ ] Signed-in home dashboard for users: key data, recent activity, next actions, tailored to their role.
- [ ] Cookies set Secure, HttpOnly, and SameSite; idle session timeout.
- [ ] CORS allow-list limited to your own origins.
- [ ] Signed-in and private pages set to noindex.
- [ ] Session and device management matches mobile.

---

## 17. Admin Dashboard & Role-Based Access — NEW SECTION
*37 new items*

### Roles & Permissions
- [ ] Staff roles defined (e.g., Owner, Admin, Support, Moderator, Finance, Analyst/Read-only, Developer).
- [ ] End-user roles defined (e.g., User, Premium; for teams: Org Owner, Admin, Member, Guest).
- [ ] Permission matrix documented: role × resource × action.
- [ ] Deny by default: every endpoint requires an explicit permission.
- [ ] Authorization enforced on the server for every request (hiding a button is not access control).
- [ ] Object-level checks so users only reach their own or their organization's records.
- [ ] Least privilege: new staff start at the lowest role; elevation is temporary and approved.
- [ ] Only Owners can grant roles; every role change is audit-logged and triggers a notification.
- [ ] Tests cover every role against every protected endpoint (Section 21).

### Admin Access Security
- [ ] Admin panel on its own route or subdomain, not linked publicly, set to noindex.
- [ ] MFA (passkeys preferred) or company SSO required for every staff account.
- [ ] Short admin sessions; re-authentication for destructive actions.
- [ ] IP allow-list, VPN, or zero-trust access (optional).
- [ ] Break-glass account procedure documented, with every use alerted.
- [ ] Quarterly access reviews; access removed the same day someone leaves.

### Audit Log
- [ ] Append-only audit log: who, what, when, target, before/after values, IP, reason.
- [ ] Covers admin actions, role changes, data exports, impersonation, refunds, deletions, and config changes.
- [ ] Searchable and exportable, with a defined retention period.

### Admin Features
- [ ] Overview dashboard: signups, active users, revenue, churn, error rate, queue backlog.
- [ ] User management: search, view, suspend/ban, force logout, resend verification, reset 2FA after an identity check.
- [ ] "View as user" / impersonation requires a reason, expires, shows a banner, and is logged.
- [ ] PII masked by default; revealing it requires a permission and is logged.
- [ ] Moderation queue with reports, actions, appeals, and SLA timers.
- [ ] Billing view: subscriptions, refunds, credits, comps (Finance role only).
- [ ] Referral and reward review with fraud flags.
- [ ] Feature flags, remote config, maintenance mode, and force-update controls.
- [ ] Notification and announcement composer with targeting, scheduling, preview, test send, and approval.
- [ ] Content management for FAQ, changelog, banners, and legal document versions.
- [ ] Privacy request (DSAR) queue with deadlines: export, delete, correct, opt-out.
- [ ] Bulk actions with a preview/dry run and a confirmation step.
- [ ] Data exports rate-limited, permission-gated, and logged.
- [ ] Links to observability dashboards and the status page (Section 18).

### Teams & Organizations (if B2B or shared workspaces)
- [ ] Organizations/workspaces with invites, roles, and seat management.
- [ ] Transfer ownership, leave, and remove-member flows.
- [ ] Org-level audit log visible to org admins.
- [ ] Tenant isolation tests prove no data leaks across organizations.
- [ ] SSO and SCIM provisioning for enterprise customers (optional).

---

## 18. Observability & Monitoring — NEW SECTION
*23 new items*

### Logging
- [ ] Structured (JSON) logs with request/correlation IDs across client, API, and workers.
- [ ] Central log aggregation (Datadog, Grafana/Loki, CloudWatch, Axiom, etc.).
- [ ] No passwords, tokens, secrets, card numbers, or unneeded PII in logs; redaction enforced in code.
- [ ] Log retention defined and consistent with the Privacy Policy.
- [ ] Audit and security logs stored apart from application logs.

### Metrics & Tracing
- [ ] Rate, errors, and duration per endpoint; saturation metrics for infrastructure.
- [ ] Distributed tracing (OpenTelemetry) across services, queues, and third-party calls.
- [ ] Database monitoring: slow queries, connections, replication lag, storage growth.
- [ ] Queue and cron monitoring: depth, age, failures, missed heartbeats.
- [ ] Business metrics watched (signups, logins, purchases, notification delivery), with alerts on sudden drops.

### Errors & Client Monitoring
- [ ] Error tracking on backend, web, and mobile (Sentry, Crashlytics, etc.), tagged by release.
- [ ] Source maps, dSYMs, and ProGuard/R8 mappings uploaded on every build.
- [ ] Crash-free users target (e.g., ≥ 99.5%) and Android ANR rate tracked.
- [ ] Real user monitoring: Core Web Vitals, app start time, screen load time.

### Alerting & SLOs
- [ ] SLOs for availability and latency of critical journeys, with error budgets.
- [ ] Alerts on user-facing symptoms, routed to on-call (PagerDuty, Opsgenie, etc.) by severity.
- [ ] Every alert links to a runbook.
- [ ] Synthetic checks for signup, login, purchase, and the landing page from several regions.
- [ ] Expiry alerts for SSL certificates, domains, push certificates/keys, and signing keys.
- [ ] Security signals alerted: failed-login spikes, admin actions, WAF blocks, unusual data exports.

### Dashboards
- [ ] Service health dashboard, release dashboard with deploy markers, and business dashboard.
- [ ] Public status page driven by real checks.
- [ ] Observability vendors covered by DPAs; sampling and cost kept under control.

---

## 19. Security Hardening — NEW SECTION
*45 new items*

- [ ] Threat model for auth, payments, admin, file uploads, and data export.
- [ ] Reviewed against OWASP ASVS (web/API) and OWASP MASVS (mobile).
- [ ] Parameterized queries, output encoding, SSRF protection, safe deserialization.
- [ ] File uploads: type and size validation, malware scanning, served from a separate domain or bucket.
- [ ] Encryption in transit (TLS 1.2+) and at rest; field-level encryption for the most sensitive data; keys in a KMS.
- [ ] WAF, DDoS protection, and bot protection on signup, login, password reset, and checkout.
- [ ] Mobile: no secrets in the binary, code obfuscation, App Attest / Play Integrity on sensitive APIs.
- [ ] Least-privilege IAM for cloud and databases; no shared accounts; root/owner accounts locked with MFA.
- [ ] MFA on every company account: cloud, GitHub, registrar, DNS, app stores, email, payments.
- [ ] Secret scanning in CI and pre-commit; secrets rotated on a schedule and when someone leaves.
- [ ] Dependency and container scanning (Dependabot/Renovate, Snyk, Trivy) with patch deadlines by severity.
- [ ] Static analysis (SAST) in CI; dynamic scanning (DAST) against staging.
- [ ] Protected main branch: required reviews and passing CI; third-party CI actions pinned by commit SHA.
- [ ] Third-party penetration test before launch and after major changes; findings fixed or risk-accepted in writing.
- [ ] Vulnerability disclosure policy (bug bounty optional).
- [ ] SOC 2 / ISO 27001 roadmap if you sell to businesses.

### Input Limits & Validation
- [ ] Every text field has a maximum (and where sensible, minimum) length, enforced in the UI, on the server, and in the database column.
- [ ] Length limits documented per field (name, username, bio, post, comment, message, search query, email, URL) with a visible character counter on long fields.
- [ ] Every request validated on the server against a schema (types, formats, ranges, allowed values); unknown fields rejected.
- [ ] Client-side validation is for convenience only; the server never trusts it.
- [ ] Request body size limit, JSON depth limit, and header size limit set at the gateway and the app.
- [ ] Numeric limits enforced: quantities, amounts, and IDs can't be negative, zero, or absurdly large where that makes no sense.
- [ ] Arrays and batch endpoints capped (maximum items per request).
- [ ] Pagination has a maximum page size; no endpoint can return an unbounded list.
- [ ] File uploads capped by size, count, dimensions, and duration; type checked by content, not just extension.
- [ ] Text trimmed and Unicode-normalized; control characters, zero-width characters, and null bytes stripped or rejected.
- [ ] User-entered HTML or Markdown sanitized with an allow-list before it is stored or rendered.
- [ ] Only allow-listed fields can be written by users (no mass assignment of role, price, owner ID, or verified flags).
- [ ] Redirect and callback URLs checked against an allow-list (no open redirects).
- [ ] Regular expressions safe from catastrophic backtracking; search and filter inputs length-limited.
- [ ] GraphQL depth, complexity, and alias limits; introspection off in production (if GraphQL).
- [ ] Error responses never expose stack traces, SQL, file paths, or internal IDs.

### Rate Limiting & Abuse Controls
- [ ] Rate limits on every endpoint, with tighter limits by user, IP, device, and API key where it matters.
- [ ] Strict limits on sensitive endpoints: login, signup, password reset, OTP/verification send and verify, email change, promo/referral code entry.
- [ ] Limits on anything that costs money per call: SMS, email, push, AI requests, file processing, exports.
- [ ] OTP and verification codes: limited attempts, short expiry, cooldown between resends, invalidated after use.
- [ ] Limits on content creation (posts, comments, messages, invites, reports, uploads) to stop spam and scraping.
- [ ] Per-user quotas for storage, uploads, and API usage, shown to the user before they hit them.
- [ ] Rate-limited responses return 429 with a Retry-After header; clients back off and show a friendly message.
- [ ] Limits stored centrally (e.g., Redis) so they hold across multiple servers.
- [ ] Timeouts on every inbound request, outbound call, and database query; slow or expensive queries capped.
- [ ] Idempotency or duplicate detection so repeated taps and retries can't create duplicates or double charges.
- [ ] Enumeration blocked: sequential IDs not guessable, and responses don't reveal whether a user, email, or code exists.
- [ ] Limits and blocks are logged and alerted (Section 18), with an admin way to lift a block for a real user.
- [ ] Tests cover: over-length input rejected, oversized body rejected, limit exceeded returns 429, limits reset correctly.

---

## 20. Privacy Engineering & Data Governance — NEW SECTION
*12 new items*

- [ ] Data map: every field, where it's stored, purpose, legal basis, retention, who can access it, and which vendors receive it.
- [ ] Data minimization review: stop collecting fields you don't need.
- [ ] Retention schedule enforced by automated deletion or anonymization jobs.
- [ ] Privacy request tooling across all systems and vendors: export (machine-readable), delete, correct, restrict, opt out.
- [ ] Identity verification for privacy requests; deadlines tracked (GDPR: one month; CCPA: 45 days).
- [ ] Consent records (what, when, version, source) stored, and withdrawals passed on to vendors.
- [ ] Privacy-protective defaults (private profile, no marketing, minimal sharing).
- [ ] Access to production data restricted, justified, and logged.
- [ ] Vendor/subprocessor register with DPAs and transfer mechanisms.
- [ ] Review (privacy, security, license) required before adding any new SDK or vendor.
- [ ] Apple privacy manifest, App Store privacy labels, and Play Data Safety rebuilt from the data map every release.
- [ ] Legal hold can pause deletion for specific accounts.

---

## 21. Testing & QA — NEW SECTION
*21 new items*

### Automated
- [ ] Written test strategy: what is covered by unit, integration, E2E, and manual testing.
- [ ] Unit tests for business logic, with a coverage floor on critical modules.
- [ ] Integration tests against a real database and queue (e.g., Testcontainers).
- [ ] E2E tests for critical journeys: signup, verify, login, 2FA, reset, onboarding, purchase, restore, cancel, data export, account deletion, notification opt-out.
- [ ] Authorization matrix tests: every role against every protected endpoint, including cross-tenant access.
- [ ] Payment and webhook tests (sandbox plus replayed events).
- [ ] Notification tests: preferences respected, templates render, unsubscribe works.
- [ ] Consent tests prove no tracking or ad network calls happen before consent.
- [ ] Automated accessibility tests (axe, Lighthouse, Accessibility Scanner, XCTest audits).
- [ ] Visual regression tests for key screens in light and dark mode.
- [ ] Migration tests: database up/down, and upgrading from the previous app version keeps user data.
- [ ] Contract tests between the mobile/web clients and the API.
- [ ] Load tests at expected peak; soak tests for leaks.
- [ ] Link checks confirm every legal and support URL is live.
- [ ] CI runs lint, type-check, tests, and build on every PR; merging is blocked on failure.
- [ ] Flaky tests quarantined and fixed, never quietly deleted.

### Manual
- [ ] Screen reader pass (VoiceOver, TalkBack, NVDA).
- [ ] Device and browser matrix pass, including the oldest supported OS and small screens.
- [ ] Poor network, offline, and airplane-mode pass.
- [ ] Localization pass (pseudo-locale, long strings, RTL).
- [ ] Written release test plan signed off before each release.

---

## 22. Incident Response & Business Continuity — NEW SECTION
*9 new items*

- [ ] Incident response plan: severity levels, incident commander, communications owner, escalation path.
- [ ] On-call rotation and a contact list that includes key vendors.
- [ ] Data breach playbook: contain, assess, notify regulators within 72 hours (GDPR), notify users and state regulators as each law requires, bring in counsel and the insurer.
- [ ] Prewritten templates for status page, email, and in-app incident notices.
- [ ] Blameless postmortems with tracked action items.
- [ ] Runbooks for the top failure modes (database down, payment provider down, email blocked, bad deploy, leaked secret).
- [ ] Backup restores tested on a schedule; full disaster recovery drill at least yearly.
- [ ] Credentials for domains, stores, cloud, and payment accounts kept in a shared vault with emergency access, so no single person is a point of failure.
- [ ] Tabletop exercise run before launch.

---

## 23. Business & Company Setup — NEW SECTION
*12 new items*

- [ ] Legal entity formed; the app, domains, and accounts owned by the entity, not an individual.
- [ ] Business bank account and bookkeeping; subscription revenue recognized correctly.
- [ ] Tax registrations in place (EIN, VAT/OSS, sales tax where you have nexus).
- [ ] Apple Developer and Google Play accounts registered as an organization (D-U-N-S) with identity verified.
- [ ] Paid apps agreements, tax forms, and banking details completed in both stores.
- [ ] EU trader status declared in App Store Connect and Play Console (Digital Services Act).
- [ ] Vendor contracts reviewed: DPA, SLA, liability, termination, data return.
- [ ] Founder agreements: equity vesting and confidentiality (IP assignment is in Section 10).
- [ ] Insurance: general liability, professional liability/E&O, cyber; D&O if you raise money.
- [ ] If selling to businesses: MSA, DPA, SLA, and security questionnaire answers ready.
- [ ] Business licenses and registrations your jurisdiction requires.
- [ ] Counsel lined up for the launch review and for emergencies.

---

## 24. AI Features (if the app uses AI) — NEW SECTION
*13 new items*

- [ ] Users told when they are talking to AI or seeing AI-generated content (EU AI Act Art. 50 and US state bot-disclosure laws; confirm current effective dates).
- [ ] AI-generated media labeled or marked where required.
- [ ] AI vendor terms: no training on your users' data, retention limits, DPA signed.
- [ ] Privacy Policy discloses AI processing and names AI vendors as subprocessors.
- [ ] No fully automated decisions with legal or similarly significant effects without human review and an appeal (GDPR Art. 22 and state AI laws such as Colorado's).
- [ ] Prompt-injection defenses; the model can't call tools or read data beyond the current user's permissions.
- [ ] Input and output safety filters, and a way to report bad AI output.
- [ ] Per-user rate limits and cost caps.
- [ ] Health, legal, and financial output carries disclaimers and hands off to humans where appropriate.
- [ ] Chatbot and companion features have safeguards for minors and a self-harm protocol (e.g., California SB 243).
- [ ] Eval suite for AI features runs in CI; regressions block the release.
- [ ] Model versions pinned, with a fallback when the provider is down.
- [ ] AI inputs and outputs logged under the retention policy, with PII minimized.

---

## 25. Documentation & Handoff — NEW SECTION
*9 new items*

- [ ] README with one-command setup, run, test, and deploy.
- [ ] `.env.example` listing every variable with a description (no real values).
- [ ] Architecture diagram and service inventory.
- [ ] API docs generated from the schema.
- [ ] Architecture decision records (ADRs) for major choices.
- [ ] Runbooks (Section 22), data map (Section 20), and permission matrix (Section 17) linked from one place.
- [ ] Release process documented (versioning, changelog, store submission).
- [ ] Ownership register: who owns each account, vendor, domain, and certificate.
- [ ] CHANGELOG kept current.

---

## 26. Launch Prep
*14 new items*

- [ ] Self-review against the Apple App Review Guidelines and Google Play Developer Program Policies.
- [ ] Apple privacy manifest (PrivacyInfo.xcprivacy), including required-reason APIs and third-party SDK manifests.
- [ ] Export compliance / encryption answers set (ITSAppUsesNonExemptEncryption).
- [ ] Age-rating questionnaires completed in both stores.
- [ ] Play target API level meets the current requirement.
- [ ] In-app purchase products created, priced, and submitted with review screenshots.
- [ ] Review notes explain non-obvious features; the demo account has premium access.
- [ ] Store listing claims are accurate, and keywords contain no competitor trademarks.
- [ ] Privacy Policy, support, and marketing URLs entered in both store listings.
- [ ] Phased release (iOS) and staged rollout (Play) configured.
- [ ] Go/no-go checklist: tests green, legal sign-off, backups verified, monitoring and on-call ready.
- [ ] Launch-day dashboard open and on-call staffed.
- [ ] Support macros and FAQ ready for launch-day questions.
- [ ] Release notes written.

---

## 27. Post-Launch Operations — NEW SECTION
*11 new items*

- [ ] Crash rate, reviews, and support tickets checked daily for the first two weeks.
- [ ] Dependency and security updates on a fixed schedule.
- [ ] Yearly platform requirements met: Play target API, Xcode/iOS SDK minimums, store policy changes.
- [ ] Legal docs reviewed at least yearly and whenever data practices, vendors, or markets change.
- [ ] Privacy labels, Data Safety form, and privacy manifest updated whenever an SDK changes.
- [ ] Regulatory watch for each launch market (privacy, AI, accessibility, children, consumer law).
- [ ] Quarterly access review, backup restore test, and cost review.
- [ ] Accessibility re-audit yearly or after a major redesign, with the statement updated.
- [ ] Expiry dates tracked for signing certificates, push keys, provisioning profiles, and domains.
- [ ] Churn and cancellation reasons reviewed and fed into the roadmap.
- [ ] Shutdown plan ready: user notice period, data export window, refunds, store removal.

---
*Not legal advice. The legal items tell you what to check and which documents to have. Confirm with a lawyer in each market you launch in.*
