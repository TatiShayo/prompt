# 🧠 HERMES ORCHESTRATION SYSTEM
## 5 New Projects + Full Multi-Agent CommandCode Loop
## Hermes spawns CommandCode instances → monitors → refeeds → runs forever

---

# PART 1 — THE NEXT 5 PROJECTS

Chosen for: money ceiling, build speed, zero legal landmines, clear differentiation.
Complements the first 3 (PostPilot/BillFlow/BookFlow) without cannibalizing them.

| # | Project | Kills | Price | MVP | Month 6 MRR |
|---|---|---|---|---|---|
| 1 | **ReviewPilot** | Birdeye / Podium | $15/mo | 3–4 wks | $8K |
| 2 | **StudioPilot** | Mindbody | $29/mo | 6–8 wks | $15K |
| 3 | **AcademiaAI** | Turnitin / Grammarly | $29/mo or $5/doc | 2–3 wks | $12K |
| 4 | **ChamaVault** | Excel / WhatsApp | KES 1,000/mo | 4–5 wks | $4K |
| 5 | **SoloCRM** | HubSpot Free | $10/mo flat | 5–6 wks | $10K |

Why these 5:
- **ReviewPilot** — Athena's own Tier 1 pick. 53% of customers expect replies within 7 days. Most SMBs reply to <10% of reviews. A button that does it with AI in one click at $15/mo is an instant yes.
- **StudioPilot** — Mindbody is genuinely despised. $129–$300/mo, predatory contracts, 20-year-old UX. High ceiling but longer build. Start after the first 3 have revenue.
- **AcademiaAI** — You ALREADY HAVE this pipeline. Package it today. $29/mo or $5 per doc. You know exactly what Turnitin catches. No other SaaS founder does.
- **ChamaVault** — 1M+ chamas in Kenya on Excel/WhatsApp. KES 1,000/mo × 500 chamas = $3,800/mo. Low-maintenance once built. WhatsApp-native.
- **SoloCRM** — HubSpot's bait-and-switch pricing (free → $800/mo) creates rage. $10/mo flat forever with no feature gating is the pitch. Broad market.

Combined Month 6 target with all 8 projects running: **~$67K MRR**

---

# PART 2 — THE HERMES MASTER ORCHESTRATOR PROMPT

## What this does:
Paste this into your Hermes agent. Hermes will:
1. Create all 5 project folders with full scaffolding
2. Write a SPEC.md, PLAN.md, PROGRESS.md, LEARNINGS.md per project
3. Write a Python orchestrator script (`hermes_director.py`) that manages all 5 CommandCode instances
4. Start the orchestrator, which spawns CommandCode per project
5. Each CommandCode instance runs in YOLO mode, builds, commits, exits
6. Orchestrator detects exit, reads PLAN.md, generates next prompt, re-launches
7. All 5 projects build continuously, nonstop, overnight

---

```
HERMES — You are my chief engineering orchestrator. Your job today is to set up 5 new SaaS projects and build a Python system that autonomously runs CommandCode CLI on each of them in a continuous loop. This is a multi-hour, multi-project autonomous build session. You have full authority to create files, run shell commands, install packages, and make every decision without asking me.

Read this entire prompt before starting.

═══════════════════════════════════════
SECTION 1 — ENVIRONMENT AUDIT
═══════════════════════════════════════

First, run these commands to understand your environment:

1. Detect DEV directory:
   - Check if C:\Users\TATI\Desktop\DEV exists (Windows)
   - Or ~/dev or ~/projects (Linux/Mac)
   - DEV_DIR = wherever your other 3 projects (postpilot, billflow, bookflow) are
   - cd into DEV_DIR for all subsequent operations

2. Detect CommandCode binary name:
   Run each until one works:
   - commandcode --version
   - cc --version  
   - code-cli --version
   - ccli --version
   - npx commandcode --version
   Store the working command as CMD_BIN for use throughout

3. Detect CommandCode YOLO flag:
   Try to find in help output: commandcode --help | grep -i "yolo\|skip\|dangerously\|auto"
   Common YOLO flags (try in order until one works):
   - --yolo
   - --dangerously-skip-permissions
   - --auto-approve
   - --yes
   Store working flag as YOLO_FLAG

4. Detect how CommandCode accepts a prompt file:
   Check: commandcode --help | grep -i "prompt\|file\|input\|print"
   Common patterns:
   - commandcode --yolo "$(cat PROMPT.md)"
   - commandcode --yolo < PROMPT.md
   - commandcode --yolo --prompt-file PROMPT.md
   - commandcode --print --yolo "$(cat PROMPT.md)"
   Store working pattern as CMD_PATTERN

5. Check Python version: python --version || python3 --version
6. Check git: git --version
7. Check Node.js: node --version
8. Check npm: npm --version
9. Check tmux: tmux -V (optional, for parallel sessions)

Log all findings to DEV_DIR/hermes_env.txt

═══════════════════════════════════════
SECTION 2 — CREATE THE 5 PROJECT FOLDERS
═══════════════════════════════════════

In DEV_DIR, create these folders and scaffold each:

PROJECTS TO CREATE:
1. reviewpilot
2. studiopilot
3. academiaai
4. chamavault
5. solocrm

For EACH project, run:

cd DEV_DIR
npx create-next-app@latest [projectname] --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes
cd [projectname]

Then install core deps:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch --yes

Then run:
git init (if not already)
git add -A
git commit -m "🚀 Initial scaffold: [projectname]"

Then create these files in each project root:

CREATE [projectname]/SPEC.md with the product spec (see Section 3 below for each project's spec)
CREATE [projectname]/PLAN.md with the build plan (see Section 3)
CREATE [projectname]/PROGRESS.md:
  content: "# [ProjectName] Progress Log\n## Session started: [date]\n"
CREATE [projectname]/LEARNINGS.md:
  content: "# [ProjectName] Learnings & Known Issues\n"
CREATE [projectname]/PROMPT.md:
  content: [the initial build prompt — see Section 3]
CREATE [projectname]/.env.local.example:
  content:
    NEXT_PUBLIC_SUPABASE_URL=
    NEXT_PUBLIC_SUPABASE_ANON_KEY=
    SUPABASE_SERVICE_ROLE_KEY=
    STRIPE_SECRET_KEY=
    NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
    STRIPE_WEBHOOK_SECRET=
    OPENAI_API_KEY=
    RESEND_API_KEY=
    NEXT_PUBLIC_APP_URL=http://localhost:3000

Do all 5 projects in sequence. Log each completion to hermes_env.txt.

═══════════════════════════════════════
SECTION 3 — SPECS, PLANS & INITIAL PROMPTS PER PROJECT
═══════════════════════════════════════

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT 1: reviewpilot/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPEC.md content:
  Product: ReviewPilot — AI Google/Yelp Review Response SaaS
  Tagline: "Respond to every review in one click. Sound human every time."
  Problem: 53% of customers expect review replies within 7 days. Most SMBs respond to <10% of reviews.
  Solution: Connect Google My Business, auto-generate AI responses to every review, approve+post in 1 click.
  Pricing: Free (50 AI responses/mo), Pro $15/mo (unlimited, multi-location), Business $29/mo (white-label, team)
  Kills: Birdeye ($299+/mo), Podium ($249+/mo), Grade.us ($110+/mo)
  Stack: Next.js 14, Supabase, Stripe, OpenAI GPT-4o-mini, Resend, Google My Business API (OAuth)

PLAN.md content:
  ## ReviewPilot Build Plan
  ## PHASE 1: STABILIZE & AUTH
  - [ ] Build passes clean
  - [ ] Auth flow works (signup → login → dashboard)
  - [ ] Supabase schema: profiles, subscriptions, businesses, reviews, responses tables
  ## PHASE 2: CORE PRODUCT
  - [ ] Landing page: hero, features, pricing, comparison vs Birdeye, FAQ
  - [ ] Dashboard: stat cards (reviews today, response rate, avg rating, locations connected)
  - [ ] Business management: add/edit business (name, GMB ID, category, address)
  - [ ] Reviews list: shows reviews pulled from GMB (mock data for MVP, real OAuth later)
  - [ ] Review card: star rating, author, date, review text, "Generate Response" button
  - [ ] AI response generation: POST /api/ai/respond → OpenAI → returns 3 tone variations (professional, friendly, brief)
  - [ ] One-click approve: marks response as approved, shows green checkmark
  - [ ] Post to Google: "Post Response" button (deep-links to GMB for now, full API post after OAuth)
  - [ ] Response history: list of all posted responses with dates
  - [ ] Auto-responder toggle: "Auto-reply to all new reviews" (stores preference, triggers on webhook)
  ## PHASE 3: SETTINGS & BILLING
  - [ ] Business settings: custom response tone, signature, blacklisted words
  - [ ] Stripe subscription integration
  - [ ] Usage tracking (responses used this month)
  ## PHASE 4: TESTING & PERFORMANCE
  - [ ] Unit tests for AI response route
  - [ ] E2e: review card → generate → approve flow
  - [ ] Lighthouse ≥85
  ## PHASE 5: ADVANCED
  - [ ] Sentiment analysis: tag reviews as positive/negative/neutral, filter by sentiment
  - [ ] Response templates library: user-defined templates AI can use as style reference
  - [ ] Competitor monitoring: track competitor's review ratings over time
  - [ ] Weekly digest email: "You received X reviews this week, response rate: Y%"
  - [ ] Multi-language: detect review language, respond in same language

PROMPT.md content:
  You are a senior fullstack engineer. Build ReviewPilot — an AI Google Review Response SaaS — in this Next.js project. YOLO MODE: build everything, make all decisions, no questions asked.
  
  PRODUCT: ReviewPilot helps small businesses respond to Google reviews using AI. Tagline: "Respond to every review in one click."
  KILLS: Birdeye ($299/mo), Podium ($249/mo). Our price: Free / $15/mo Pro.
  
  READ PLAN.md FIRST. Start with Phase 1. Complete every unchecked task [ ] in order.
  After each task: git commit "✅ [phase]: [task]", mark [x] in PLAN.md, continue immediately.
  
  DESIGN: Dark theme. Orange accent #f97316 (reviews/warmth). Background #0a0906. Surface #141210. Border #2a2520.
  
  KEY IMPLEMENTATION:
  AI Response API (src/app/api/ai/respond/route.ts):
    Input: {reviewText, rating, businessName, businessCategory, tone}
    System: "You are a professional business owner. Write a {tone} response to this {rating}-star Google review for {businessName} ({businessCategory}). Be authentic, address specific points in their review, and never sound AI-generated. Return JSON: {variations: [{tone, response}]} — 3 variations: professional, friendly, concise. No preamble. JSON only."
    Model: gpt-4o-mini
  
  DB SCHEMA (create supabase/schema.sql):
    profiles: id, full_name, company_name, subscription_tier, stripe_customer_id
    businesses: id, user_id, name, gmb_id, category, address, is_connected, avg_rating, total_reviews
    reviews: id, business_id, gmb_review_id, author_name, rating, text, posted_at, sentiment, is_responded
    responses: id, review_id, response_text, tone_used, ai_generated, posted_at, approved_by
    subscriptions: id, user_id, stripe_subscription_id, plan, status
  
  Seed 20 realistic fake reviews across 2 fake businesses for demo purposes.
  
  NEVER STOP. Read PLAN.md, find first [ ] task, build it, verify, commit, repeat.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT 2: studiopilot/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPEC.md content:
  Product: StudioPilot — Gym/Yoga/Salon Management SaaS
  Tagline: "Run your studio. Not your software."
  Problem: Mindbody costs $129–$300+/mo with predatory annual contracts and 20-year-old UX.
  Solution: Everything Mindbody does at $29/mo flat, month-to-month, with modern UX.
  Pricing: Starter $29/mo (1 location, unlimited clients), Pro $59/mo (3 locations + staff), Studio $99/mo (unlimited)
  Kills: Mindbody ($129–$300/mo), Acuity Scheduling ($27–$61/mo), Pike13 ($96/mo)
  Stack: Next.js 14, Supabase, Stripe, OpenAI, Resend

PLAN.md content:
  ## StudioPilot Build Plan
  ## PHASE 1: STABILIZE
  - [ ] Build passes clean, auth works, middleware protects dashboard
  ## PHASE 2: CLIENT MANAGEMENT
  - [ ] Landing page: hero, features (class scheduling, client profiles, payments, staff), vs Mindbody comparison
  - [ ] Client list: searchable, with tags (active/inactive/vip), membership status, last visit
  - [ ] Add/edit client: name, email, phone, emergency contact, medical notes, membership tier
  - [ ] Client profile: visit history, class attendance, payment history, notes timeline
  - [ ] Membership plans: create plans (monthly flat, per-class, drop-in), assign to clients
  ## PHASE 3: CLASS SCHEDULING
  - [ ] Class types: create (yoga, spin, HIIT etc.) with duration, capacity, price
  - [ ] Class schedule: weekly recurring schedule (Mon 9am Yoga, etc.)
  - [ ] Class detail: who's booked, waitlist, check-in button
  - [ ] Client booking: clients can book classes via their portal link
  - [ ] Waitlist: automatic promotion when spot opens
  - [ ] Class cancellation: notify booked clients via email
  ## PHASE 4: PAYMENTS
  - [ ] Payment recording: log cash/card/M-Pesa payment per client
  - [ ] Membership billing: Stripe subscriptions for monthly members
  - [ ] Outstanding balance: flag clients with overdue payments
  - [ ] Revenue dashboard: daily/weekly/monthly revenue chart
  ## PHASE 5: STAFF
  - [ ] Staff profiles: name, specialties, schedule
  - [ ] Staff assignment to classes
  - [ ] Staff hours log
  ## PHASE 6: TESTING & POLISH
  - [ ] Unit tests for booking logic (no double-booking, capacity enforcement)
  - [ ] E2e: book a class flow
  - [ ] Mobile responsive (owners check stats on phone)
  - [ ] Lighthouse ≥85
  ## PHASE 7: ADVANCED
  - [ ] Automated birthday emails to clients
  - [ ] Class series packages (10-class pack)
  - [ ] AI class description generator
  - [ ] Retention alerts: flag clients who haven't visited in 30 days
  - [ ] Digital waiver signing: clients sign liability waiver online before first class

PROMPT.md content:
  You are a senior fullstack engineer. Build StudioPilot — a gym/yoga/salon management SaaS — in this Next.js project. YOLO MODE.
  
  PRODUCT: StudioPilot replaces Mindbody at $29/mo flat. Full class scheduling, client management, payments.
  
  READ PLAN.md FIRST. Start with Phase 1. Complete every [ ] task in order. Git commit after each.
  
  DESIGN: Dark theme. Teal accent #14b8a6. Background #09100f. Surface #111a19. Border #1a2e2b.
  
  KEY DB SCHEMA (create supabase/schema.sql):
    profiles, subscriptions (standard)
    locations: id, user_id, name, address, timezone
    clients: id, user_id, first_name, last_name, email, phone, membership_tier, join_date, notes, is_active
    class_types: id, user_id, name, description, duration_minutes, capacity, price, color
    class_schedule: id, class_type_id, instructor_id, start_time, end_time, location_id, is_recurring, day_of_week
    class_instances: id, class_schedule_id, date, is_cancelled, cancellation_reason
    bookings: id, client_id, class_instance_id, status, booked_at, checked_in_at
    staff: id, user_id, name, email, specialties, is_active
    payments: id, client_id, user_id, amount, currency, method, description, paid_at
    memberships: id, client_id, plan_name, price, billing_cycle, start_date, end_date, stripe_subscription_id
  
  Seed: 2 fake locations, 3 class types, 1 week of class schedule, 15 fake clients. Makes the demo immediately useful.
  
  NEVER STOP. PLAN.md drives the work.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT 3: academiaai/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPEC.md content:
  Product: AcademiaAI — AI Academic Writing Humanizer & Enhancement SaaS
  Tagline: "Your work. Just better."
  Problem: Students and researchers use AI but need it undetectable + academically polished.
  Solution: AI humanizer + academic enhancer + plagiarism-risk scorer. You have the pipeline already.
  Pricing: Free (3 docs/mo), Pro $19/mo (unlimited, all tools), Pay-per-doc $5/doc (no sub needed)
  Kills: Grammarly Business ($25/mo, no AI humanizing), QuillBot ($9.95/mo, basic), Undetectable.ai ($10/mo, limited)
  Stack: Next.js 14, Supabase, Stripe, OpenAI, Resend

PLAN.md content:
  ## AcademiaAI Build Plan
  ## PHASE 1: STABILIZE
  - [ ] Build passes, auth works
  ## PHASE 2: CORE TOOLS — THE PRODUCT
  - [ ] Landing page: "Your work. Just better." hero, 4 tool cards, before/after demo, pricing
  - [ ] Dashboard: word count processed this month, documents saved, subscription tier, quick tool launcher
  - [ ] TOOL 1 — AI Humanizer (/dashboard/humanize):
      - Textarea input (paste AI text)
      - Humanization level slider: Subtle / Balanced / Aggressive
      - "Humanize" button → POST /api/tools/humanize
      - Side-by-side output: Original left, Humanized right
      - AI detection score badge (before vs after, simulated 0-100)
      - Copy output button, Save to documents button
  - [ ] TOOL 2 — Academic Enhancer (/dashboard/enhance):
      - Input: paste text + select level (High School / Undergraduate / Masters / PhD)
      - "Enhance" button → POST /api/tools/enhance
      - Output: rewritten text with formal vocabulary, better structure, academic tone
      - Change highlights: show what was changed (before/after diff view)
  - [ ] TOOL 3 — Plagiarism Risk Scanner (/dashboard/plagiarism):
      - Input: paste text
      - Analyze button → POST /api/tools/plagiarism-risk
      - Output: risk score (0-100), flagged sentences highlighted in orange/red, suggestions to rephrase
      - Note: this is an AI-based RISK estimator, not a real plagiarism database check
  - [ ] TOOL 4 — Citation Generator (/dashboard/citations):
      - Input: paste a URL, DOI, book title, or author
      - Select format: APA, MLA, Chicago, Harvard
      - Generate button → returns formatted citation
      - Copy button
  - [ ] Documents library: saved processed docs with name, date, word count, which tool used
  - [ ] Document detail: view original + processed version, re-process option
  ## PHASE 3: PAYMENTS
  - [ ] Pay-per-doc flow: if free tier limit hit → Stripe Payment Link for $5 → unlock one doc
  - [ ] Pro subscription: Stripe checkout → unlimited access
  - [ ] Usage tracking: count docs processed this month per user
  ## PHASE 4: TESTING
  - [ ] Unit test: humanizer API (mock OpenAI, verify text is transformed)
  - [ ] Unit test: academic enhancer (verify vocabulary level changes)
  - [ ] Unit test: usage limit enforcement (free user hits 3 docs, gets paywall)
  - [ ] E2e: paste text → humanize → copy output
  - [ ] Lighthouse ≥85
  ## PHASE 5: ADVANCED
  - [ ] Grammar + Style check combined with humanize (one-pass does both)
  - [ ] Bulk upload: process a .docx or .txt file, return processed .docx
  - [ ] Chrome extension stub: landing page section explaining "coming soon" extension
  - [ ] API access (Pro+): users can call the humanizer/enhancer via API key
  - [ ] Leaderboard: "AcademiaAI users have humanized X million words this month" (social proof counter)

PROMPT.md content:
  You are a senior fullstack engineer. Build AcademiaAI — an AI academic writing humanizer SaaS — in this Next.js project. YOLO MODE.
  
  PRODUCT: AcademiaAI helps students and researchers humanize AI-generated text and enhance academic writing quality.
  4 tools: Humanizer, Academic Enhancer, Plagiarism Risk Scanner, Citation Generator.
  
  READ PLAN.md FIRST. Complete every [ ] task in order. Git commit after each.
  
  DESIGN: Dark theme. Indigo accent #6366f1. Background #09090f. Surface #111118. Border #1e1e2e.
  Academic/scholarly aesthetic — clean, trustworthy, serious.
  
  KEY IMPLEMENTATIONS:
  
  /api/tools/humanize (POST):
    Input: {text, level: 'subtle'|'balanced'|'aggressive'}
    System prompt (subtle): "Rewrite this text to sound naturally human-written by a student. Make small vocabulary swaps, vary sentence rhythm, add minor imperfections, remove overly formal AI patterns. Preserve all meaning and academic content. Return only the rewritten text."
    System prompt (aggressive): "Completely rephrase this text so it reads as authentic student writing. Change structure, vocabulary, sentence variety significantly. Keep all facts and arguments. Sound like a real person wrote this during a late-night study session. Return only the rewritten text."
    Model: gpt-4o (not mini — quality matters here)
  
  /api/tools/enhance (POST):
    Input: {text, level: 'highschool'|'undergraduate'|'masters'|'phd'}
    Prompt: "Rewrite this text to match {level} academic writing standards. Improve vocabulary, sentence structure, argument clarity, and formal tone. Maintain original meaning. Return only the enhanced text."
  
  /api/tools/plagiarism-risk (POST):
    Input: {text}
    Prompt: "Analyze this academic text for plagiarism risk. Identify sentences that appear generic, overly common, or likely to match existing sources. Return JSON: {riskScore: 0-100, flaggedSentences: [{text, reason, riskLevel: 'low'|'medium'|'high'}], suggestions: [{original, rephrased}]}. JSON only."
  
  Seed 3 sample documents in the docs library for demo.
  
  NEVER STOP. PLAN.md is the source of truth.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT 4: chamavault/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPEC.md content:
  Product: ChamaVault — Digital Chama (Group Savings) Management for Kenya & East Africa
  Tagline: "Your chama. Organized. Transparent. Growing."
  Problem: 1M+ chamas in Kenya run on WhatsApp messages, Excel spreadsheets, and handwritten notebooks.
  Solution: Mobile-first chama management: contributions, loans, fines, minutes, elections, M-Pesa friendly.
  Pricing: KES 500/mo (small chama <10 members), KES 1,000/mo (standard <30), KES 2,000/mo (large 30+)
  Kills: Excel, WhatsApp groups, handwritten ledgers, basic Google Sheets
  Stack: Next.js 14, Supabase, Stripe (for non-Kenya payments), M-Pesa (Daraja API), Resend/WhatsApp

PLAN.md content:
  ## ChamaVault Build Plan
  ## PHASE 1: STABILIZE
  - [ ] Build passes, auth works
  ## PHASE 2: CHAMA SETUP
  - [ ] Landing page: Swahili + English, "Simamia Chama Yako Vizuri" headline, feature list, KES pricing, WhatsApp demo CTA
  - [ ] Create/join chama flow: chairperson creates chama (name, meeting day, contribution amount, frequency)
  - [ ] Member invitation: chairperson invites by email or phone → members receive link to join
  - [ ] Member roles: Chairperson, Treasurer, Secretary, Member
  - [ ] Chama profile: name, photo, founding date, objectives, bank/M-Pesa account info
  ## PHASE 3: FINANCIAL MANAGEMENT — CORE
  - [ ] Contribution tracker: per member, per month — paid/pending/overdue status
  - [ ] Record contribution: treasurer selects member + month + amount → log to DB
  - [ ] M-Pesa contribution: member pays via M-Pesa, treasurer confirms receipt
  - [ ] Contribution summary: table showing all members × all months grid (like a school fees tracker)
  - [ ] Treasury balance: running total of all contributions minus loans minus expenses
  - [ ] Fine management: add fine to member (missed meeting, late contribution), track paid/unpaid
  - [ ] Expense log: record chama expenses (venue, snacks, admin costs) with receipts
  ## PHASE 4: LOANS & DIVIDENDS
  - [ ] Loan applications: member applies, committee votes (approve/reject), disbursement recorded
  - [ ] Loan repayment: track monthly repayments, outstanding balance, interest accrued
  - [ ] Dividend calculator: at year-end, calculate each member's share based on contributions
  - [ ] Dividend distribution: record that dividends were paid out to each member
  ## PHASE 5: MEETINGS & GOVERNANCE
  - [ ] Meeting scheduler: create meeting (date, agenda, venue)
  - [ ] Attendance register: check off members present/absent per meeting
  - [ ] Meeting minutes: textarea to record minutes, PDF export
  - [ ] Voting: create a resolution, members vote yes/no, results recorded
  ## PHASE 6: COMMUNICATION
  - [ ] WhatsApp reminders: generate wa.me link with contribution reminder message per member
  - [ ] Email notifications: contribution due reminder, meeting reminder, loan approval notice
  - [ ] Monthly statement: PDF statement per member showing their contributions, loans, balance
  ## PHASE 7: TESTING & POLISH
  - [ ] Mobile-first CSS (most users on Android, small screens) — test at 360px
  - [ ] Swahili language option (static, just Swahili strings for key UI text)
  - [ ] Unit tests: contribution calculations, loan balance tracking, dividend splits
  - [ ] Lighthouse ≥85
  ## PHASE 8: ADVANCED
  - [ ] Chama constitution: upload/store PDF constitution document
  - [ ] Investment tracker: record chama's investments (property, stock, business) with current value
  - [ ] Multi-chama: one user can be treasurer for multiple chamas
  - [ ] Public chama page: read-only page shareable with potential members (shows objectives, meeting schedule, not financials)
  - [ ] Automated SMS: integrate Africa's Talking API for SMS reminders

PROMPT.md content:
  You are a senior fullstack engineer. Build ChamaVault — a digital chama (group savings) management SaaS for Kenya — in this Next.js project. YOLO MODE.
  
  PRODUCT: ChamaVault replaces Excel + WhatsApp for managing Kenya group savings (chamas). KES 500–2,000/mo.
  
  READ PLAN.md FIRST. Complete every [ ] task in order. Git commit after each.
  
  DESIGN: Dark theme. Yellow/gold accent #f59e0b (money/savings/prosperity). Background #0a0900. Surface #14120a. Border #2a2510.
  Warm, trustworthy, African aesthetic. Use Ubuntu or Nunito font (Google Fonts). Include a subtle kanga-inspired geometric pattern as a subtle background texture (CSS pattern, not image).
  
  CURRENCY HANDLING:
  All amounts in KES (Kenyan Shillings). Format with: new Intl.NumberFormat('en-KE', {style:'currency', currency:'KES'}).format(amount)
  Never show raw numbers. Always KES prefix.
  
  KEY DB SCHEMA (create supabase/schema.sql):
    chamas: id, name, photo_url, founding_date, objective, meeting_day, meeting_frequency, contribution_amount, is_active
    chama_members: id, chama_id, user_id, full_name, phone, role, joined_at, share_units
    contributions: id, chama_id, member_id, month_year, amount_due, amount_paid, paid_at, payment_method, recorded_by
    fines: id, chama_id, member_id, reason, amount, paid, issued_at
    loans: id, chama_id, member_id, amount, interest_rate, disbursed_at, due_date, status, approved_by
    loan_repayments: id, loan_id, amount, paid_at
    expenses: id, chama_id, description, amount, category, expense_date, receipt_url
    meetings: id, chama_id, date, agenda, venue, minutes_text, created_at
    meeting_attendance: id, meeting_id, member_id, present
    votes: id, chama_id, resolution_text, created_at, closes_at
    vote_records: id, vote_id, member_id, vote_value, voted_at
  
  Seed 1 demo chama "Wema Savings Group" with 8 members, 6 months contribution history, 1 active loan.
  
  NEVER STOP. PLAN.md drives everything.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT 5: solocrm/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPEC.md content:
  Product: SoloCRM — Dead-Simple CRM for Solopreneurs at $10/mo Flat
  Tagline: "Every lead. Every deal. No BS pricing."
  Problem: HubSpot starts free then jumps to $800/mo. Salesforce is enterprise. Most solo founders use spreadsheets.
  Solution: Full CRM (contacts, pipeline, tasks, email sequences) at $10/mo, nothing gated, no upsells.
  Pricing: Free (250 contacts, 1 pipeline), Pro $10/mo (unlimited everything, email sequences, AI)
  Kills: HubSpot Free (bait-and-switch), Pipedrive ($14.90/mo, limited free), Monday CRM ($10/mo but complex)
  Stack: Next.js 14, Supabase, Stripe, OpenAI, Resend

PLAN.md content:
  ## SoloCRM Build Plan
  ## PHASE 1: STABILIZE
  - [ ] Build passes, auth works, protected routes
  ## PHASE 2: CONTACTS
  - [ ] Landing page: "Every lead. Every deal. No BS pricing." hero, vs HubSpot comparison table, $10/mo CTA
  - [ ] Contact list: searchable, filterable by tag/status, sortable by name/date/value
  - [ ] Add/edit contact: name, email, phone, company, title, source (cold/referral/inbound), tags, notes
  - [ ] Contact detail: all info, activity timeline, linked deals, tasks, email history
  - [ ] Bulk import: CSV upload with column mapping → parse with papaparse → bulk insert
  - [ ] Duplicate detection: warn if email already exists before adding
  ## PHASE 3: PIPELINE
  - [ ] Create pipeline: user names stages (e.g. Lead → Qualified → Proposal → Won/Lost)
  - [ ] Kanban board: drag-and-drop deals between stages (use custom drag or dnd-kit)
  - [ ] Deal card: contact name, value, probability, days in stage, next task
  - [ ] Add/edit deal: title, contact, value, close date, probability, stage, notes
  - [ ] Deal detail: full info, activity timeline, notes
  - [ ] Won/Lost: mark deal outcome, reason for loss
  - [ ] Revenue forecast: sum of (deal value × probability) for all open deals
  ## PHASE 4: TASKS & FOLLOW-UPS
  - [ ] Task list: all tasks across all contacts, sorted by due date
  - [ ] Add task: title, contact, due date, type (call/email/meeting/follow-up)
  - [ ] Task completion: check off, logs to contact timeline
  - [ ] Overdue tasks: red badge on overdue, daily digest email
  - [ ] Reminders: email reminder 1 day before task due date via Resend
  ## PHASE 5: EMAIL SEQUENCES
  - [ ] Sequence builder: create multi-step email sequence (Step 1: Day 0, Step 2: Day 3, Step 3: Day 7)
  - [ ] Each step: subject, body (with {{firstName}}, {{company}} merge tags), delay days
  - [ ] Enroll contact: assign contact to sequence, system schedules emails automatically
  - [ ] Email sending: Resend sends scheduled emails, logs to contact timeline
  - [ ] Unsubscribe: every email has unsubscribe link, marks contact as opted-out
  ## PHASE 6: AI ASSISTANT
  - [ ] AI email writer: "Write a follow-up email for {{contactName}} who showed interest in {{product}}" → generates draft
  - [ ] AI deal summary: "Summarize the status of my {{dealTitle}} deal" → reads timeline, writes summary
  - [ ] AI next step suggester: given deal stage + days stuck → suggests best next action
  ## PHASE 7: TESTING & POLISH
  - [ ] Unit tests: pipeline calculations, sequence scheduling logic, merge tag replacement
  - [ ] E2e: add contact → create deal → move through pipeline → mark won
  - [ ] Mobile: contact list and pipeline kanban must work at 375px
  - [ ] Lighthouse ≥85
  ## PHASE 8: ADVANCED
  - [ ] Chrome extension: capture LinkedIn profile → auto-add as contact in SoloCRM
  - [ ] Email tracking: track opens and clicks on sent emails (pixel tracking via Resend webhooks)
  - [ ] Meeting notes: text field per contact, AI generates action items from notes
  - [ ] Zapier webhook: trigger automations when deal stage changes or contact added

PROMPT.md content:
  You are a senior fullstack engineer. Build SoloCRM — a dead-simple CRM for solopreneurs at $10/mo flat — in this Next.js project. YOLO MODE.
  
  PRODUCT: SoloCRM. HubSpot alternative. $10/mo, nothing gated, no upsells. Features: contacts, pipeline, tasks, email sequences, AI assistant.
  
  READ PLAN.md FIRST. Complete every [ ] task in order. Git commit after each.
  
  DESIGN: Dark theme. Cyan accent #06b6d4. Background #09100f. Surface #0f1a1c. Border #1a2e30.
  Clean, no-nonsense aesthetic. The anti-enterprise CRM. Fast, readable, frictionless.
  
  KEY IMPLEMENTATIONS:
  
  Kanban pipeline (install dnd-kit: npm install @dnd-kit/core @dnd-kit/sortable @dnd-kit/utilities):
    DndContext + SortableContext per column
    onDragEnd → update deal.stage_id in Supabase + log move to timeline
    Optimistic UI: update locally first, sync to DB in background
  
  Email sequences (scheduling):
    When contact enrolled in sequence, create scheduled_emails records:
    scheduled_emails: id, contact_id, sequence_id, step_number, scheduled_at, sent_at, opened_at
    A Supabase Edge Function (or a check on dashboard load): SELECT * FROM scheduled_emails WHERE scheduled_at <= now() AND sent_at IS NULL → send via Resend → mark sent
  
  Merge tags:
    Replace {{firstName}}, {{lastName}}, {{company}}, {{dealTitle}} before sending
    Function: replaceMergeTags(template, contact) → string
  
  KEY DB SCHEMA (create supabase/schema.sql):
    profiles, subscriptions (standard)
    contacts: id, user_id, first_name, last_name, email, phone, company, title, source, tags text[], notes, is_opted_out, created_at
    pipelines: id, user_id, name, is_default
    pipeline_stages: id, pipeline_id, name, order_index, probability, color
    deals: id, user_id, contact_id, pipeline_id, stage_id, title, value, close_date, probability, notes, won_at, lost_at, lost_reason
    deal_timeline: id, deal_id, event_type, description, created_at
    tasks: id, user_id, contact_id, deal_id, title, due_date, type, is_complete, completed_at
    email_sequences: id, user_id, name, is_active
    sequence_steps: id, sequence_id, step_number, delay_days, subject, body
    sequence_enrollments: id, contact_id, sequence_id, enrolled_at, current_step, is_active
    scheduled_emails: id, contact_id, sequence_id, step_id, scheduled_at, sent_at, subject, body
  
  Seed: 1 demo pipeline "Sales Pipeline" with stages (Lead/Contacted/Proposal/Negotiation/Won/Lost), 12 fake contacts, 8 fake deals spread across stages.
  
  NEVER STOP. PLAN.md. First [ ] task. Go.

═══════════════════════════════════════
SECTION 4 — WRITE THE PYTHON ORCHESTRATOR
═══════════════════════════════════════

After all 5 folders are scaffolded, create this file:
DEV_DIR/hermes_director.py

Write the FULL Python script with this logic:

```python
#!/usr/bin/env python3
"""
hermes_director.py — Autonomous multi-project CommandCode orchestrator
Manages 5 parallel SaaS builds. Spawns CommandCode per project.
When process exits, reads PLAN.md, generates follow-up, relaunches.
Runs forever until all tasks complete.
"""
import subprocess, os, time, threading, json, re, datetime
from pathlib import Path

# ══════════════════════════════════
# CONFIGURATION — edit these
# ══════════════════════════════════
DEV_DIR = Path(__file__).parent  # same folder as this script
CMD_BIN = "commandcode"  # or "cc", "ccli" — set to working binary
YOLO_FLAG = "--yolo"  # or "--dangerously-skip-permissions"
LOG_FILE = DEV_DIR / "hermes_master.log"
MAX_RESTARTS = 999  # per project (effectively unlimited)
RESTART_DELAY = 5   # seconds between restarts
CHECK_INTERVAL = 30 # seconds between progress checks

PROJECTS = [
    {"name": "reviewpilot",  "dir": DEV_DIR / "reviewpilot"},
    {"name": "studiopilot",  "dir": DEV_DIR / "studiopilot"},
    {"name": "academiaai",   "dir": DEV_DIR / "academiaai"},
    {"name": "chamavault",   "dir": DEV_DIR / "chamavault"},
    {"name": "solocrm",      "dir": DEV_DIR / "solocrm"},
]

# ══════════════════════════════════
# LOGGING
# ══════════════════════════════════
def log(msg):
    ts = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    line = f"[{ts}] {msg}"
    print(line)
    with open(LOG_FILE, "a") as f:
        f.write(line + "\n")

# ══════════════════════════════════
# PLAN.md READER
# ══════════════════════════════════
def count_tasks(project_dir):
    """Count unchecked [ ] and checked [x] tasks in PLAN.md"""
    plan = project_dir / "PLAN.md"
    if not plan.exists():
        return 0, 0
    content = plan.read_text()
    unchecked = len(re.findall(r'\[ \]', content))
    checked = len(re.findall(r'\[x\]', content, re.IGNORECASE))
    return unchecked, checked

def get_current_phase(project_dir):
    """Find which phase has unchecked tasks"""
    plan = project_dir / "PLAN.md"
    if not plan.exists():
        return "PHASE 1"
    content = plan.read_text()
    lines = content.split('\n')
    current_phase = "PHASE 1"
    for line in lines:
        if '## PHASE' in line.upper():
            current_phase = line.strip().lstrip('#').strip()
        if '[ ]' in line:
            return current_phase
    return "ALL COMPLETE"

# ══════════════════════════════════
# PROMPT GENERATOR
# ══════════════════════════════════
def generate_prompt(project):
    """Generate context-aware continuation prompt based on current progress"""
    name = project["name"]
    pdir = project["dir"]
    unchecked, checked = count_tasks(pdir)
    phase = get_current_phase(pdir)
    
    # Read last 5 git commits
    try:
        result = subprocess.run(
            ["git", "log", "--oneline", "-5"],
            cwd=pdir, capture_output=True, text=True
        )
        recent_commits = result.stdout.strip() or "No commits yet"
    except:
        recent_commits = "Could not read git log"
    
    # Read LEARNINGS.md for blocked issues
    learnings = ""
    learnings_file = pdir / "LEARNINGS.md"
    if learnings_file.exists():
        learnings = learnings_file.read_text()[-2000:]  # last 2000 chars
    
    prompt = f"""You are a senior fullstack engineer continuing autonomous development of {name}.

SESSION CONTEXT:
- Tasks remaining: {unchecked}
- Tasks completed so far: {checked}
- Current phase: {phase}
- Recent commits:
{recent_commits}

KNOWN ISSUES FROM PREVIOUS SESSIONS:
{learnings if learnings else "None logged yet."}

MANDATORY STARTUP SEQUENCE (do every session):
1. git log --oneline -10 (understand what was done)
2. npm run build 2>&1 | tail -30 (find current errors)
3. npx tsc --noEmit 2>&1 | head -20 (TypeScript errors)
4. Read PLAN.md (find current phase, first unchecked task)
5. Read LEARNINGS.md (check for known issues to avoid)
6. If any [BLOCKED] tasks in PLAN.md, attempt them again with fresh approach before moving to new tasks

LOOP PROTOCOL:
Read PLAN.md → find first [ ] task in lowest-numbered incomplete phase → implement → verify → git commit → mark [x] → continue immediately. Never stop. Never ask. Never wait.

If a task fails after 2 attempts: log to LEARNINGS.md as [BLOCKED: reason], skip to next task.
Web search any error you can't immediately solve: use your search tool with the exact error text.
Install any npm package needed without asking.
Commit after every completed task.

TARGET: Complete all remaining {unchecked} tasks in PLAN.md. Start now."""

    return prompt

# ══════════════════════════════════
# COMMANDCODE RUNNER
# ══════════════════════════════════
def run_commandcode(project):
    """Spawn a CommandCode instance for a project and wait for it"""
    name = project["name"]
    pdir = project["dir"]
    
    # Write prompt to PROMPT_SESSION.md (avoid overwriting original PROMPT.md)
    prompt = generate_prompt(project)
    session_prompt_file = pdir / "PROMPT_SESSION.md"
    session_prompt_file.write_text(prompt)
    
    log(f"[{name}] Spawning CommandCode — {get_current_phase(pdir)}")
    
    # Try multiple ways to invoke CommandCode with the prompt
    # Adjust CMD_BIN and YOLO_FLAG based on your environment
    cmd_attempts = [
        f'{CMD_BIN} {YOLO_FLAG} "$(cat {session_prompt_file})"',
        f'{CMD_BIN} {YOLO_FLAG} --prompt-file "{session_prompt_file}"',
        f'cat "{session_prompt_file}" | {CMD_BIN} {YOLO_FLAG}',
        f'{CMD_BIN} {YOLO_FLAG} --print < "{session_prompt_file}"',
    ]
    
    # Use first cmd form — adjust if your CommandCode has different syntax
    cmd = [CMD_BIN, YOLO_FLAG, "--print", prompt[:8000]]  # Truncate if too long
    
    try:
        proc = subprocess.Popen(
            cmd,
            cwd=pdir,
            stdout=subprocess.PIPE,
            stderr=subprocess.STDOUT,
            text=True,
            bufsize=1
        )
        
        # Stream output to log
        project_log = pdir / "agent_session.log"
        with open(project_log, "a") as logf:
            logf.write(f"\n\n{'='*50}\nSESSION: {datetime.datetime.now()}\n{'='*50}\n")
            for line in proc.stdout:
                print(f"  [{name}] {line.rstrip()}")
                logf.write(line)
        
        proc.wait()
        exit_code = proc.returncode
        log(f"[{name}] CommandCode exited (code {exit_code})")
        return exit_code
        
    except FileNotFoundError:
        log(f"[{name}] ERROR: CommandCode binary '{CMD_BIN}' not found. Trying alternatives...")
        # Try to find CommandCode
        for alt in ["cc", "ccli", "code-agent", "deepseek"]:
            try:
                subprocess.run([alt, "--version"], capture_output=True, check=True)
                log(f"[{name}] Found alternative: {alt}")
                global CMD_BIN
                CMD_BIN = alt
                return -1  # Retry
            except:
                continue
        log(f"[{name}] Could not find CommandCode. Sleeping 60s before retry.")
        time.sleep(60)
        return -2
    except Exception as e:
        log(f"[{name}] Exception: {e}")
        time.sleep(10)
        return -3

# ══════════════════════════════════
# PROJECT WORKER THREAD
# ══════════════════════════════════
def project_worker(project):
    """Runs forever for one project: spawn → monitor → restart loop"""
    name = project["name"]
    pdir = project["dir"]
    restarts = 0
    
    log(f"[{name}] Worker started")
    
    while restarts < MAX_RESTARTS:
        unchecked, checked = count_tasks(pdir)
        
        if unchecked == 0 and checked > 0:
            log(f"[{name}] 🎉 ALL TASKS COMPLETE ({checked} tasks done). Worker done.")
            break
        
        if unchecked == 0:
            log(f"[{name}] No PLAN.md or no tasks. Waiting for setup...")
            time.sleep(30)
            restarts += 1
            continue
        
        log(f"[{name}] Restart #{restarts+1} — {unchecked} tasks remaining, {checked} done")
        
        # Update PROGRESS.md
        progress_file = pdir / "PROGRESS.md"
        with open(progress_file, "a") as f:
            f.write(f"\n[{datetime.datetime.now()}] Session #{restarts+1} starting. {unchecked} tasks remaining.\n")
        
        # Run CommandCode
        exit_code = run_commandcode(project)
        
        restarts += 1
        
        # After exit, check if we made progress
        new_unchecked, new_checked = count_tasks(pdir)
        progress_made = new_checked - checked
        
        if progress_made > 0:
            log(f"[{name}] ✅ Made progress: {progress_made} new tasks completed. Restarting in {RESTART_DELAY}s...")
        else:
            log(f"[{name}] ⚠️  No progress detected. Restarting anyway in {RESTART_DELAY*3}s...")
            time.sleep(RESTART_DELAY * 2)  # Wait longer if no progress
        
        time.sleep(RESTART_DELAY)
    
    log(f"[{name}] Worker finished after {restarts} sessions.")

# ══════════════════════════════════
# DASHBOARD PRINTER
# ══════════════════════════════════
def print_dashboard():
    """Print a progress summary every CHECK_INTERVAL seconds"""
    while True:
        time.sleep(CHECK_INTERVAL)
        print("\n" + "═"*60)
        print(f"  HERMES DIRECTOR — {datetime.datetime.now().strftime('%H:%M:%S')}")
        print("═"*60)
        for p in PROJECTS:
            pdir = p["dir"]
            unchecked, checked = count_tasks(pdir)
            total = unchecked + checked
            pct = int((checked/total*100)) if total > 0 else 0
            bar = "█" * (pct//10) + "░" * (10-pct//10)
            phase = get_current_phase(pdir)
            print(f"  {p['name']:<15} [{bar}] {pct:3}% — {checked}/{total} tasks — {phase}")
        print("═"*60 + "\n")

# ══════════════════════════════════
# MAIN
# ══════════════════════════════════
if __name__ == "__main__":
    log("="*60)
    log("HERMES DIRECTOR STARTING")
    log(f"Managing {len(PROJECTS)} projects")
    log(f"CMD_BIN: {CMD_BIN} {YOLO_FLAG}")
    log("="*60)
    
    # Verify projects exist
    for p in PROJECTS:
        if not p["dir"].exists():
            log(f"WARNING: {p['name']} directory not found at {p['dir']}")
    
    # Start dashboard thread
    dashboard_thread = threading.Thread(target=print_dashboard, daemon=True)
    dashboard_thread.start()
    
    # Start worker threads — one per project (true parallel)
    threads = []
    for project in PROJECTS:
        t = threading.Thread(target=project_worker, args=(project,), daemon=False)
        t.name = project["name"]
        t.start()
        threads.append(t)
        time.sleep(3)  # Stagger starts slightly to avoid npm conflicts
        log(f"Thread started for {project['name']}")
    
    log("All 5 project workers running in parallel.")
    log("They will restart CommandCode automatically after each session.")
    log("Monitor: tail -f hermes_master.log")
    log("Stop: Ctrl+C")
    
    # Wait for all threads
    try:
        for t in threads:
            t.join()
    except KeyboardInterrupt:
        log("HERMES DIRECTOR stopped by user.")
```

After writing the file, run:
python hermes_director.py (or python3 hermes_director.py)

═══════════════════════════════════════
SECTION 5 — START THE WHOLE SYSTEM
═══════════════════════════════════════

After completing all setup above, run this final sequence:

1. Verify all 5 project folders exist:
   ls DEV_DIR (should show: reviewpilot/ studiopilot/ academiaai/ chamavault/ solocrm/)

2. Verify each has PLAN.md:
   for d in reviewpilot studiopilot academiaai chamavault solocrm; do echo "$d:"; grep -c "\[ \]" $d/PLAN.md; done

3. Run a smoke test: can CommandCode be called from Python subprocess?
   python3 -c "import subprocess; r=subprocess.run(['commandcode','--version'], capture_output=True, text=True); print(r.stdout or r.stderr)"

4. If smoke test passes: python3 hermes_director.py

5. If CommandCode binary name is different, update CMD_BIN in hermes_director.py

6. The system is now autonomous. It will:
   - Run 5 CommandCode instances in parallel
   - Each builds its project using PLAN.md as the task list
   - When CommandCode exits (context limit or task complete), director relaunches it
   - Director reads PLAN.md to generate a fresh, contextually-aware prompt each time
   - Progress is tracked in PROGRESS.md per project
   - Errors/blockers logged to LEARNINGS.md per project
   - Dashboard prints every 30 seconds showing % complete per project

Output a summary when done:
HERMES SETUP COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━
Projects scaffolded: [list with task counts]
Orchestrator: hermes_director.py
To monitor: tail -f hermes_master.log  
To check progress: python3 -c "from hermes_director import *; [print(p['name'], count_tasks(p['dir'])) for p in PROJECTS]"
Starting director now...
━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

# PART 3 — THE 3 ORIGINAL PROJECTS: FOLLOW-UP LOOP INTEGRATION

If you want postpilot, billflow, bookflow ALSO managed by hermes_director.py, add these to the PROJECTS list:

```python
# Add these 3 to PROJECTS in hermes_director.py:
{"name": "postpilot",  "dir": DEV_DIR / "postpilot"},
{"name": "billflow",   "dir": DEV_DIR / "billflow"},
{"name": "bookflow",   "dir": DEV_DIR / "bookflow"},
```

Then it manages all 8 projects simultaneously.

---

# PART 4 — MANUAL OVERRIDE COMMANDS

When you want Hermes to force a specific project to work on something specific:

```bash
# Override: rewrite PROMPT_SESSION.md for a project with a custom instruction
# Then the next restart picks it up automatically

echo "Focus ONLY on fixing the TypeScript errors in billflow. Run npx tsc --noEmit, fix every error, commit, then return to PLAN.md." > billflow/PROMPT_SESSION.md

# Check what a project is currently doing:
tail -f reviewpilot/agent_session.log

# See how many tasks remain across all projects:
for p in reviewpilot studiopilot academiaai chamavault solocrm postpilot billflow bookflow; do
  echo "$p: $(grep -c '\[ \]' $p/PLAN.md 2>/dev/null || echo 'no plan') remaining"
done

# Emergency stop one project's worker (kill its CommandCode process):
pkill -f "commandcode.*reviewpilot"

# See all running CommandCode processes:
ps aux | grep commandcode
```

---

# PART 5 — WHAT HERMES CAN'T DO (needs you once)

These 8 things per project require your 30 seconds each:
1. **Supabase project** — supabase.com → New project → run schema.sql → copy keys to .env.local
2. **Stripe products** — 2 products per project → copy price IDs to .env.local
3. **OpenAI key** — one key shared across all projects → .env.local
4. **Resend key** — resend.com → free tier → one key for all → .env.local
5. **Deploy** — Vercel → import GitHub repo → add env vars → done (2 min per project)

That's it. Everything else Hermes + CommandCode handles.

---

# TOTAL EMPIRE STATS

| Project | Month 6 MRR | Status |
|---|---|---|
| PostPilot | $12,000 | Building (batch 1) |
| BillFlow | $10,000 | Building (batch 1) |
| BookFlow | $8,000 | Building (batch 1) |
| ReviewPilot | $8,000 | Building (batch 2) |
| StudioPilot | $15,000 | Building (batch 2) |
| AcademiaAI | $12,000 | Building (batch 2) |
| ChamaVault | $4,000 | Building (batch 2) |
| SoloCRM | $10,000 | Building (batch 2) |
| **TOTAL** | **$79,000/mo** | **8 products** |
