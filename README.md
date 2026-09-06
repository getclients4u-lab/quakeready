# QuakeReady™ — The 90-Second Earthquake Survival System™

**Build date:** 2026-09-06 · **Builder:** Archie (nightly digital-business builder) · **Budget:** $0 (all free tiers)

## The Niche (why now)
Google Trends (US): **"earthquake now" is the #1 trending topic** (~20,000+ traffic) with "earthquake" at ~10,000+ — dwarfing every other trend. Driver: a Southern California quake cluster (Ontario 3.4/3.2 ≈ Sept 2 with ~730 felt reports, Santa Rosa 3.3, Compton 3.2) plus the Colombia earthquake aftermath (5.7, dozens of aftershocks). Millions of people who "felt it" are now asking the same anxious question: *what do I actually do?* → the perfect info-product gap: fear is spiking faster than preparedness education.

## The Business
- **Brand:** QuakeReady™ (shield + seismograph motif)
- **Product:** The 90-Second Earthquake Survival System™ — 8-part digital PDF system
- **Mechanism:** The 4-Phase Quake Protocol™ — **BEFORE** (hazard hunt, go-bag, family plan) → **DURING** (drop-cover-hold reflex) → **AFTER** (first-hour safety card) → **RECOVER** (12-week tracker)
- **Price:** $19 founder (anchor $97 → $39 after 100 spots)
- **Audience:** Anyone who felt the recent quakes / lives in a quake zone (39 US states + travelers) — "felt it, froze, wants to be ready by tonight"

## Deliverables (8 PDFs in the pack)
1. The QuakeReady Core Guide (the 4-Phase Quake Protocol™ roadmap)
2. The 20-Minute Home Hazard Hunt
3. The 72-Hour Go-Bag Checklist
4. The Drop, Cover, Hold On Drill
5. The Family Emergency Plan
6. The Aftershock & Post-Quake Safety Card
7. The Work/Car/Travel Playbook
8. The 12-Week Quake-Ready Tracker

## Files
- `index.html` — long-form conversion landing page (hero 3-parter, news-urgency strip, myth-busting, 4-phase mechanism, 8-tool stack, offer box w/ guarantee, 6-question FAQ, medical/emergency disclaimer)
- `thank-you.html` — post-purchase page
- `admin.html` — admin dashboard (orders/users/add-user/product review)
- `download.html` — member downloads area (code-gated)
- `api/` — Vercel serverless backend: hub.js, webhook.js, verify.js, admin.js, download.js
- `emails/launch-emails.md` — 3-email launch sequence (teaser / launch / follow-up)
- `vsl/vsl-script.md` — 5–6-min VSL script + 46-slide uppercase storyboard
- `assets/logo.svg` — brand logo

## Live URL
**→ https://quakeready-glow.vercel.app/** (HTTP 200 verified)
- thank-you: https://quakeready-glow.vercel.app/thank-you.html (200)
- repo: github.com/getclients4u-lab/quakeready
- data repo (private): github.com/getclients4u-lab/quakeready-data
- Vercel project: quakeready (git-linked, ssoProtection off)

## Stripe (TEST MODE)
- Payment link: https://buy.stripe.com/test_dRmdRafzy1gL3zp0Kz1Nu0l
- All CTA buttons wired to the paylink; post-payment redirect → /thank-you.html

## Order Stack (proven backend, adapted from GutMap)
- Stripe webhook → `/api/webhook` (HMAC-verified) → stores buyer in private `quakeready-data` repo (buyers.json), registers access user (users.json w/ SHA256-peppered `QR-XXXXX-XXXXX` code), emails the code via AgentMail (QUAKEREADY_MAIL_FROM)
- `/api/verify` checks email+code → unlock downloads; `/api/download` streams the 8 PDFs from the private repo; `/api/admin` = orders/users/add/revoke
- E2E test passed: signed checkout.session.completed → `{"received":true,"stored":1,"registered":1,"emailed":true}`; wrong code → 403; `/product/*.pdf` on public site → 404; PDF download → 200

## Notes
- Content is educational preparedness info built on public guidance from FEMA, Ready.gov, USGS & the American Red Cross; disclaimer on page + thank-you.
- VSL video: script + storyboard produced (no ELEVENLABS_API_KEY in env). Audio + slideshow render ready when key is added.
- Cleanup after E2E: test buyers removed; only Castle (heyeverlastingmemories@gmail.com) has active access.
