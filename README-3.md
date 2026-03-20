# 🛡️ GigShield — AI-Powered Parametric Income Protection for India's Q-Commerce Delivery Partners

> **Guidewire DEVTrails 2026 | Phase 1 Submission**
> Protecting the Last Mile: Automated income insurance for Zepto / Blinkit / Swiggy Instamart delivery partners against uncontrollable external disruptions.

---

## 📋 Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Persona & Market Research](#2-persona--market-research)
3. [Core Use Case Scenarios](#3-core-use-case-scenarios)
4. [Application Workflow](#4-application-workflow)
5. [Weekly Premium Model](#5-weekly-premium-model)
6. [Policy Logic & Coverage Boundaries](#6-policy-logic--coverage-boundaries)
7. [Parametric Triggers](#7-parametric-triggers)
8. [AI/ML Integration Plan](#8-aiml-integration-plan)
9. [Adversarial Defense & Anti-Spoofing Strategy](#9-adversarial-defense--anti-spoofing-strategy)
10. [Tech Stack & Architecture](#10-tech-stack--architecture)
11. [Real-World API Integrations](#11-real-world-api-integrations)
12. [Development Roadmap](#12-development-roadmap)
13. [Business Viability](#13-business-viability)

---

## 1. Executive Summary

**GigShield** is an AI-powered, fully parametric income protection platform built exclusively for **Q-Commerce delivery partners** (Zepto, Blinkit, Swiggy Instamart) operating in Tier-1 Indian cities. Unlike traditional insurance, GigShield monitors real-world environmental triggers — severe rain, dangerous AQI levels, heatwaves, and declared curfews — and automatically pays workers for lost earning hours with **zero manual claims filing**.

### Why Q-Commerce (not Food or E-Commerce)?

| Dimension | Q-Commerce (Zepto/Blinkit) | Food (Zomato/Swiggy) | E-Commerce (Amazon) |
|---|---|---|---|
| **Disruption Sensitivity** | 🔴 Extreme (10-min SLA, outdoor micro-routes) | 🟠 High | 🟡 Moderate |
| **Income Variability** | 🔴 Very High (surge + flat hours) | 🟠 High | 🟡 Medium |
| **Zone Density** | 🔴 Hyper-local 2km radius | 🟠 City-wide | 🟡 Wide radius |
| **Addressable Market** | ~450K–500K active monthly partners | ~3M | ~2M |

Q-Commerce riders are the most financially exposed: they operate on hyper-local 2-km radius dark store zones, work in all weather to meet the 10-minute delivery promise, and have no formal income protection. **This is the highest-need, least-served segment.**

> **Real-world validation:** SEWA's parametric heat-insurance program in Ahmedabad triggered automatic payouts when temperatures exceeded 40°C, disbursing ₹2.92 crore to 50,000 informal workers in 2024 — proving the model is viable for India's informal workforce. Bajaj Allianz's ClimateSafe (2025) extends this to gig workers with automatic settlement on trigger. GigShield operationalizes this proven model for the digital-native Q-commerce cohort.

---

## 2. Persona & Market Research

### Primary Persona: Rajan, 24, Zepto Delivery Partner, Bengaluru

- Works 6–8 hours/day, earning ₹600–₹900/day (approx. ₹4,200–₹5,500/week)
- Operates from the Koramangala dark store on a 2-km radius
- Android smartphone (budget tier); uses UPI exclusively for payments
- Platform pays weekly — his entire financial planning is week-to-week
- Has **no access to formal insurance.** Platform accident cover does not cover income loss during disruption events.
- *Illustrative scenario based on typical worker profile:* During severe monsoon disruptions, Q-commerce partners in Bengaluru may lose 3–5 working days in an affected month, resulting in estimated income loss of ₹900–₹2,500 for that period.

### Market Size (India, 2025–2026)

| Metric | Data | Source |
|---|---|---|
| Q-Commerce delivery partners (active monthly, late 2025) | ~450,000–500,000 | Economic Times, Nov 2025 |
| Total Q-Commerce market GMV (2025) | >$10 billion | Redseer Strategy Consultants, 2025 |
| Monthly transacting users | ~30 million | Redseer, 2025 |
| Avg. weekly earnings (Tier-1 cities) | ₹4,000–₹6,500 | Blinkit weekly payout model |
| Insurance penetration in this segment | <5% | GigShield pilot assumption |
| **Addressable income-loss pool** | **₹8,000–₹12,000 crore/year** | *Pricing-model assumption — see note* |

> ⚠️ **Model Assumption Note:** The income-loss pool figure is a **Phase 1 pricing simulation assumption** derived from: estimated active workforce × avg. weekly earnings × estimated disruption-event frequency in high-risk monsoon and AQI zones. This is used for policy design and stress-testing, not as an audited market-wide estimate. Real loss frequency will be calibrated against pilot claims data.

### The Insurance Gap

India's parametric insurance market is growing at ~11.3% annually through 2028, yet Q-commerce delivery partners are almost entirely unserved. IRDAI's Bima Sugam digital distribution framework and the Bima Vistaar inclusion scheme create a direct regulatory runway for GigShield's insurer-partnered model.

---

## 3. Core Use Case Scenarios

### Scenario 1: Bengaluru Monsoon Flood *(Environmental — Primary)*

**Trigger:** IMD Bengaluru district rainfall exceeds 65mm/3hrs AND IMD "extremely heavy rain" advisory (>204mm/24hr threshold) is active OR BBMP waterlogging red-alert fires for Koramangala/HSR zone.

Rajan opens the app at 7 AM. GigShield dashboard shows a **RED disruption alert**. His active Standard policy (₹89/week) auto-initiates a claim. By late morning — with zero action from Rajan — ₹416 is transferred via UPI representing 8 lost working hours at his declared hourly rate.

*Prototype SLA: simulated near-instant. Production target: same-day disbursal subject to insurer and banking rails.*

---

### Scenario 2: Delhi Severe AQI Event *(Environmental — Secondary)*

**Trigger:** WAQI API and CPCB official stations both report AQI > 400 (Severe+) for Delhi NCR for ≥ 4 consecutive hours between 6 AM–8 PM.

Priya (Blinkit partner, Dwarka) cannot safely work outdoors. GigShield detects the AQI breach via dual-source validation and auto-initiates her claim. Payout: ₹280 (4 working hours × ₹70/hr declared rate). Both WAQI and CPCB must agree before trigger fires — single-source anomalies do not pay out.

---

### Scenario 3: Mumbai Curfew / Bandh *(Social — Tertiary)*

**Trigger:** Official Section 144 order published in PIB/State gazette for the affected pin code, confirmed via geofence match AND NLP classifier confidence ≥ 0.92 with official source attribution confirmed.

Vikram's (Swiggy Instamart, Andheri) registered operating zone falls inside the declared area. Automated payout within the same working day of official notification. No news aggregator or social media source is sufficient — only verified government publications trigger T5.

---

### Scenario 4: Genuine Network Drop in Bad Weather *(Edge Case — Honest Worker Protected)*

Rajan is at a pickup point when a severe storm cuts mobile connectivity for 40 minutes. His GPS drops mid-shift. GigShield does **not** penalize him. The system looks back 30 minutes: his pre-drop location is confirmed in the active disruption zone, and the weather trigger is already active. His claim processes without interruption — he never sees a flag.

---

## 4. Application Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         GIGSHIELD PLATFORM FLOW                             │
├──────────────┬──────────────────────────────────┬───────────────────────────┤
│   ONBOARDING │      ACTIVE POLICY MANAGEMENT    │   CLAIM & PAYOUT          │
│   (< 5 min)  │                                  │                           │
│              │  • Weekly policy renewal (UPI    │ 1. External trigger        │
│ 1. Phone OTP │    autopay or manual)            │    detected (Weather/AQI/ │
│ 2. Platform  │  • Real-time disruption map      │    Curfew) — dual source  │
│    Worker ID │  • Earnings history + protected  │    validated              │
│    verify    │    hours log                     │                           │
│ 3. Zone      │  • Coverage status badge         │ 2. Anti-Spoofing Check    │
│    Selection │  • Weekly premium alert          │    (Multi-signal, <90s)   │
│    on map    │  • Offline exclusion enforced    │                           │
│ 4. Earnings  │                                  │ 3. Auto Claim Initiated   │
│    bracket   │                                  │    (Zero worker action)   │
│ 5. UPI link  │                                  │                           │
│ 6. Tier      │                                  │ 4. UPI Payout dispatched  │
│    selection │                                  │    (Prototype: simulated; │
│              │                                  │    Production: same-day)  │
│              │                                  │                           │
│              │                                  │ 5. WhatsApp notification  │
└──────────────┴──────────────────────────────────┴───────────────────────────┘
```

### Onboarding (Optimized for Low Digital Literacy)

- **Step 1:** Phone number + OTP — 30 seconds, no email required
- **Step 2:** Platform Worker ID (Zepto/Blinkit partner ID) — cross-validated via mock platform API for active employment status
- **Step 3:** Primary working zone selection (dark store location on Google Maps picker)
- **Step 4:** Weekly earnings bracket selection (₹3,000 / ₹4,500 / ₹6,000+) — bracket locked 30 days post-selection to prevent pre-event tier inflation
- **Step 5:** UPI ID linking for instant payouts
- **Step 6:** Coverage tier selection (Basic / Standard / Premium)

Total onboarding time: **under 5 minutes**, available in English, Hindi, and Kannada.

---

## 5. Weekly Premium Model

### Design Rationale

Gig workers operate week-to-week. Blinkit explicitly markets weekly earnings payouts as a core rider benefit — GigShield mirrors this cadence, aligns with real cash flow, and allows workers to pause during low-risk weeks. **No annual lock-in. No paperwork.**

### Weekly Premium Tiers

| Tier | Weekly Premium | Hourly Payout Rate | Max Daily Payout | Max Weekly Payout | Coverage Hrs/Day |
|---|---|---|---|---|---|
| **Basic** | ₹49 | ₹35/hr | ₹280 | ₹1,120 | Up to 8 hrs |
| **Standard** | ₹89 | ₹52/hr | ₹416 | ₹1,664 | Up to 8 hrs |
| **Premium** | ₹149 | ₹70/hr | ₹560 | ₹2,240 | Up to 8 hrs |

> **Affordability Check:** Standard tier (₹89/week) = **~1.6–2.2% of avg. weekly earnings** (₹4,000–₹5,500). This is below the widely-used 2% affordability threshold for micro-insurance viability in India.

### Competitor Benchmarking

| Product | Weekly Premium Equiv. | Coverage | GigShield Differentiation |
|---|---|---|---|
| **Bajaj Allianz ClimateSafe (2025)** | ~₹69 base | Weather events only | Multi-trigger + AI dynamic pricing + zero-touch claims |
| **SEWA Parametric Heat** | ~₹35 equivalent | Heat events only | Q-Commerce zone-specific, real-time AQI + rain |
| **GigShield Standard** | ₹89 (dynamic) | Weather + AQI + flood + curfew | Platform-embedded, instant payout target |

### AI-Powered Dynamic Pricing

The base weekly premium is adjusted by the risk model at each renewal:

| Risk Factor | Premium Adjustment |
|---|---|
| Historical disruption rate for zone (last 12 weeks) | +/- ₹5–20 |
| Seasonal multiplier (monsoon Jun–Sep: 1.3×; Delhi AQI Nov–Jan: 1.2×) | +/- ₹10–30 |
| Worker platform tenure > 1 year (verified low fraud risk) | -₹5–10 |
| Zone waterlogging index (BBMP/MCGM historical flood data) | +/- ₹5–25 |
| No-claim bonus (0 claims in prior 4 weeks) | -5% of tier base |

**Illustrative pricing example:** Rajan, Standard tier, Koramangala zone, July. Base ₹89 + zone monsoon risk +₹12 + seasonal +₹18 − tenure credit -₹8 = ₹111/week. With a no-claim bonus from June: **₹105/week effective.**

### Revised Unit Economics (Actuarial Structure)

Rather than assuming every trigger causes a full-day payout, GigShield prices on: **event frequency × zone exposure rate × average approved hours lost × fraud-adjusted approval rate.** Early pilots will be launched with conservative caps and insurer-backed reinsurance until real claims data is available.

| Metric | Conservative Scenario | Base Scenario |
|---|---|---|
| Active covered workers (pilot) | 20,000 | 50,000 |
| Avg. effective weekly premium | ₹95 | ₹105 |
| Weekly premium pool | ₹19 lakh | ₹52.5 lakh |
| Zone exposure rate per trigger event | 15–20% | 20–25% |
| Avg. approved payout per triggered worker | ₹280–₹350 | ₹300–₹420 |
| Weekly claims (trigger week) | ₹8.4–₹14 lakh | ₹15–₹26 lakh |
| Loss ratio range | 55–65% | 55–65% |
| IRDAI parametric loss ratio cap | 70% | 70% |
| **Post-reinsurance operating margin** | **~20–25%** | **~25–30%** |

---

## 6. Policy Logic & Coverage Boundaries

A policy term is **7 calendar days** from the activation timestamp.

### What Is Covered

Income interruption caused **exclusively** by predefined external parametric trigger events in the worker's registered operating zone during an active weekly policy window. Payout is calculated against a **pre-agreed benefit table** (hourly rate × disrupted hours) — not reimbursement of actual income. This is standard parametric structure and removes the need for individual income verification at claim time.

### What Is NOT Covered

- Accidents, illness, medical expenses, or hospitalisation
- Vehicle repair, vehicle theft, or fuel costs
- Low order demand **without** an active parametric trigger
- Voluntary time off or personal unavailability
- Personal phone, network, or app issues unrelated to a covered disruption
- Events occurring outside the registered operating zone
- Any period where the worker's platform app shows **"offline/unavailable" status prior to the trigger event activating** — workers who go offline before a trigger fires are ineligible for that event

### Key Policy Rules

| Rule | Detail |
|---|---|
| **Zone lock** | Coverage valid only for the registered zone selected before the weekly window opens |
| **Earnings tier lock** | Selected tier locked for 30 days — cannot be upgraded immediately before a known weather event |
| **Waiting period** | New accounts: 7 calendar days before first claim eligibility |
| **Free-look period** | 7-day free-look from policy activation (IRDAI mandatory for digital policies) |
| **Basis risk disclosure** | If a trigger occurs but the worker is outside the covered zone, no payout is generated. Payout is zone-level and trigger-based, not individual-loss-verified. |
| **Payout cap** | Maximum ₹2,240/week regardless of trigger event count in that week |
| **Fraud & appeal** | Flagged claims enter a rapid-review workflow. Rejected claims have a 72-hour appeal window. |
| **Bima Sugam compliance** | Distribution via IRDAI's Bima Sugam API-compliant digital channel |

---

## 7. Parametric Triggers

All triggers are **objective, third-party verifiable, and monitored every 15 minutes** during active coverage windows (6 AM–10 PM). No worker files, calls, or uploads anything.

Every trigger requires **at least 2 independent data sources to agree** before a payout initiates. Single-source anomalies do not pay out.

### Core Launch Triggers (Phase 2–3)

| # | Trigger | Data Sources | Threshold | Dual-Source Rule | Coverage |
|---|---|---|---|---|---|
| **T1** | Extreme Rainfall | OpenWeatherMap API + IMD district alerts | >65mm/3hrs **OR** IMD "extremely heavy rain" (>204mm/24hr) advisory | OWM ≥ threshold **AND** IMD alert active | Full disrupted hours |
| **T2** | Severe AQI | WAQI API (aqicn.org) + CPCB CAAQMS official stations | AQI > 400 for ≥ 4 consecutive hours (6 AM–8 PM) | WAQI ≥ 400 **AND** CPCB nearest station ≥ 400 | Hours AQI ≥ 400 |
| **T3** | Flooding / Waterlogging | BBMP / MCGM ward-level alerts + OpenWeatherMap | Active red-alert waterlogging for registered zone | Official civic alert **AND** OWM heavy rain ongoing | Full working day |

### Later-Stage Triggers (Phase 3+)

| # | Trigger | Data Sources | Threshold | Coverage |
|---|---|---|---|---|
| **T4** | Heatwave | OpenWeatherMap + IMD heat alert | Temp > 44°C for ≥ 2 consecutive days with IMD advisory | 4 hrs/day (peak heat window 11 AM–3 PM) |
| **T5** | Curfew / Section 144 | PIB official gazette API + State government feed + NLP classifier | Official order for registered pin code ≥ 4 hrs; NLP confidence ≥ 0.92 with official source attribution | Full declared disruption hours |

> **T5 Design Note:** Curfew classification uses only official gazette and government sources — not social media or unverified news aggregators. Geofence match to registered pin code is required before T5 fires. This eliminates false positives from adjacent-district events.

---

## 8. AI/ML Integration Plan

### 8.1 Dynamic Premium Calculation — XGBoost Regression

**Training data:** 3 years of IMD historical weather data (district/pin code level), CPCB AQI historical records, claims patterns from SEWA and AXA Climate parametric pilots, Zepto/Blinkit zone-level delivery data (simulated Phase 1).

**Key features:** Zone waterlogging index, 12-week disruption frequency, seasonal index, platform tenure, earnings tier, TomTom traffic density.

**Output:** Adjusted weekly premium per worker per zone, recalculated at each renewal.

---

### 8.2 Fraud Detection — Gradient Boosted Classifier + Isolation Forest

**Primary anomaly signals:**

| Signal | Description | Weight |
|---|---|---|
| Claim velocity | >5 disruption days in rolling 4-week window | High |
| Offline-before-trigger | Platform shows worker offline before trigger activated | Auto-disqualify |
| Platform cross-check | Active deliveries recorded during claimed disruption hours | Immediate flag |
| Network clustering | Multiple claims from same device ID / IP subnet in narrow window | High |
| Account age + burst | Account < 7 days old + immediate premium + claim | Auto-hold |
| Zone cluster anomaly | Claim spike from single pin code inconsistent with weather zone boundary | Ring investigation |
| Browser / device fingerprint | Fingerprint / session inconsistency across claims | Medium |

**Output:** Risk score 0–1. Score > 0.75 = manual review. Score > 0.90 = auto-hold pending investigation.

---

### 8.3 Curfew / Social Disruption NLP Classifier — DistilBERT

**Model:** Fine-tuned DistilBERT on Indian government alert text.

**Monitored sources:** PIB press releases, State government official feeds, NDMA alerts — **verified government domains only** (not general news feeds or Twitter).

**Confidence threshold for trigger:** ≥ 0.92 AND official source attribution confirmed.

---

## 9. Adversarial Defense & Anti-Spoofing Strategy

> ⚠️ This section directly addresses the DEVTrails 2026 adversarial brief: a coordinated ring of 500 delivery workers using GPS-spoofing apps to fake locations inside a declared weather zone and drain the liquidity pool.

### Core Principle

**GPS coordinates are one of ~12 signals. A fraudster who spoofs GPS has fooled exactly one sensor.** Genuine stranded workers and GPS spoofers produce distinctly different behavioral fingerprints across signals that cannot all be simultaneously manipulated through a consumer spoofing app.

---

### Defense Layer 1 — Differentiation: Genuine Partner vs. GPS Spoofer

| Signal | Genuine Stranded Partner | GPS Spoofer | Available In |
|---|---|---|---|
| **GPS coordinates** | Places them in alert zone ✓ | Spoofed to alert zone ✓ | PWA (browser geolocation) |
| **Location continuity** | Smooth movement path into zone over prior 20–30 min; GPS trail consistent with approaching weather | Sudden appearance in zone with no prior route history | PWA (session history log) |
| **Browser/device fingerprint** | Consistent fingerprint matching onboarding session | Inconsistent, rotating, or emulator signatures | PWA (browser APIs) |
| **IP / session behavior** | IP consistent with declared zone; stable session | Home ISP or residential IP flagged as geographically inconsistent with outdoor delivery zone | PWA |
| **Platform activity** (mock API) | Platform shows worker "active but idle" or last attempt within zone before trigger | Platform shows no active session, different IP, or active deliveries during claimed disruption | Platform API integration |
| **Device motion / accelerometer** | Micro-movements consistent with sheltering behavior (with user permission) | Flat zero-movement — phone stationary at home | PWA (DeviceMotion API, permission-based) |
| **Pre-trigger online status** | Worker "online/available" on platform before trigger activated | Worker was "offline" before trigger — automatic policy exclusion | Platform API |

> **PWA Scope Note:** GigShield's Phase 1–2 web app uses browser geolocation, session continuity, device/browser fingerprint consistency, IP/network anomaly detection, DeviceMotion API (permission-based), and partner-platform activity via mock API. Signals that require OS-level telephony access (raw cell tower IDs, Wi-Fi SSID enumeration) are not claimed for the PWA — they are flagged as production-phase enhancements via native platform SDK integration.

**Decision rule:** A claim requires ≥ 4 of 7 signals consistent with genuine outdoor disruption.
- ≥ 4 consistent → Auto-approve
- 2–3 consistent → Provisional approval (80% payout immediate, 20% held 24 hrs)
- ≤ 1 consistent → Auto-flag for rapid human review

---

### Defense Layer 2 — Syndicate Detection: Coordinated Ring

A single bad actor is hard to detect in isolation. A coordinated ring of 500 produces a **statistically impossible pattern** that the anomaly engine catches.

**1. Temporal spike analysis:** Natural weather events produce a smooth claim ramp over 20–40 minutes. A coordinated ring produces a sharp spike (50+ claims within a 3-minute window) — mathematically inconsistent with organic behavior. Flagged as a coordination signal.

**2. Spatial clustering vs. IP-geo mismatch:** High-density claim GPS cluster in a tight grid cell, but browser IP geo-lookups (Google Geolocation API) show devices scattered across residential areas → mismatch triggers ring investigation.

**3. Device fingerprint graph:** If 20+ "different workers" share near-identical browser fingerprints (user-agent, screen resolution, canvas fingerprint, timezone, language) → app cloning or shared-device ring.

**4. New account velocity:** >15 new accounts created in the same zone within 7 days before a trigger event AND all file claims immediately → high-confidence synthetic identity ring. All new accounts have a mandatory 7-day waiting period.

**5. Platform cross-validation:** Mock Zepto/Blinkit API checks whether the platform recorded the worker completing an active delivery during the same window they claim to be stranded. If yes → immediate disqualification regardless of GPS.

**6. Zone-level payout circuit breaker:** Total claims from any single pin code in a single event cannot exceed 2× the actuarially expected rate for that zone's registered population. Excess claims enter accelerated human review — not automatic approval.

---

### Defense Layer 3 — UX Balance: Protecting Honest Workers

**GigShield's Claim Decision Protocol:**

| Scenario | System Action | Worker-Facing Message |
|---|---|---|
| **Clean claim** (≥4/7 signals consistent, no ring flag) | Auto-approve; payout dispatched | *"Your claim is approved. ₹416 is on its way to your UPI."* |
| **Signal gap** (GPS ok, 2–3 signals temporarily missing due to network disruption in bad weather) | **Provisional approval** — 80% payout released immediately; 20% held up to 24 hrs | *"We've processed your claim. ₹332 is on its way. We're verifying one more data point — remaining ₹84 will arrive by tomorrow morning."* |
| **Flagged claim** (≤2 signals consistent, suspicious timing pattern) | Enters **Rapid Human Review Queue** (2-hr SLA business hours; 4-hr overnight) | *"Your claim is being reviewed by our team. We'll update you within 2 hours."* |
| **High-confidence fraud** (ring detected + device fingerprint match + platform mismatch + offline-before-trigger) | Claim rejected; account flagged | *"We were unable to verify your location. If you believe this is an error, tap here to appeal."* No accusatory language. |
| **Network drop in active weather** (GPS drops, but 30-min lookback confirms pre-drop position in zone + trigger active) | Full auto-approval using location history | No interruption — worker never sees a flag. |

**Appeals:** Any rejected claim can be appealed via a 60-second voice note + timestamped selfie at the claimed location. Appeals reviewed within 4 business hours. No permanent ban on first flag — escalation is proportional to confidence level.

---

### Defense Layer 4 — Proactive Structural Safeguards

| Safeguard | Mechanism |
|---|---|
| 7-day new account waiting period | Prevents burst account creation ahead of known weather events |
| 30-day earnings tier lock | Prevents pre-event tier upgrades (known parametric fraud pattern) |
| Offline-before-trigger exclusion | Policy rule: workers offline before a trigger activates are ineligible for that event |
| Zone-level payout cap | Total payouts per pin code per event capped at actuarial expected loss for that zone |
| Liquidity circuit breaker | If total claims in any 4-hr window exceed 2× the weekly premium pool, automatic payouts pause and all pending claims go to accelerated human review |

---

## 10. Tech Stack & Architecture

### Platform: Mobile-First Progressive Web App (PWA)

**Rationale:** PWA eliminates app store friction (critical for low-digital-literacy workers), works on budget Android devices with 2G/3G, and supports offline resilience during the very disruption events being insured. Workers already use browser-based tools in their Zepto/Blinkit workflow.

### System Architecture

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                          GIGSHIELD ARCHITECTURE                              │
├─────────────────┬────────────────────────────────┬───────────────────────────┤
│   FRONTEND      │         BACKEND                │   EXTERNAL INTEGRATIONS   │
│   (React PWA)   │                                │                           │
│                 │  Node.js + Express REST API    │  OpenWeatherMap API        │
│  React 18+Vite  │  WebSocket (real-time alerts)  │  WAQI AQI API             │
│  Tailwind CSS   │                                │  CPCB CAAQMS (validation) │
│                 │  PostgreSQL                    │  IMD Open Data Portal     │
│  Worker App:    │  (Policies, Claims, Workers,   │  TomTom Traffic API       │
│  ─ Dashboard    │   Fraud flags, Audit logs)     │  BBMP/MCGM (mock)         │
│  ─ Policy Mgmt  │                                │  Razorpay Sandbox (UPI)   │
│  ─ Claim Status │  Redis                         │  Zepto/Blinkit API (mock) │
│  ─ Payout Hist  │  (Trigger cache, sessions)     │  Twilio WhatsApp API      │
│                 │                                │  Google Maps + Geocoding  │
│  Admin Panel:   │  Python + FastAPI (ML Service) │  Google Geolocation API   │
│  ─ Loss ratio   │  ─ XGBoost premium model       │  PIB/State gazette feeds  │
│  ─ Fraud queue  │  ─ Fraud scoring model         │                           │
│  ─ Zone heatmap │  ─ DistilBERT NLP classifier   │                           │
│  ─ Trigger log  │  ─ Ring anomaly detection      │                           │
│  ─ Predictive   │                                │                           │
│    claims view  │  Celery + Redis                │                           │
│                 │  (Async trigger polling        │                           │
│                 │   every 15 minutes)            │                           │
│                 │                                │                           │
│                 │  Apache Kafka (Phase 3)        │                           │
│                 │  (Real-time trigger streams    │                           │
│                 │   at scale)                    │                           │
└─────────────────┴────────────────────────────────┴───────────────────────────┘
```

### Tech Stack

| Layer | Technology | Justification |
|---|---|---|
| **Frontend** | React 18 + Vite + Tailwind CSS | Lightweight, PWA-capable, fast on 3G |
| **Backend API** | Node.js + Express | Fast JSON APIs; WebSocket for real-time disruption alerts |
| **ML Service** | Python + FastAPI | Standard for XGBoost / HuggingFace model serving |
| **Database** | PostgreSQL | Reliable relational store for policies, claims, audit logs |
| **Cache / Queue** | Redis + Celery | 15-minute async trigger polling at scale |
| **Authentication** | JWT + OTP (Twilio SMS) | Phone-number-first; no email required |
| **Payments** | Razorpay Sandbox (UPI + bank transfer) | Real API, sandbox mode, India-native rails |
| **Notifications** | Twilio WhatsApp Business API | Workers prefer WhatsApp; higher engagement than SMS |
| **Hosting** | AWS (EC2, RDS, ElastiCache) | Aligns with Guidewire's AWS partnership |
| **Maps / Geo** | Google Maps Platform + Geolocation API | Zone selection UI + IP-based geo-validation for anti-spoofing |
| **Stream Processing** | Apache Kafka (Phase 3 roadmap) | Real-time trigger stream processing at city scale |
| **ML Models** | XGBoost, DistilBERT, Isolation Forest | Open source, production-proven, Indian NLP support |

---

## 11. Real-World API Integrations

### Active Integrations (Free Tier / Sandbox)

| API | Purpose | Tier |
|---|---|---|
| **OpenWeatherMap API** | Real-time weather, rainfall mm, temperature, 5-day forecast for premium modeling | Free tier |
| **WAQI API (aqicn.org)** | Real-time AQI for 100+ Indian cities; geo-query by lat/lon | Free tier |
| **CPCB CAAQMS** | Official Indian AQI — second-source validation for T2 trigger | Public HTTP |
| **IMD Open Data Portal** | Historical weather for ML training; district-level alerts | Public |
| **TomTom Traffic API** | Hyper-local traffic and road accessibility signal for zone disruption scoring | Free tier |
| **Google Maps Geocoding** | Zone-to-pin-code mapping for trigger geofencing | Free tier |
| **Google Geolocation API** | IP-based location validation for anti-spoofing (PWA-feasible alternative to cell-tower lookup) | Pay-as-you-go |
| **Razorpay Sandbox** | UPI payout simulation with real API structure | Sandbox |
| **Twilio** | WhatsApp notifications (claim approvals, disruption alerts) | Free trial |

### Simulated / Mock Integrations (Phase 1–2)

| API | What Is Mocked | Production Path |
|---|---|---|
| **Zepto/Blinkit Partner API** | Worker ID validation, active session status, earnings history, online/offline status | Live integration via platform partnership agreement |
| **BBMP / MCGM Flood Alert** | Ward-level waterlogging alerts (dynamic JSON mock) | Link to official civic alert RSS/HTTP feeds |
| **PIB / State Gazette** | Curfew and Section 144 notifications for NLP classifier training data | Subscribe to official PIB API in production |

---

## 12. Development Roadmap

### Phase 1 (March 4–20): Ideation & Foundation ✅ *Current*
- [x] Persona research and market validation with cited sources
- [x] Weekly premium model design with competitor benchmarking
- [x] Parametric trigger taxonomy with dual-source validation rules
- [x] Anti-spoofing architecture (multi-signal, PWA-feasible, syndicate detection)
- [x] Policy logic and coverage boundaries defined
- [x] Tech stack selection and architecture diagram
- [x] GitHub repository with README.md

### Phase 2 (March 21 – April 4): Core Platform Build
- [ ] Worker onboarding PWA (React 18, Tailwind, Google Maps zone picker)
- [ ] Policy creation + dynamic premium calculator (live XGBoost call)
- [ ] OpenWeatherMap + WAQI + CPCB API integrations (T1, T2, T3)
- [ ] 3–5 automated parametric triggers with dual-source validation
- [ ] Claims management UI — zero-touch worker flow
- [ ] Razorpay sandbox UPI payout flow
- [ ] Mock Zepto/Blinkit API (worker ID, session status, online/offline)
- [ ] Basic fraud scoring (account age, velocity, platform cross-check)
- [ ] WhatsApp claim notifications via Twilio

### Phase 3 (April 5–17): Scale, Fraud Defense & Dashboards
- [ ] XGBoost premium model trained on IMD/CPCB historical data
- [ ] Full multi-signal anti-spoofing engine (browser signals + platform API + IP geo)
- [ ] Coordinated ring anomaly detection (cluster + device fingerprint + spike timing)
- [ ] Provisional payout UX (80/20 split, 24-hour resolution flow)
- [ ] Admin dashboard: loss ratio, trigger log, fraud alert queue, zone heat map, predictive next-week claims view
- [ ] Worker dashboard: earnings protected tracker, active coverage badge, claim history
- [ ] T4 (heatwave) and T5 (curfew NLP) trigger implementation
- [ ] TomTom traffic signal integration
- [ ] Apache Kafka stream architecture for real-time trigger processing
- [ ] 5-minute demo video + final pitch deck (PDF)

---

## 13. Business Viability

### Market Opportunity

India's Q-commerce sector reached **>$10 billion GMV** with **30 million monthly transacting users** in 2025 (Redseer). Monthly active delivery partners were estimated at **450,000–500,000 in late 2025** (Economic Times), with Zepto and Blinkit holding roughly 60% combined market share. The sector is growing at 40–45% annually, making Q-commerce a practical, focused first wedge for a city-level parametric income-protection product.

GigShield's commercial logic is not to insure every lost rupee. It is to offer a **low-ticket weekly income-stabilization layer** for a worker segment highly exposed to weather and pollution shocks but almost entirely unserved by traditional products.

### Proven Market Precedents

| Precedent | Relevance to GigShield |
|---|---|
| **SEWA Parametric Heat Insurance (India, 2024)** | Automatic payouts for 50,000 informal workers; ₹2.92 crore disbursed on temperature threshold breach — direct proof of viability for India's informal workforce |
| **Bajaj Allianz ClimateSafe (2025)** | Gig-worker-targeted parametric product with automatic settlement; confirms insurer appetite and IRDAI comfort with this structure |
| **AXA Climate India (AQI-linked)** | Automatic cash transfer on AQI breach — direct precedent for GigShield's T2 trigger design |

### Unit Economics

| Metric | Value |
|---|---|
| Customer Acquisition Cost | ₹0 (embedded onboarding via platform partner app) |
| Avg. annual revenue per worker | ₹4,600–₹5,460 (₹89–₹105/week × 52 weeks) |
| Estimated annual worker LTV (3-year) | ₹2,000–₹3,500 |
| CAC payback period | < 4 weeks |
| Estimated weekly churn (opt-out rate) | 8–12% |

### Go-to-Market

1. **Pilot (Q3 2026):** 5,000 Zepto delivery partners in Bengaluru (HSR / Koramangala / Indiranagar zones) — launched ahead of July monsoon season (peak disruption window). Real claims data calibrates the pricing model.
2. **City Scale (Q4 2026):** Expand to Mumbai (MCGM flood zones) and Delhi NCR (November AQI season).
3. **Platform Embed (2027):** In-app distribution within Zepto/Blinkit partner apps, positioned as a **worker welfare initiative** — aligning with platform ESG commitments and IRDAI's Bima Vistaar inclusion mandate.

### Regulatory Alignment

GigShield is designed as an **insurer-partnered parametric protection platform** distributed via a **licensed intermediary / embedded distribution model**, with underwriting retained by a regulated Indian insurer. GigShield does not hold or claim independent underwriting authority.

| Framework | Alignment |
|---|---|
| **IRDAI Bima Sugam** | Distribution via IRDAI's Bima Sugam API-compliant digital channel |
| **IRDAI Regulatory Sandbox** | Available for insurtech pilots; suitable for city-level launch phase |
| **Bima Vistaar** | IRDAI's gig and informal worker inclusion scheme — direct product alignment |
| **IRDAI 70% loss ratio cap** | Pricing model calibrated to remain compliant throughout pilot |

---

## Appendix: Key Data Sources

| Source | URL | Usage |
|---|---|---|
| OpenWeatherMap | api.openweathermap.org | Weather triggers, premium modeling |
| WAQI / aqicn.org | api.waqi.info | AQI triggers |
| CPCB Air Quality | app.cpcbccr.com/AQI_India | AQI second-source validation |
| IMD Open Data | imdpune.gov.in | Historical weather, ML training data |
| TomTom Traffic API | developer.tomtom.com | Zone accessibility signal |
| Razorpay Sandbox | razorpay.com/docs | UPI payout simulation |
| Google Maps / Geolocation API | developers.google.com/maps | Zone selection, IP-based geo-validation |
| Redseer Q-Commerce Report 2025 | redseer.com | Market GMV and user sizing |
| Economic Times (Nov 2025) | economictimes.com | Active Q-Commerce rider count |
| WEF / SEWA Parametric Study | weforum.org | India parametric precedent (50K workers, 2024) |
| Bajaj Allianz ClimateSafe | tradingview.com/news | Competitor benchmarking |
| Incognia Gig Fraud Report 2025 | incognia.com/frontline-report-gig-economy-edition | Anti-spoofing threat intelligence |
| Blinkit Delivery Partner | blinkit.com/delivery | Weekly payout cadence confirmation |
| IRDAI Bima Sugam | irdai.gov.in | Regulatory distribution framework |
| India Corporate Law / IRDAI Distribution Guide | corporate.cyrilamarchandblogs.com | Insurance distribution structure in India |

---

> **GigShield — Because the last mile deserves a safety net.**

**Repository:** [GitHub link]
**Phase 1 Demo Video:** [2-minute walkthrough video link]
**Team:** [Team name]
