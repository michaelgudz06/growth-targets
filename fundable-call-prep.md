# Fundable Call Prep — Michael Gudz
*Call with founders · May 2026*

---

## Who I Am (30-second context)

Michael Gudz — BBA student at SFU, graduating [date]. Built a job-search automation tool that pulls recently-funded Canadian startups via your API and renders them into a filterable dashboard with tier scoring, fit analysis, and outreach tracking. I'm reaching out because I've been a power user since signing up, I have genuine product feedback, and I'd love to talk about your GTM motion.

---

## How I Use Fundable

**Use case:** Personal job search — finding recently-funded Canadian startups that match my resume, then running targeted outbound.

**Workflow I built:**
1. Pull companies from the Fundable API filtered by `country=Canada`, `date_range=Jan 2025–May 2026`
2. Score each company against my resume (GTM/growth/RevOps roles, B2B SaaS, fintech, AI)
3. Render into a custom dashboard with tier rankings, fit notes, and outreach playbook
4. Track outreach status per company (active/discarded/favourited)

**Result so far:** Built a list of 115 funded Canadian companies, narrowed to 25 top targets with personalized outreach angles for each.

**What surprised me:** The data freshness. Seeing a funding round appear in Fundable before it hit TechCrunch was a real unlock. That's the moat.

---

## User Feedback — What Works

- **Data freshness is genuinely better than Crunchbase** — for recently-funded companies, Fundable is noticeably faster
- **API is clean to work with** — the company search endpoint (name/domain/LinkedIn/Crunchbase fuzzy matching) just works; zero friction to integrate
- **50-datapoint depth per company** is real — employee count, industry tags, round details, and LinkedIn all present without needing secondary lookups
- **Credit model is accessible** — free 50 credits got me through enough testing to see real value before committing
- **MCP access** (Pro+) is a differentiator vs. every competitor — being able to wire Fundable directly into an AI agent is a category-defining feature that most users haven't discovered yet

---

## User Feedback — Bugs & Friction Points

### 1. People API contact data gaps
When I hit `GET /person/search?domain=gumloop.com`, I get founder names but the contact data fields (email, phone) often return null — even on Pro+ where contact data is listed as included. It's unclear whether this is a data coverage issue or an API misconfiguration. Needs a clear error message or coverage indicator.

**Suggestion:** Show a `contact_coverage_score` per company (e.g., "3/5 decision-makers have verified contact data") so users know what to expect before burning credits.

### 2. No bulk company enrichment endpoint
Right now, enriching 115 companies requires 115 separate API calls. There's no batch endpoint for `GET /companies?domains[]=...`. For anyone building a dashboard or CRM integration, this is a significant rate-limit / cost bottleneck.

**Suggestion:** Add `POST /companies/batch` accepting up to 100 domains per call. This alone would unlock CRM enrichment workflows that are currently impractical.

### 3. Alert data not granular enough for developers
`GET /alerts` returns matches but doesn't include the full company profile in the response — you have to make a second call to `GET /company`. Two-call round trips per alert add up fast in automated workflows.

**Suggestion:** Add an `?include=company,deals,investors` query param to the alerts endpoint so developers can get everything in one call.

### 4. Credit consumption not visible per endpoint
I had to discover empirically (by watching my credit balance) roughly what each endpoint costs. There's no visible per-call cost in the docs or in the API response headers.

**Suggestion:** Return `X-Credits-Used` and `X-Credits-Remaining` in every response header. This is standard practice in data APIs (e.g., Apollo, Hunter.io) and reduces developer anxiety around usage.

### 5. No Canadian/regional data for private company team size
Employee count for Canadian companies is often missing or shows the default `"11-50"` range even when LinkedIn data is clearly more specific. US companies seem more accurate.

**Suggestion:** Either flag data confidence levels per field, or partner with a Canadian company registry data source.

---

## Feature Requests (GTM-Relevant)

### High value — CRM sync
Native HubSpot/Salesforce integration for enrichment workflows: user maps a list of company domains → Fundable auto-enriches all matching records in the CRM. This is the killer GTM use case that converts monthly → annual. Apollo built its entire growth motion around this.

### Medium value — "Trigger" feed
A webhook/feed that fires when a company in my watchlist raises a new round, hires a new CXO, or changes employee headcount by 20%+. This would make Fundable a daily-active product instead of a periodic lookup tool.

### Medium value — Investor relationship graph
For each company, show which investors have portfolio overlap with other companies in my pipeline. This surfaces warm intro paths automatically. Your `/deal/investors` endpoint has the data — it just needs a UI layer.

### Interesting angle — "Job seeker" mode
Right now the product is positioned at VCs and founders. But there's a real use case for ambitious job seekers (like me) who want to find recently-funded companies to target. A lightweight "job seeker" plan ($15–20/mo) with a curated weekly digest of funded companies + basic contact data could drive massive top-of-funnel growth via university communities, career Discord servers, and Slack groups. Low CAC, strong virality.

---

## Why I'm Interested in the GTM/Growth Role

**What I've already demonstrated:**
- Built a full workflow on top of your API in [X days] — shows I understand the product deeply, not just in theory
- Identified your best use cases from the ground up — that's product marketing instinct
- The feedback doc you're reading right now is the kind of thinking I'd apply to your outbound motion daily

**What I bring:**
- Enterprise sales background (Shinden Consulting — $50K+ client engagements, Salesforce implementations, C-suite presentations)
- CRM proficiency: Salesforce, HubSpot — the exact tools your target customers use
- Financial analysis skills (RBC commercial banking) — useful for pricing conversations and ROI positioning
- Built outreach tooling from scratch at NextSpark — I know how GTM actually works at a small team

**What I want to do at Fundable:**
1. Own outbound to the job-seeker and SDR/RevOps buyer segments — an underserved market where I can bring immediate credibility as a user
2. Build the playbook for how Fundable sells into startup ecosystem communities (YC, universities, sales orgs)
3. Help translate user feedback into product priorities — I've already built a pipeline for this

---

## Questions to Ask on the Call

1. What does your current customer mix look like — VCs vs. founders vs. other?
2. Where is growth coming from organically right now?
3. What's the biggest GTM challenge you're solving this quarter?
4. What does the growth/GTM role look like day-to-day — more outbound, product marketing, or partnerships?
5. Are you seeing demand from non-VC users (SDRs, job seekers, recruiters)?

---

## The Ask

"I'd love to explore what a GTM/growth role looks like at Fundable. I've already built something on top of your product, I have genuine user feedback, and I think I can help you reach buyer segments you're not fully addressing yet. Can we talk about what that looks like?"

---

*Prep notes based on Jobloom/startup hiring framework: show rather than tell, reduce uncertainty, lead with evidence.*
