# Complete App Checklist

## 1. Authentication

### Sign Up
- [ ] Email + password signup.
- [ ] Social login: Google, Apple (required by Apple if any social login exists), Facebook.
- [ ] Phone/OTP signup as an option.
- [ ] Email verification link or 6-digit code.
- [ ] Password strength meter + minimum rules.
- [ ] Show/hide password toggle.
- [ ] Confirm password field.
- [ ] Username availability check (live).
- [ ] Referral code field (optional, prefilled from deep link).
- [ ] Checkbox to accept Terms + Privacy Policy.
- [ ] Marketing email opt-in (unchecked by default).
- [ ] Age/DOB gate if content is restricted.
- [ ] Country/region selector.
- [ ] Captcha or bot protection on submit.
- [ ] Clear inline error messages per field.
- [ ] "Already have an account? Log in" link.

### Log In
- [ ] Email/username + password login.
- [ ] Social login buttons match signup options.
- [ ] "Remember me" / stay logged in.
- [ ] Biometric login (Face ID, Touch ID, fingerprint).
- [ ] Magic link / passwordless option.
- [ ] Rate limiting + account lockout after failed attempts.
- [ ] Generic error text so emails can't be enumerated.
- [ ] Session persistence with refresh tokens.

### Password Management
- [ ] Forgot password flow via email.
- [ ] Reset link expires (15–60 min).
- [ ] Reset token is single-use.
- [ ] Change password from inside settings (requires old password).
- [ ] Email notification whenever password changes.
- [ ] Log out all other devices after a reset.

### Security
- [ ] Two-factor authentication (SMS, authenticator app, or email).
- [ ] Backup/recovery codes for 2FA.
- [ ] Active sessions list with device, location, last active.
- [ ] Revoke individual sessions or log out everywhere.
- [ ] Login alert email for new device/location.
- [ ] Passwords hashed (bcrypt/argon2), never stored plain.
- [ ] HTTPS everywhere + secure token storage (Keychain/Keystore).

### Account Deletion
- [ ] In-app "Delete account" button (Apple + Google require this).
- [ ] Confirmation step with password or OTP re-auth.
- [ ] Explain what gets deleted and what is kept.
- [ ] Grace period (e.g. 30 days) before hard delete.
- [ ] Cancel active subscriptions on delete.
- [ ] Export my data before deleting.
- [ ] Deactivate (pause) as a softer alternative.
- [ ] Confirmation email after deletion.

---

## 2. Onboarding
- [ ] Splash screen with logo.
- [ ] 3–4 intro slides explaining core value.
- [ ] Skip button on every onboarding screen.
- [ ] Permission requests explained before the system prompt.
- [ ] Personalization questions (goals, interests, experience).
- [ ] Guest / "try without account" mode if possible.
- [ ] Empty-state screens that teach the first action.
- [ ] Interactive tooltip tour for the main screen.
- [ ] Progress indicator during setup.

---

## 3. Profile
- [ ] Profile photo upload + crop.
- [ ] Default avatar/initials fallback.
- [ ] Display name, username, bio.
- [ ] Email and phone with verified badges.
- [ ] Edit profile screen with save/cancel.
- [ ] Public profile view vs. own profile view.
- [ ] Stats (posts, followers, streaks, points — whatever fits).
- [ ] Account type badge (free, pro, verified).
- [ ] Privacy controls: public, private, friends-only.
- [ ] Block and report users.
- [ ] Linked social accounts management.

---

## 4. Settings
- [ ] Account settings (email, phone, password).
- [ ] Notification preferences per category.
- [ ] Language selector.
- [ ] Region/currency/units.
- [ ] Data & privacy controls.
- [ ] Download my data (GDPR export).
- [ ] Clear cache.
- [ ] Sync / backup toggle.
- [ ] App version + build number displayed.
- [ ] Restore purchases button.
- [ ] Log out button.

---

## 5. Color Themes & UI
- [ ] Light mode.
- [ ] Dark mode.
- [ ] Follow system theme (default).
- [ ] Manual theme override in settings.
- [ ] Theme persists across restarts.
- [ ] Accent color picker (optional premium feature).
- [ ] AMOLED/true-black variant.
- [ ] All colors from a single token/palette file.
- [ ] Contrast checked to WCAG AA.
- [ ] Font size respects system settings.
- [ ] Dynamic type / text scaling support.
- [ ] Reduce motion support.
- [ ] Screen reader labels on every interactive element.
- [ ] RTL layout support if you ship Arabic/Hebrew.
- [ ] Consistent spacing scale and corner radii.
- [ ] Loading skeletons instead of blank screens.
- [ ] Haptic feedback on key actions.
- [ ] Safe area / notch handling.
- [ ] Tablet and landscape layouts.

---

## 6. Referral System
- [ ] Unique referral code per user.
- [ ] Shareable deep link (works on web + app store fallback).
- [ ] Share sheet with WhatsApp, SMS, copy link.
- [ ] Referral code entry during signup.
- [ ] Deferred deep linking so the code survives install.
- [ ] Reward for referrer (credits, free days, cash).
- [ ] Reward for the invited user.
- [ ] Reward only triggers after a qualifying action (verify, subscribe, first purchase).
- [ ] Referral dashboard: invited, pending, completed, earned.
- [ ] Notification when a referral converts.
- [ ] Fraud checks: self-referral, duplicate device, disposable emails.
- [ ] Cap on total rewards per user.
- [ ] Leaderboard or tiered milestones (optional).
- [ ] Terms for the referral program.

---

## 7. Ads
- [ ] Ad network integrated (AdMob, AppLovin, Meta, or mediation).
- [ ] Banner ads placed without blocking content.
- [ ] Interstitial ads at natural breaks only.
- [ ] Frequency cap on interstitials.
- [ ] Rewarded video ads for bonus features/credits.
- [ ] Native ads styled to match the app.
- [ ] App open ad (use sparingly).
- [ ] No ads for paying/premium users.
- [ ] Remove-ads one-time purchase option.
- [ ] Ad consent flow: GDPR/UMP for EU, ATT prompt for iOS.
- [ ] CCPA opt-out for US users.
- [ ] No ads on children-directed content without COPPA compliance.
- [ ] Test ad IDs used in dev, real IDs in production.
- [ ] Ad load failure handled gracefully.
- [ ] Ad revenue tracked in analytics.

---

## 8. Monetization
- [ ] Free vs. premium feature matrix defined.
- [ ] Paywall screen with clear benefits.
- [ ] Subscription tiers (monthly, yearly with discount shown).
- [ ] Lifetime / one-time purchase option.
- [ ] Free trial with clear end date.
- [ ] In-app purchases via StoreKit / Google Play Billing.
- [ ] Stripe or similar for web payments.
- [ ] Restore purchases works on reinstall.
- [ ] Receipt validation server-side.
- [ ] Subscription status synced across devices.
- [ ] Manage/cancel subscription link.
- [ ] Promo codes and discounts.
- [ ] Renewal reminder before trial ends.
- [ ] Grace period for failed payments.
- [ ] Billing history / invoices.

---

## 9. Notifications
- [ ] Push notifications (FCM / APNs).
- [ ] Permission asked at the right moment, not on launch.
- [ ] In-app notification center with read/unread.
- [ ] Email notifications for critical events.
- [ ] Per-category toggles (marketing, social, security, reminders).
- [ ] Quiet hours / do-not-disturb window.
- [ ] Deep link from notification to the right screen.
- [ ] Badge count management.
- [ ] Unsubscribe link in every marketing email.

---

## 10. Legal & Compliance
- [ ] Terms of Service.
- [ ] Privacy Policy.
- [ ] Cookie Policy (web).
- [ ] EULA (Apple requires one or defaults to theirs).
- [ ] Refund / cancellation policy.
- [ ] Subscription terms with auto-renewal disclosure.
- [ ] Community guidelines if there is user content.
- [ ] Disclaimer if health, finance, or legal advice is involved.
- [ ] Data Processing Agreement for B2B.
- [ ] Open source licenses / attributions screen.
- [ ] GDPR: consent, data export, right to be forgotten.
- [ ] CCPA: "Do not sell my data" option.
- [ ] COPPA: age gate if under-13 users are possible.
- [ ] App Store privacy nutrition labels filled in.
- [ ] Google Play Data Safety form filled in.
- [ ] Contact/company address in the policies.
- [ ] Version + last-updated date on each legal doc.
- [ ] Prompt users to re-accept when terms change.
- [ ] Legal docs reachable from settings and signup.

### Accessibility / Disability Compliance
- [ ] Accessibility Statement page (separate legal doc).
- [ ] State the standard you conform to (WCAG 2.2 Level AA).
- [ ] State conformance level: full, partial, or non-conformant.
- [ ] List known limitations and workarounds.
- [ ] Accessibility feedback contact (email + response time promise).
- [ ] Date the statement was last reviewed.
- [ ] ADA Title III compliance (US, public-facing apps).
- [ ] Section 508 / VPAT report if selling to US government or education.
- [ ] European Accessibility Act compliance (mandatory since June 2025 for EU consumer apps).
- [ ] EN 301 549 conformance for EU public sector.
- [ ] AODA compliance if serving Ontario, Canada.
- [ ] Third-party audit or self-assessment on record.
- [ ] Remediation plan with dates for known gaps.
- [ ] Statement linked from settings and website footer.

---

## 11. Content Moderation (if user-generated content)
- [ ] Report content button.
- [ ] Block user.
- [ ] Mute/hide.
- [ ] Automated filter for spam and slurs.
- [ ] Admin review queue.
- [ ] Appeal process.
- [ ] Apple requires all four: filter, report, block, and 24h action.

---

## 12. Support & Feedback
- [ ] Help center / FAQ.
- [ ] Contact support form or email.
- [ ] In-app chat support (optional).
- [ ] Bug report with screenshot + logs attached.
- [ ] Feature request channel.
- [ ] Rate the app prompt (after a positive moment, not randomly).
- [ ] Changelog / "What's new" screen.
- [ ] Social links.

---

## 13. Core App Quality
- [ ] Offline mode / cached data.
- [ ] Clear error states with retry.
- [ ] No-internet banner.
- [ ] Pull to refresh.
- [ ] Search with history and suggestions.
- [ ] Filters and sorting.
- [ ] Pagination or infinite scroll.
- [ ] Undo for destructive actions.
- [ ] Confirmation dialogs for deletes.
- [ ] Deep links / universal links.
- [ ] Share functionality.
- [ ] Force update screen for breaking versions.
- [ ] Maintenance mode screen.
- [ ] Feature flags for safe rollouts.

---

## 14. Backend & Infra
- [ ] Auth service with JWT/refresh tokens.
- [ ] Role-based access control.
- [ ] API rate limiting.
- [ ] Input validation and sanitization on the server.
- [ ] Database backups + tested restore.
- [ ] File/image storage with CDN.
- [ ] Image compression and resizing.
- [ ] Environment separation (dev, staging, prod).
- [ ] Secrets in env vars, never in the repo.
- [ ] Logging and error tracking (Sentry).
- [ ] Uptime monitoring and alerts.
- [ ] CI/CD pipeline.
- [ ] API versioning.
- [ ] Soft deletes and audit trail.

---

## 15. Analytics
- [ ] Analytics SDK installed (Firebase, Mixpanel, PostHog).
- [ ] Key events defined and named consistently.
- [ ] Funnel tracking: install → signup → activation → purchase.
- [ ] Retention and churn dashboards.
- [ ] Crash reporting.
- [ ] Attribution SDK for paid ads.
- [ ] A/B testing framework.
- [ ] Analytics respects user opt-out.

---

## 16. Web Presence

**Pick a route first — everything below branches from it.**
- [ ] Route A: full web app (feature parity with mobile).
- [ ] Route B: landing page only (marketing + legal + store links).

### Required Either Way
- [ ] Domain bought and DNS pointed.
- [ ] HTTPS with auto-renewing SSL cert.
- [ ] www and non-www resolve to one canonical URL.
- [ ] Privacy Policy at a stable public URL (app stores require this).
- [ ] Terms of Service at a stable public URL.
- [ ] Support/contact URL (app stores require this).
- [ ] Account deletion page reachable without installing the app (Google Play requires this).
- [ ] Accessibility Statement page.
- [ ] Cookie banner if you use analytics or ads in the EU.
- [ ] Favicon + Open Graph image for link previews.
- [ ] Meta title and description per page.
- [ ] Mobile responsive down to 360px.
- [ ] Analytics installed.
- [ ] Hosting + deploy pipeline set up.
- [ ] robots.txt and sitemap.xml.
- [ ] 404 page.
- [ ] Legal docs linked in the footer of every page.

### Route B: Landing Page Only
- [ ] Hero with one-line value prop.
- [ ] App Store and Google Play badges (official assets).
- [ ] Smart badge: hide the iOS badge on Android and vice versa.
- [ ] Screenshots or short demo video.
- [ ] Feature highlights (3–6 blocks).
- [ ] Pricing section if the app is paid.
- [ ] FAQ section.
- [ ] Email waitlist / newsletter capture.
- [ ] Social proof: reviews, ratings, user count.
- [ ] Deep link handler so referral links open the app or fall back to the store.
- [ ] Apple App Site Association + Android assetlinks.json hosted at /.well-known/.
- [ ] Referral landing page that carries the code through install.
- [ ] Blog or changelog (optional, helps SEO).
- [ ] Single page is fine — do not over-build.

### Route A: Full Web App
- [ ] Everything in Route B (marketing site still needed, usually at the root or a subdomain).
- [ ] Decide split: marketing at `yoursite.com`, app at `/app` or `app.yoursite.com`.
- [ ] Shared backend/API with the mobile app.
- [ ] Same auth system — one account works on web and mobile.
- [ ] Session handling via httpOnly cookies or secure token storage.
- [ ] Social login configured with web redirect URIs.
- [ ] Password reset links work on web.
- [ ] Feature parity audit: what is web-only, mobile-only, both.
- [ ] Responsive layouts for mobile, tablet, desktop.
- [ ] Keyboard navigation and visible focus states.
- [ ] Browser support matrix defined (last 2 versions).
- [ ] Light/dark theme matches the mobile app.
- [ ] Web payments via Stripe (avoids store commission).
- [ ] Purchases on web unlock premium in the app and vice versa.
- [ ] Subscription status synced across both platforms.
- [ ] PWA: installable, manifest, icons, offline shell.
- [ ] Web push notifications.
- [ ] CSRF protection on state-changing requests.
- [ ] Content Security Policy headers.
- [ ] Rate limiting on public endpoints.
- [ ] Server-side rendering or SSG for SEO on public pages.
- [ ] Image optimization and lazy loading.
- [ ] Lighthouse score checked (performance, SEO, a11y).
- [ ] "Get the mobile app" banner for phone visitors.
- [ ] Error boundary / crash page.
- [ ] Admin dashboard (optional, web is the natural home for it).

---

## 17. Launch Prep
- [ ] App icon in all required sizes.
- [ ] Splash/launch screen.
- [ ] Store screenshots for every device size.
- [ ] App preview video.
- [ ] Store title, subtitle, keywords, description.
- [ ] Marketing website or landing page.
- [ ] Support URL and privacy URL live.
- [ ] Demo account for app review.
- [ ] Beta testing via TestFlight / Play internal track.
- [ ] Localization for target markets.
- [ ] Tested on oldest supported OS version.
- [ ] Tested on small and large screens.
- [ ] Performance: cold start under 2s.
- [ ] App size optimized.
- [ ] Rollback plan for a bad release.
