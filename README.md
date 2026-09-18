# App Launch Checklist

A pre-launch checklist for shipping a complete consumer app — mobile, web, or both.

It covers the parts that sit *around* your core product: the login flow, the legal
docs, the paywall, the ads, the referral loop, the store requirements. The features
that are boring to build, easy to postpone, and expensive to discover missing during
app review or after a launch.

**[→ Open the checklist](list.md)** — 17 sections, ~306 items.

## What's in it

| # | Section | Covers |
|---|---------|--------|
| 1 | Authentication | Signup, login, password reset, 2FA, account deletion |
| 2 | Onboarding | Intro slides, permission priming, empty states |
| 3 | Profile | Photo, bio, privacy controls, block & report |
| 4 | Settings | Notification prefs, language, data export |
| 5 | Color Themes & UI | Light/dark/system, accessibility, RTL, responsive |
| 6 | Referral System | Codes, deep links, two-sided rewards, fraud caps |
| 7 | Ads | Placements, frequency caps, GDPR/ATT/CCPA consent |
| 8 | Monetization | Paywall, tiers, trials, receipt validation |
| 9 | Notifications | Push, in-app center, per-category toggles |
| 10 | Legal & Compliance | ToS, Privacy, GDPR/CCPA/COPPA, accessibility statement |
| 11 | Content Moderation | Report, block, filter — required if you have user content |
| 12 | Support & Feedback | FAQ, bug reports, rate prompt, changelog |
| 13 | Core App Quality | Offline mode, error states, force update, feature flags |
| 14 | Backend & Infra | Auth service, rate limits, backups, secrets, CI/CD |
| 15 | Analytics | Funnels, retention, crash reporting, A/B testing |
| 16 | Web Presence | Landing page vs. full web app — two routes |
| 17 | Launch Prep | Store assets, demo account, beta track, rollback plan |

## How to use it

- Copy `list.md` into your project and tick items off as you go.
- Not every item applies to every app. Skip what doesn't fit, but skip it
  deliberately rather than by forgetting.
- Some sections branch. Section 16 asks you to pick a route (landing page or full
  web app) before working through it.
- Sections 11 and the referral fraud checks only matter if you have user-generated
  content or a referral program.

## The non-optional ones

Most of the list is judgment. These are hard requirements that get apps rejected:

- **In-app account deletion** — required by both Apple and Google.
- **Web-accessible deletion page** — Google Play requires deletion to be reachable
  without installing the app.
- **Sign in with Apple** — required if you offer any other third-party login.
- **Report, block, filter, and 24h moderation** — required by Apple for any app with
  user-generated content.
- **Privacy Policy at a public URL** — required by both stores.
- **Store privacy labels** — App Store nutrition labels and Play Data Safety form.
- **European Accessibility Act** — in force since June 2025 for EU consumer apps.

## Note on the legal sections

The checklist tells you *which documents to have*, not what they should say. Sections
10 and 16 are prompts for a conversation with a lawyer, not a substitute for one —
especially around GDPR, COPPA, and accessibility conformance claims.
