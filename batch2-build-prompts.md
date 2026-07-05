# 🚀 BATCH 2 — 5 SaaS Projects: Initial Build Prompts
## ReviewPilot · StudioPilot · AcademiaAI · ChamaVault · SoloCRM

---

| Project | Kills | MVP | Month 6 MRR |
|---|---|---|---|
| **ReviewPilot** | Birdeye / Podium | 3–4 wks | $8K |
| **StudioPilot** | Mindbody | 6–8 wks | $15K |
| **AcademiaAI** | Grammarly / Undetectable | 2–3 wks | $12K |
| **ChamaVault** | Excel / WhatsApp | 4–5 wks | $4K |
| **SoloCRM** | HubSpot Free | 5–6 wks | $10K |

**Build order recommendation:** AcademiaAI first (you already have the pipeline, fastest money), then ReviewPilot, ChamaVault, SoloCRM, StudioPilot last (most complex).

---

## PROMPT 0 — FOLDER SETUP (BATCH 2)
*(Paste into your current CMD window. Scaffolds all 5 new project folders.)*

---

```
You are a senior fullstack engineer. Scaffold 5 production-ready Next.js SaaS projects in the current directory. Run all commands in sequence. Do not ask questions. Auto-accept everything. Create every file specified.

═══════════════════════════════════════
STEP 1 — SCAFFOLD ALL 5 PROJECTS
═══════════════════════════════════════

npx create-next-app@latest reviewpilot --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes
npx create-next-app@latest studiopilot --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes
npx create-next-app@latest academiaai --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes
npx create-next-app@latest chamavault --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes
npx create-next-app@latest solocrm --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --yes

═══════════════════════════════════════
STEP 2 — INSTALL DEPENDENCIES IN EACH
═══════════════════════════════════════

Run inside reviewpilot/:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts @tanstack/react-table
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch popover command --yes

Run inside studiopilot/:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts @tanstack/react-table date-fns-tz
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch popover command calendar --yes

Run inside academiaai/:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts diff
npm install -D @types/diff
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch slider --yes

Run inside chamavault/:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts @react-pdf/renderer papaparse
npm install -D @types/papaparse
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch popover command calendar --yes

Run inside solocrm/:
npm install @supabase/supabase-js @supabase/ssr stripe @stripe/stripe-js lucide-react class-variance-authority clsx tailwind-merge framer-motion date-fns openai resend sonner zod react-hook-form @hookform/resolvers next-themes recharts @tanstack/react-table @dnd-kit/core @dnd-kit/sortable @dnd-kit/utilities papaparse
npm install -D @types/papaparse
npx shadcn@latest init --defaults
npx shadcn@latest add button card input label badge table tabs dialog sheet dropdown-menu select textarea skeleton avatar progress separator tooltip switch popover command --yes

═══════════════════════════════════════
STEP 3 — CREATE .env.local.example IN EACH
═══════════════════════════════════════

Create reviewpilot/.env.local.example:
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_PRO_PRICE_ID=
NEXT_PUBLIC_STRIPE_BUSINESS_PRICE_ID=
OPENAI_API_KEY=
RESEND_API_KEY=
NEXT_PUBLIC_APP_URL=http://localhost:3000

Create studiopilot/.env.local.example:
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_STARTER_PRICE_ID=
NEXT_PUBLIC_STRIPE_PRO_PRICE_ID=
NEXT_PUBLIC_STRIPE_STUDIO_PRICE_ID=
OPENAI_API_KEY=
RESEND_API_KEY=
NEXT_PUBLIC_APP_URL=http://localhost:3000

Create academiaai/.env.local.example:
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_PRO_PRICE_ID=
NEXT_PUBLIC_STRIPE_PERDOC_PRICE_ID=
OPENAI_API_KEY=
RESEND_API_KEY=
NEXT_PUBLIC_APP_URL=http://localhost:3000

Create chamavault/.env.local.example:
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_SMALL_PRICE_ID=
NEXT_PUBLIC_STRIPE_STANDARD_PRICE_ID=
NEXT_PUBLIC_STRIPE_LARGE_PRICE_ID=
OPENAI_API_KEY=
RESEND_API_KEY=
NEXT_PUBLIC_APP_URL=http://localhost:3000

Create solocrm/.env.local.example:
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_PRO_PRICE_ID=
OPENAI_API_KEY=
RESEND_API_KEY=
NEXT_PUBLIC_APP_URL=http://localhost:3000

═══════════════════════════════════════
STEP 4 — CREATE SUPABASE SCHEMAS
═══════════════════════════════════════

Create reviewpilot/supabase/schema.sql:
create extension if not exists "uuid-ossp";
create table profiles (id uuid references auth.users primary key, full_name text, company_name text, subscription_tier text default 'free', stripe_customer_id text, responses_used_this_month int default 0, created_at timestamptz default now());
create table subscriptions (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_subscription_id text unique, plan text, status text, current_period_end timestamptz, created_at timestamptz default now());
create table businesses (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, name text not null, category text, address text, gmb_id text, is_connected boolean default false, avg_rating numeric default 0, total_reviews int default 0, auto_respond boolean default false, response_tone text default 'professional', response_signature text, created_at timestamptz default now());
create table reviews (id uuid default uuid_generate_v4() primary key, business_id uuid references businesses(id) on delete cascade, gmb_review_id text, author_name text, author_photo_url text, rating int, text text, posted_at timestamptz, sentiment text default 'neutral', is_responded boolean default false, created_at timestamptz default now());
create table responses (id uuid default uuid_generate_v4() primary key, review_id uuid references reviews(id) on delete cascade, response_text text not null, tone_used text, ai_generated boolean default true, approved_at timestamptz, posted_at timestamptz, created_by uuid references profiles(id));
alter table profiles enable row level security;
alter table businesses enable row level security;
alter table reviews enable row level security;
alter table responses enable row level security;
create policy "Users own their data" on profiles for all using (auth.uid() = id);
create policy "Users own their data" on businesses for all using (auth.uid() = user_id);
create policy "Users own their reviews" on reviews for all using (auth.uid() = (select user_id from businesses where id = business_id));
create policy "Users own their responses" on responses for all using (auth.uid() = (select user_id from businesses b join reviews r on r.business_id = b.id where r.id = review_id));

Create studiopilot/supabase/schema.sql:
create extension if not exists "uuid-ossp";
create table profiles (id uuid references auth.users primary key, full_name text, subscription_tier text default 'starter', stripe_customer_id text, created_at timestamptz default now());
create table subscriptions (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_subscription_id text unique, plan text, status text, current_period_end timestamptz);
create table locations (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, name text not null, address text, timezone text default 'Africa/Nairobi', phone text, created_at timestamptz default now());
create table staff (id uuid default uuid_generate_v4() primary key, location_id uuid references locations(id) on delete cascade, user_id uuid references profiles(id), full_name text not null, email text, phone text, specialties text[], is_active boolean default true);
create table clients (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, first_name text not null, last_name text, email text, phone text, emergency_contact text, medical_notes text, membership_tier text, is_active boolean default true, join_date date, created_at timestamptz default now());
create table class_types (id uuid default uuid_generate_v4() primary key, location_id uuid references locations(id) on delete cascade, name text not null, description text, duration_minutes int default 60, capacity int default 20, price numeric default 0, currency text default 'KES', color text default '#14b8a6', is_active boolean default true);
create table class_schedule (id uuid default uuid_generate_v4() primary key, class_type_id uuid references class_types(id) on delete cascade, instructor_id uuid references staff(id), location_id uuid references locations(id), start_time time, end_time time, day_of_week int, is_recurring boolean default true);
create table class_instances (id uuid default uuid_generate_v4() primary key, class_schedule_id uuid references class_schedule(id), class_type_id uuid references class_types(id), instructor_id uuid references staff(id), instance_date date not null, start_time time, end_time time, is_cancelled boolean default false, cancellation_reason text);
create table bookings (id uuid default uuid_generate_v4() primary key, client_id uuid references clients(id) on delete cascade, class_instance_id uuid references class_instances(id) on delete cascade, status text default 'booked', booked_at timestamptz default now(), checked_in_at timestamptz, waitlist_position int, unique(client_id, class_instance_id));
create table memberships (id uuid default uuid_generate_v4() primary key, client_id uuid references clients(id) on delete cascade, plan_name text, price numeric, billing_cycle text, start_date date, end_date date, stripe_subscription_id text, status text default 'active');
create table payments (id uuid default uuid_generate_v4() primary key, client_id uuid references clients(id), user_id uuid references profiles(id) on delete cascade, amount numeric not null, currency text default 'KES', method text, description text, paid_at timestamptz default now(), stripe_payment_id text);
alter table profiles enable row level security;
alter table locations enable row level security;
alter table clients enable row level security;
alter table class_types enable row level security;
alter table bookings enable row level security;
alter table payments enable row level security;
create policy "Users own their data" on profiles for all using (auth.uid() = id);
create policy "Users own locations" on locations for all using (auth.uid() = user_id);
create policy "Users own clients" on clients for all using (auth.uid() = user_id);
create policy "Users own class types" on class_types for all using (auth.uid() = (select user_id from locations where id = location_id));
create policy "Users own payments" on payments for all using (auth.uid() = user_id);

Create academiaai/supabase/schema.sql:
create extension if not exists "uuid-ossp";
create table profiles (id uuid references auth.users primary key, full_name text, subscription_tier text default 'free', stripe_customer_id text, docs_used_this_month int default 0, total_words_processed int default 0, created_at timestamptz default now());
create table subscriptions (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_subscription_id text unique, plan text, status text, current_period_end timestamptz);
create table documents (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, title text, original_text text not null, processed_text text, tool_used text, word_count int, processing_level text, ai_detection_before numeric, ai_detection_after numeric, created_at timestamptz default now(), updated_at timestamptz default now());
create table one_time_purchases (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_payment_intent_id text, amount numeric, purchased_at timestamptz default now(), credits_granted int default 1);
alter table profiles enable row level security;
alter table documents enable row level security;
alter table one_time_purchases enable row level security;
create policy "Users own profiles" on profiles for all using (auth.uid() = id);
create policy "Users own documents" on documents for all using (auth.uid() = user_id);
create policy "Users own purchases" on one_time_purchases for all using (auth.uid() = user_id);

Create chamavault/supabase/schema.sql:
create extension if not exists "uuid-ossp";
create table profiles (id uuid references auth.users primary key, full_name text, phone text, subscription_tier text default 'free', stripe_customer_id text, created_at timestamptz default now());
create table subscriptions (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_subscription_id text unique, plan text, status text, current_period_end timestamptz);
create table chamas (id uuid default uuid_generate_v4() primary key, name text not null, photo_url text, founding_date date, objective text, meeting_day text, meeting_frequency text default 'monthly', contribution_amount numeric default 0, currency text default 'KES', bank_name text, account_number text, mpesa_paybill text, is_active boolean default true, created_by uuid references profiles(id), created_at timestamptz default now());
create table chama_members (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, user_id uuid references profiles(id), full_name text not null, phone text, email text, role text default 'member', joined_at timestamptz default now(), share_units numeric default 1, is_active boolean default true);
create table contributions (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, member_id uuid references chama_members(id) on delete cascade, month_year text not null, amount_due numeric default 0, amount_paid numeric default 0, paid_at timestamptz, payment_method text default 'cash', recorded_by uuid references chama_members(id), notes text);
create table fines (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, member_id uuid references chama_members(id) on delete cascade, reason text not null, amount numeric not null, is_paid boolean default false, paid_at timestamptz, issued_at timestamptz default now());
create table loans (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, member_id uuid references chama_members(id) on delete cascade, amount numeric not null, interest_rate numeric default 10, purpose text, disbursed_at date, due_date date, status text default 'pending', approved_by uuid references chama_members(id), total_repaid numeric default 0);
create table loan_repayments (id uuid default uuid_generate_v4() primary key, loan_id uuid references loans(id) on delete cascade, amount numeric not null, paid_at timestamptz default now(), notes text);
create table expenses (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, description text not null, amount numeric not null, category text, expense_date date, receipt_url text, recorded_by uuid references chama_members(id));
create table meetings (id uuid default uuid_generate_v4() primary key, chama_id uuid references chamas(id) on delete cascade, meeting_date date not null, agenda text, venue text, minutes_text text, created_at timestamptz default now());
create table meeting_attendance (id uuid default uuid_generate_v4() primary key, meeting_id uuid references meetings(id) on delete cascade, member_id uuid references chama_members(id) on delete cascade, present boolean default false);
alter table profiles enable row level security;
alter table chamas enable row level security;
alter table chama_members enable row level security;
alter table contributions enable row level security;
alter table loans enable row level security;
alter table expenses enable row level security;
create policy "Users own profiles" on profiles for all using (auth.uid() = id);
create policy "Members can access their chama data" on chamas for all using (id in (select chama_id from chama_members where user_id = auth.uid()));
create policy "Members can see member list" on chama_members for all using (chama_id in (select chama_id from chama_members where user_id = auth.uid()));
create policy "Members see contributions" on contributions for all using (chama_id in (select chama_id from chama_members where user_id = auth.uid()));
create policy "Members see loans" on loans for all using (chama_id in (select chama_id from chama_members where user_id = auth.uid()));
create policy "Members see expenses" on expenses for all using (chama_id in (select chama_id from chama_members where user_id = auth.uid()));

Create solocrm/supabase/schema.sql:
create extension if not exists "uuid-ossp";
create table profiles (id uuid references auth.users primary key, full_name text, company text, subscription_tier text default 'free', stripe_customer_id text, created_at timestamptz default now());
create table subscriptions (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, stripe_subscription_id text unique, plan text, status text, current_period_end timestamptz);
create table contacts (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, first_name text not null, last_name text, email text, phone text, company text, title text, source text, tags text[], notes text, is_opted_out boolean default false, created_at timestamptz default now(), updated_at timestamptz default now());
create table pipelines (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, name text not null, is_default boolean default false);
create table pipeline_stages (id uuid default uuid_generate_v4() primary key, pipeline_id uuid references pipelines(id) on delete cascade, name text not null, order_index int default 0, probability int default 50, color text default '#06b6d4');
create table deals (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, contact_id uuid references contacts(id), pipeline_id uuid references pipelines(id), stage_id uuid references pipeline_stages(id), title text not null, value numeric default 0, currency text default 'USD', close_date date, probability int default 50, notes text, won_at timestamptz, lost_at timestamptz, lost_reason text, created_at timestamptz default now());
create table deal_activities (id uuid default uuid_generate_v4() primary key, deal_id uuid references deals(id) on delete cascade, contact_id uuid references contacts(id), event_type text, description text, created_at timestamptz default now());
create table tasks (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, contact_id uuid references contacts(id), deal_id uuid references deals(id), title text not null, due_date timestamptz, type text default 'follow-up', is_complete boolean default false, completed_at timestamptz, notes text, created_at timestamptz default now());
create table email_sequences (id uuid default uuid_generate_v4() primary key, user_id uuid references profiles(id) on delete cascade, name text not null, is_active boolean default true, created_at timestamptz default now());
create table sequence_steps (id uuid default uuid_generate_v4() primary key, sequence_id uuid references email_sequences(id) on delete cascade, step_number int not null, delay_days int default 0, subject text not null, body text not null);
create table sequence_enrollments (id uuid default uuid_generate_v4() primary key, contact_id uuid references contacts(id) on delete cascade, sequence_id uuid references email_sequences(id) on delete cascade, enrolled_at timestamptz default now(), current_step int default 1, is_active boolean default true, completed_at timestamptz);
create table scheduled_emails (id uuid default uuid_generate_v4() primary key, contact_id uuid references contacts(id) on delete cascade, sequence_id uuid references email_sequences(id), step_id uuid references sequence_steps(id), scheduled_at timestamptz not null, sent_at timestamptz, subject text, body text, opened_at timestamptz);
alter table profiles enable row level security;
alter table contacts enable row level security;
alter table pipelines enable row level security;
alter table deals enable row level security;
alter table tasks enable row level security;
alter table email_sequences enable row level security;
alter table scheduled_emails enable row level security;
create policy "Users own their data" on profiles for all using (auth.uid() = id);
create policy "Users own contacts" on contacts for all using (auth.uid() = user_id);
create policy "Users own pipelines" on pipelines for all using (auth.uid() = user_id);
create policy "Users own deals" on deals for all using (auth.uid() = user_id);
create policy "Users own tasks" on tasks for all using (auth.uid() = user_id);
create policy "Users own sequences" on email_sequences for all using (auth.uid() = user_id);
create policy "Users own scheduled emails" on scheduled_emails for all using (auth.uid() = (select user_id from contacts where id = contact_id));

═══════════════════════════════════════
STEP 5 — GIT INIT + INITIAL COMMIT IN EACH
═══════════════════════════════════════

In each project folder (reviewpilot, studiopilot, academiaai, chamavault, solocrm):
git add -A
git commit -m "🚀 Initial scaffold: [projectname]"

When all 5 are done, output:
✅ reviewpilot/ — Ready
✅ studiopilot/ — Ready
✅ academiaai/ — Ready
✅ chamavault/ — Ready
✅ solocrm/ — Ready
📋 Next: Open each folder in a new CMD window and paste the build prompt.
```

---

## PROMPT 1 — BUILD REVIEWPILOT
*(Open reviewpilot/ in a new CMD → paste this)*

---

```
You are a senior fullstack engineer. Build ReviewPilot — a complete AI Google Review Response SaaS — in this Next.js project. YOLO MODE: build every page, every feature, every API route. No questions. No pausing. Make all decisions.

═══════════════════════════════════════
PRODUCT OVERVIEW
═══════════════════════════════════════
ReviewPilot helps small businesses respond to Google/Yelp reviews using AI. One click turns any review into a polished, human-sounding reply.

Tagline: "Respond to every review in one click. Sound human every time."
Target: Restaurants, salons, clinics, gyms, hotels, any local business with online reviews.

Pricing:
- Free: 50 AI responses/month, 1 location
- Pro ($15/mo): Unlimited responses, 3 locations, sentiment analytics
- Business ($29/mo): Unlimited + 10 locations + white-label + team access + auto-reply toggle

═══════════════════════════════════════
TECH STACK
═══════════════════════════════════════
- Next.js 14 App Router + TypeScript
- Supabase (auth + DB)
- Stripe (subscriptions)
- OpenAI GPT-4o-mini
- Resend (emails)
- shadcn/ui + Tailwind (dark, orange accent #f97316)
- Recharts (analytics)
- Framer Motion + Sonner

═══════════════════════════════════════
ALL PAGES TO BUILD
═══════════════════════════════════════

1. LANDING PAGE (src/app/page.tsx)
   - Navbar: logo, features, pricing, login, "Start Free"
   - Hero: "Respond to Every Review in One Click" — big headline, before/after demo widget showing a real-looking 1-star review being turned into a professional response. Orange CTA button.
   - Social proof: "Trusted by 2,400+ local businesses" + 5 industry type badges (Restaurant, Clinic, Salon, Hotel, Retail)
   - Features section: 6 cards — AI Response Generation, Sentiment Analysis, Multi-Platform (Google/Yelp/TripAdvisor), Auto-Reply Mode, Tone Customization, Weekly Digest Report
   - Problem/Solution: "53% of customers expect a reply within 7 days. Most businesses respond to less than 10% of reviews. ReviewPilot fixes that."
   - Comparison table: ReviewPilot vs Birdeye ($299/mo) vs Podium ($249/mo) vs Grade.us ($110/mo) — you win on price and simplicity
   - Pricing: 3 cards (Free / Pro $15 / Business $29) with Stripe checkout buttons
   - Testimonials: 3 realistic placeholders from restaurant owner, clinic manager, hotel GM
   - FAQ: 6 questions (how does AI response work, which platforms, can I edit before posting, etc.)
   - Footer

2. AUTH (same pattern as PostPilot):
   - src/app/auth/login/page.tsx
   - src/app/auth/signup/page.tsx
   - src/app/auth/reset/page.tsx
   - src/app/auth/callback/route.ts

3. DASHBOARD (src/app/dashboard/page.tsx)
   - Protected layout with sidebar
   - Sidebar: logo, nav links (Dashboard, Reviews, Businesses, Analytics, Settings, Billing), user avatar, plan badge
   - Stats row: Reviews Today (real from DB), Response Rate (responded/total %), Average Rating, Locations Connected
   - Review feed: latest 10 unresponded reviews across all locations, sorted by date, each with star rating, author, snippet, "Generate Response" button
   - Activity feed: recent responses posted
   - Quick action: "Auto-respond to all pending" button (generates + queues responses for all unresponded reviews)

4. REVIEWS PAGE (src/app/dashboard/reviews/page.tsx)
   - Filter tabs: All | Unresponded | Responded | By Rating (1★ 2★ 3★ 4★ 5★) | By Sentiment
   - Review cards: author avatar (initial), star rating (colored stars), review text, date, business tag, sentiment badge (Positive/Neutral/Negative)
   - "Generate Response" button on each unresponded review → opens response panel
   - Response panel (slide-out sheet): shows 3 AI-generated variations with tone labels (Professional / Friendly / Concise), each with copy + "Approve & Post" button
   - Approved response shows below review with green "Responded" badge
   - Search reviews by keyword

5. BUSINESSES (src/app/dashboard/businesses/page.tsx)
   - Grid of location cards: business name, category icon, address, connection status badge, avg rating stars, total reviews count
   - Add business modal: name, category (dropdown: Restaurant/Clinic/Salon/Hotel/Gym/Retail/Other), address, GMB ID (optional for now), auto-respond toggle, response tone preference (Professional/Friendly/Casual)
   - Business detail: full settings, response signature, blacklist words, edit/delete
   - "Import Reviews" button: opens modal — "Paste your Google My Business review data as JSON or CSV" — parses and imports reviews into DB
   - For MVP: manual import. Note "Direct GMB API integration coming soon"

6. ANALYTICS (src/app/dashboard/analytics/page.tsx)
   - Date range picker (7d / 30d / 90d / custom)
   - Line chart: response rate over time (% responded per day)
   - Bar chart: reviews by rating (1★ through 5★ count)
   - Donut chart: sentiment breakdown (positive / neutral / negative %)
   - Table: top performing responses (most positive sentiment follow-up reviews)
   - Insight card: "Your response rate improved 23% this month" (calculated from data)

7. SETTINGS (src/app/dashboard/settings/page.tsx)
   - Tabs: Profile, Response Defaults, Notifications
   - Profile: name, email, company name
   - Response Defaults: default tone (Professional/Friendly/Concise), global signature (e.g. "— The [Name] Team"), max response length (short/medium/long)
   - Blacklisted words: words that should never appear in AI responses
   - Notifications: email digest (daily/weekly/never), alert when 1-star review comes in

8. BILLING (src/app/dashboard/billing/page.tsx)
   - Current plan card, usage (X of 50 free responses used), upgrade CTA
   - Stripe upgrade flow
   - Cancel subscription

═══════════════════════════════════════
KEY FEATURE IMPLEMENTATIONS
═══════════════════════════════════════

AI RESPONSE GENERATOR — src/app/api/ai/respond/route.ts:
Input: { reviewText, rating, businessName, businessCategory, tone, signature, blacklistedWords[] }
System: "You are a professional business owner writing a response to a {rating}-star review for {businessName}, a {businessCategory}. Write a {tone} response that: addresses specific points from the review, thanks the reviewer by name if possible, invites them back (if positive/neutral) or offers resolution (if negative), never sounds AI-generated, uses natural language and varied sentence structure. Keep it under 150 words. Do NOT use: {blacklistedWords}. End with: {signature}. Return JSON only: {variations: [{tone: string, response: string}]} — 3 variations (Professional, Friendly, Concise). No preamble."
Model: gpt-4o-mini

SENTIMENT ANALYSIS — run when reviews are imported/created:
src/app/api/ai/sentiment/route.ts
Simple call: "Rate this review sentiment as positive, neutral, or negative. Return JSON: {sentiment: 'positive'|'neutral'|'negative', score: 0-100}. Review: [text]"
Store in reviews.sentiment

SEED DATA — create src/lib/seed.ts:
Create 2 demo businesses: "Mzuri Restaurant" (Restaurant, Nairobi) and "Clarity Dental Clinic" (Clinic, Nairobi)
Create 25 realistic reviews total, mix of ratings and sentiments, realistic Kenyan/African names as reviewers
This makes the dashboard immediately compelling on first login

STRIPE WEBHOOKS — src/app/api/webhooks/stripe/route.ts:
Handle subscription events, update profiles.subscription_tier
Free: 50 responses/mo, Pro: unlimited, Business: unlimited + 10 locations

AUTH MIDDLEWARE — middleware.ts:
Protect /dashboard/* routes
Redirect to /auth/login if no session

═══════════════════════════════════════
DESIGN SYSTEM
═══════════════════════════════════════
Dark theme only.
Background: #0a0906, Surface: #141210, Border: #2a2520
Primary accent: #f97316 (orange — warmth, trust, local business energy)
Secondary: #eab308 (yellow — star ratings)
Success: #10b981, Danger: #ef4444, Neutral: #6b7280
Font: Geist Sans
Star ratings: filled stars in #eab308, empty in #374151
Sentiment badges: positive=#10b981/bg-emerald-950, neutral=#6b7280/bg-zinc-900, negative=#ef4444/bg-red-950
Review cards: hover lifts slightly (transform translateY(-2px))
Response panel: slides in from right (framer-motion x animation)

Build order: layout → auth → dashboard with seed data → reviews page → response generator → businesses → analytics → billing → landing page.

The review card + AI response panel is the CORE product. Make it beautiful and instant-feeling. The response should appear within 2 seconds of clicking "Generate".
```

---

## PROMPT 2 — BUILD STUDIOPILOT
*(Open studiopilot/ in a new CMD → paste this)*

---

```
You are a senior fullstack engineer. Build StudioPilot — a complete gym/yoga/salon studio management SaaS — in this Next.js project. YOLO MODE: build everything, make all decisions, no questions.

═══════════════════════════════════════
PRODUCT OVERVIEW
═══════════════════════════════════════
StudioPilot replaces Mindbody ($129–$300+/mo, predatory contracts, outdated UX) at $29/mo flat with month-to-month billing. Everything fitness and wellness studios need.

Tagline: "Run your studio. Not your software."
Target: Yoga studios, gyms, dance schools, martial arts, pilates, personal trainers, salons.

Pricing:
- Starter ($29/mo): 1 location, unlimited clients, class scheduling, payments
- Pro ($59/mo): 3 locations + staff management + waitlist + automated reminders
- Studio ($99/mo): Unlimited locations + custom client portal + advanced analytics + API access

═══════════════════════════════════════
TECH STACK
═══════════════════════════════════════
- Next.js 14 App Router + TypeScript
- Supabase (auth + DB)
- Stripe (subscriptions + membership payments)
- OpenAI GPT-4o-mini (class description generator)
- Resend (booking confirmations, reminders)
- shadcn/ui + Tailwind (dark, teal accent #14b8a6)
- Recharts (revenue charts)
- date-fns + date-fns-tz (timezone-aware scheduling)
- Framer Motion + Sonner

═══════════════════════════════════════
ALL PAGES TO BUILD
═══════════════════════════════════════

1. LANDING PAGE (src/app/page.tsx)
   - Navbar: logo, features, pricing, login, "Try Free 30 Days"
   - Hero: "Run Your Studio. Not Your Software." — clean headline, show a scheduling calendar mockup, teal CTA
   - Pain point section: "Mindbody charges $200/month AND locks you into annual contracts. StudioPilot: $29/month. Cancel anytime. No lock-in."
   - Feature grid: 8 features (Class Scheduling, Client Profiles, Payments, Waitlists, Staff Management, Automated Reminders, Revenue Reports, Client Portal)
   - For who: tabs switching between Yoga Studio / Gym / Dance School / Salon — each shows a slightly different feature highlight
   - Comparison: StudioPilot vs Mindbody vs Acuity vs Pike13 (price + features table)
   - Pricing: 3 cards (Starter $29 / Pro $59 / Studio $99) with Stripe checkout
   - Testimonials: 3 from yoga studio owner, gym manager, dance instructor
   - FAQ: 7 questions (can I import from Mindbody, does it work for multiple locations, etc.)
   - Footer

2. AUTH: login, signup, reset, callback (standard pattern)

3. DASHBOARD (src/app/dashboard/page.tsx)
   - Sidebar layout: logo, nav links (Dashboard, Schedule, Clients, Staff, Payments, Reports, Settings, Billing)
   - Today's view: classes happening today as a timeline (8am Yoga with 12/15 spots, 10am HIIT with 8/20 spots), quick check-in buttons
   - Stats cards: Active Members, Classes Today, Revenue This Week, New Clients This Month
   - Upcoming schedule (next 7 days): mini calendar view with classes as colored chips
   - Retention alert: "3 clients haven't visited in 30+ days" with their names and "Send reminder" buttons
   - Quick action: "Create Class", "Add Client", "Record Payment"

4. SCHEDULE (src/app/dashboard/schedule/page.tsx)
   - Week view by default (Mon–Sun columns), with time slots as rows (6am–10pm)
   - Classes appear as colored blocks per their class_type color
   - Click class block → class detail drawer (who's booked, check-in, waitlist, cancel)
   - "Add Class" button → modal with class type selector, instructor, date/time, repeat toggle
   - Filters: by location, by instructor, by class type
   - Month view toggle: shows classes as chips on calendar grid

5. CLASS TYPES (src/app/dashboard/classes/page.tsx)
   - Grid of class type cards: color swatch, name, duration, capacity, price, active/inactive toggle
   - Add/edit class type: name, description, duration (15/30/45/60/90min/custom), capacity, price, color, category
   - "Generate Description with AI" button: type class name → AI writes a compelling class description

6. CLIENTS (src/app/dashboard/clients/page.tsx)
   - Searchable table: name, email, phone, membership, last visit, total visits, status badge (Active/Inactive/New)
   - Tags: VIP, At Risk (30+ days no visit), New (joined last 30 days)
   - Add/edit client: full form with all fields including emergency contact and medical notes
   - Client detail page: profile header with visit stats, membership info, booking history, payment history, notes timeline
   - "Book Client into Class" button on client detail
   - Export clients to CSV

7. CLASS DETAIL / CHECK-IN (src/app/dashboard/schedule/[instanceId]/page.tsx)
   - Class info header: name, date/time, instructor, location, capacity used (12/20)
   - Attendees list: each row has client name, membership status, check-in toggle, remove button
   - Waitlist section: clients waiting, promote to spot button when cancellation happens
   - Cancel class button: confirms, sends email to all booked clients

8. STAFF (src/app/dashboard/staff/page.tsx)
   - Staff cards: photo/initials, name, specialties, classes this week count, status toggle
   - Add/edit staff: name, email, phone, specialties (multi-select), bio
   - Staff schedule: which classes they're assigned to this week
   - Hours log: record worked hours per staff member

9. PAYMENTS (src/app/dashboard/payments/page.tsx)
   - Revenue overview: this month vs last month, chart
   - Transactions table: date, client, amount, method, description
   - Record payment modal: client selector, amount, currency (KES default), method (Cash/M-Pesa/Card/Bank), description
   - Memberships tab: all active memberships, renewal dates, monthly MRR total
   - Outstanding: clients with unpaid balances, one-click reminder send

10. REPORTS (src/app/dashboard/reports/page.tsx)
    - Revenue by month (bar chart, recharts)
    - Most popular classes (bar chart by total bookings)
    - Client retention rate over time (line chart)
    - Peak hours heatmap: 7x24 grid showing booking density per day/hour
    - Export as PDF button (generate simple PDF with recharts chart as image)

11. CLIENT PORTAL (src/app/portal/[studioSlug]/page.tsx) — public, no auth
    - Studio header: name, logo, location
    - Class schedule for next 7 days: cards per class with time, instructor, spots left
    - "Book" button per class → simple booking form (name, email, phone) → confirms booking
    - For paid classes: Stripe checkout before confirming
    - "View my bookings" tab: client enters their email → sees their upcoming bookings + cancel option

12. SETTINGS (src/app/dashboard/settings/page.tsx)
    - Tabs: Studio Info, Notifications, Booking Rules
    - Studio Info: name, logo, address, timezone, currency, portal slug
    - Notifications: reminder emails (24hr before class, 1hr before), booking confirmation template
    - Booking Rules: cancellation window (24hr/48hr/no cancellation), waitlist enabled toggle, max future bookings per client

13. BILLING (src/app/dashboard/billing/page.tsx)
    - Current plan, usage stats (locations, clients count), upgrade/downgrade, Stripe portal link

═══════════════════════════════════════
KEY FEATURE IMPLEMENTATIONS
═══════════════════════════════════════

BOOKING ENGINE:
src/app/api/bookings/route.ts (POST):
- Check capacity: SELECT count(*) FROM bookings WHERE class_instance_id = ? AND status='booked' < class_type.capacity
- If full and waitlist enabled: add to waitlist with position
- If available: insert booking, send confirmation email
- Concurrency: use Supabase transaction to prevent overbooking race condition

CLASS REMINDER CRON (simulate with Supabase Edge Function comment):
- 24 hours before each class: query class_instances WHERE instance_date = tomorrow, send reminder to all booked clients
- Document how to set up: Supabase Edge Functions + pg_cron, or Vercel cron job

AI CLASS DESCRIPTION — src/app/api/ai/class-description/route.ts:
Input: { className, duration, level, studioType }
Prompt: "Write an engaging 2-3 sentence class description for a {duration}-minute {className} class, {level} level, at a {studioType}. Make it sound exciting and welcoming. No preamble."
Model: gpt-4o-mini

SEED DATA:
- 1 location: "Amani Wellness Studio" (Nairobi, timezone Africa/Nairobi)
- 3 class types: Morning Yoga (60min, KES 800, teal), Power HIIT (45min, KES 1000, orange), Pilates Flow (60min, KES 900, purple)
- 3 staff: Aisha, James, Wanjiku
- 15 clients with realistic names, 2 weeks of class schedule, existing bookings

═══════════════════════════════════════
DESIGN SYSTEM
═══════════════════════════════════════
Dark theme. Background: #09100f, Surface: #111a19, Border: #1a2e2b
Accent: teal #14b8a6, Secondary: purple #a855f7
Status: active=#10b981, inactive=#6b7280, waitlist=#f59e0b
Class colors: teal, orange, purple, blue, pink, red (stored per class_type)
Font: Geist Sans
Schedule blocks: colored left border + class name, instructor initials avatar, capacity fraction
Client status: green dot (active), yellow (at risk), gray (inactive)
Kenyan context: currency defaults to KES, use Nairobi timezone by default

Build order: layout → auth → dashboard with today's classes → schedule view → class types → clients → check-in → payments → client portal → landing.

The schedule view and client check-in are the CORE daily-use features. Make them feel fast and effortless — a studio owner will look at these 20 times a day.
```

---

## PROMPT 3 — BUILD ACADEMIAAI
*(Open academiaai/ in a new CMD → paste this)*

---

```
You are a senior fullstack engineer. Build AcademiaAI — a complete AI academic writing tool SaaS — in this Next.js project. YOLO MODE. Build everything. No questions.

═══════════════════════════════════════
PRODUCT OVERVIEW
═══════════════════════════════════════
AcademiaAI gives students and researchers 4 AI tools: humanize AI text, enhance academic writing, scan plagiarism risk, and generate citations. The owner already has this pipeline — we're packaging it as a SaaS.

Tagline: "Your work. Just better."
Target: University students, researchers, academic writers, ESL students globally.

Pricing:
- Free: 3 documents/month, Humanizer only, basic mode
- Pro ($19/mo): Unlimited documents, all 4 tools, all enhancement levels, saved library
- Pay-per-doc ($5): Single document credit, no subscription needed (Stripe Payment Link)

═══════════════════════════════════════
TECH STACK
═══════════════════════════════════════
- Next.js 14 App Router + TypeScript
- Supabase (auth + DB + storage)
- Stripe (subscriptions + one-time payments)
- OpenAI GPT-4o (not mini — quality is the product here)
- Resend (emails)
- shadcn/ui + Tailwind (dark, indigo accent #6366f1)
- diff library (show what changed between original and processed)
- Framer Motion + Sonner + Slider (shadcn)

═══════════════════════════════════════
ALL PAGES TO BUILD
═══════════════════════════════════════

1. LANDING PAGE (src/app/page.tsx)
   - Navbar: logo, "Tools", Pricing, Login, "Try Free"
   - Hero: "Your Work. Just Better." Large headline. Subtitle: "Humanize AI text, elevate academic tone, and reduce plagiarism risk — all in one place." Email capture + "Get Started Free" button.
   - LIVE DEMO WIDGET (most important landing page element):
     * A textarea pre-filled with obviously AI-generated text (robotic, repetitive)
     * A "Humanize" button
     * Below it: the result appears, showing the transformed text with a subtle diff highlight of changed phrases
     * This is static/mocked HTML animation — not a real API call on the landing page
   - 4 Tool cards with icons: Humanizer, Academic Enhancer, Plagiarism Risk Scanner, Citation Generator
   - How it works: 3 steps (Paste your text → Choose your tool → Get instant results)
   - Trust signals: "Used by students at 50+ universities", lock icon "Your text is never stored after processing" (privacy message)
   - Comparison: AcademiaAI vs Grammarly vs QuillBot vs Undetectable.ai (features + price)
   - Pricing: 3 cards (Free / Pro $19/mo / Pay-per-doc $5) — emphasize pay-per-doc option for people who don't want subscriptions
   - Student testimonials: 3 realistic quotes
   - FAQ: 8 questions (is it detectable, which detectors does it beat, is my text stored, can I use it for dissertation, etc.)
   - Footer with privacy policy mention

2. AUTH: login, signup, reset, callback (standard)

3. DASHBOARD (src/app/dashboard/page.tsx)
   - Clean tool launcher layout (not a typical dashboard — more like a home screen)
   - Sidebar: logo, tool links (Humanize, Enhance, Plagiarism, Citations, My Documents), account
   - Usage card: "X of 3 free documents used this month" with progress bar — if Pro, shows "Unlimited"
   - 4 large tool cards with color icons, name, one-line description, "Open Tool" button
   - Recent documents section: last 5 processed docs with tool used, word count, date, "Open" link
   - Tip of the day: rotating academic writing tip
   - Pro upsell banner (for free users): "Need more? Go Pro for unlimited + all tools"

4. TOOL 1 — HUMANIZER (src/app/dashboard/humanize/page.tsx)
   - Left panel (input): large textarea "Paste your AI-generated text here", word count live counter, detect input language badge
   - Right panel (output): shows processed result, word count
   - Humanization level: segmented control — Subtle (light touch) | Balanced (recommended) | Aggressive (complete restyle)
   - "Humanize" button with loading spinner
   - Output features: side-by-side diff view (highlight changed words/phrases in subtle indigo), copy button, word count comparison
   - AI Detection Estimate: two badges — "Before: ~87% AI detected" and "After: ~12% AI detected" (calculated using a simple heuristic scoring function, not a real detector API — be honest it's an estimate)
   - Save to documents button
   - "Try another level" quick button if user wants to re-run with different setting

5. TOOL 2 — ACADEMIC ENHANCER (src/app/dashboard/enhance/page.tsx)
   - Input textarea: paste text
   - Academic level selector: 4 cards — High School | Undergraduate | Masters | PhD — each with a brief description of what changes
   - Discipline selector (optional): dropdown — Sciences | Humanities | Business | Law | Medicine | General
   - "Enhance Writing" button
   - Output: enhanced text in right panel, split-view diff showing vocabulary upgrades highlighted
   - Vocabulary upgrade count: "24 words upgraded to academic equivalents"
   - Save to documents

6. TOOL 3 — PLAGIARISM RISK SCANNER (src/app/dashboard/plagiarism/page.tsx)
   - Input textarea: paste text
   - "Scan Risk" button
   - Output:
     * Risk score: large circular progress gauge (0–100, green < 30, yellow 30–60, red > 60)
     * Flagged passages: the input text re-rendered with flagged sentences highlighted in orange/red
     * Each highlighted sentence has a "Why flagged" tooltip
     * Suggested rewrites: accordion list of flagged sentences with AI-generated rewrite suggestion
     * Disclaimer: "This is an AI-based risk estimation. Always verify with your institution's plagiarism checker."
   - Save scan result to documents

7. TOOL 4 — CITATION GENERATOR (src/app/dashboard/citations/page.tsx)
   - Input method tabs: URL | DOI | Book Title | Manual Entry
   - URL input: paste URL → AI extracts title, author, date, publication from the page
   - DOI input: enter DOI → fetch metadata
   - Book: enter title and author → AI finds publication details
   - Manual: form fields (author, title, year, publisher, etc.)
   - Format selector: APA | MLA | Chicago | Harvard | Vancouver
   - "Generate Citation" button
   - Output: formatted citation in large text, copy button
   - Citation history: last 20 generated citations in this session (in-memory, no DB needed)
   - "Export all as .txt" button

8. MY DOCUMENTS (src/app/dashboard/documents/page.tsx)
   - Table: title (auto-generated from first 50 chars), tool used, word count, date, actions
   - Search/filter by tool type
   - Click row → Document detail: shows original text vs processed text side-by-side
   - Delete document
   - Re-process: send document back to any tool

9. SETTINGS (src/app/dashboard/settings/page.tsx)
   - Profile: name, email
   - Privacy: "Delete all my documents" button (wipes documents table for user)
   - Notifications: email when monthly free credits reset

10. BILLING (src/app/dashboard/billing/page.tsx)
    - Current plan, docs used this month
    - Pay-per-doc: "Buy a single document credit for $5" → Stripe Payment Link
    - Pro upgrade: Stripe checkout
    - For Pro users: "Manage subscription" Stripe portal link

═══════════════════════════════════════
KEY FEATURE IMPLEMENTATIONS
═══════════════════════════════════════

HUMANIZER — src/app/api/tools/humanize/route.ts:
Subtle: "Lightly rewrite this text so it reads as naturally human-written. Make small vocabulary swaps, vary sentence rhythm slightly, remove the most obvious AI patterns (overuse of 'Furthermore', 'In conclusion', 'It is worth noting'). Preserve all meaning. Return only the rewritten text, nothing else."
Balanced: "Rewrite this text to sound naturally human-written by an educated person. Vary sentence length and structure, use more conversational transitions, replace corporate/AI vocabulary with natural alternatives, add minor imperfections in formality. Preserve all content and arguments. Return only the rewritten text."
Aggressive: "Completely rephrase this text so it reads as authentic human writing. Restructure paragraphs, change sentence patterns significantly, use varied vocabulary including colloquial phrases where appropriate, sound like a real person wrote this. Keep all facts and arguments intact. Return only the rewritten text."
Model: gpt-4o

ACADEMIC ENHANCER — src/app/api/tools/enhance/route.ts:
Prompt: "Rewrite this text to match {level} level academic writing standards in the {discipline} field. Upgrade vocabulary to academic equivalents, improve sentence structure and argument clarity, use appropriate hedging language, ensure formal register. Preserve all original meaning and arguments. Return only the enhanced text."
Model: gpt-4o

PLAGIARISM RISK — src/app/api/tools/plagiarism/route.ts:
Prompt: "Analyze this academic text for plagiarism risk. Identify phrases that appear generic, overused, or likely to match common sources. Return JSON only: {riskScore: 0-100, explanation: string, flaggedPassages: [{text: string, reason: string, riskLevel: 'low'|'medium'|'high', suggestedRewrite: string}]}. Be specific about why each passage is flagged."
Model: gpt-4o

DIFF VIEW (in React components):
import { diffWords } from 'diff'
const changes = diffWords(original, processed)
Render: unchanged text in default color, added text with indigo bg, removed text with strikethrough and red color

USAGE GATING — src/lib/gate.ts:
checkDocumentAccess(userId): 
  - Get profiles.docs_used_this_month + profiles.subscription_tier
  - Free: max 3/month. Pro: unlimited.
  - Check one_time_purchases for any unused credits
  - Returns: {allowed: boolean, reason?: string, remaining?: number}
  
incrementDocUsage(userId): UPDATE profiles SET docs_used_this_month = docs_used_this_month + 1

MONTHLY RESET: At start of each new month, docs_used_this_month should reset to 0
  - Implement as: check if current month differs from profiles.last_reset_month → reset if so

STRIPE PAYMENT — Pay-per-doc:
  - Create a Stripe Payment Link in dashboard for $5
  - Webhook: on payment_intent.succeeded → insert into one_time_purchases → user gets 1 credit
  - checkDocumentAccess should check one_time_purchases before rejecting free user

═══════════════════════════════════════
DESIGN SYSTEM
═══════════════════════════════════════
Dark theme. Academic, trustworthy aesthetic.
Background: #09090f, Surface: #111118, Border: #1e1e2e
Accent: indigo #6366f1, Secondary: violet #8b5cf6
Success: #10b981, Warning: #f59e0b, Danger: #ef4444
Font: Geist Sans (body), Geist Mono (for processed text output — makes it feel like terminal output)
Tool cards: each has a distinct color (Humanizer: indigo, Enhancer: violet, Plagiarism: amber, Citations: teal)
Diff highlights: added text = indigo/10 bg with indigo text, removed = red/10 bg strikethrough
Progress ring on plagiarism score: SVG circle, animated fill

Build order: layout → auth → tool pages (they ARE the product) → documents library → landing → billing.

The 4 tool pages are the ENTIRE product. Make them fast, clean, and satisfying to use. Processing should show a skeleton/shimmer while loading, then reveal the result with a subtle fade-in animation. The diff view should make users feel like they can clearly see the AI "fingerprints" being removed.
```

---

## PROMPT 4 — BUILD CHAMAVAULT
*(Open chamavault/ in a new CMD → paste this)*

---

```
You are a senior fullstack engineer. Build ChamaVault — a complete digital chama (group savings) management SaaS for Kenya — in this Next.js project. YOLO MODE. Build everything. No questions.

═══════════════════════════════════════
PRODUCT OVERVIEW
═══════════════════════════════════════
ChamaVault digitizes Kenya's 1M+ investment/savings groups (chamas) that currently run on WhatsApp messages, Excel spreadsheets, and handwritten notebooks. Mobile-first, Swahili-friendly, M-Pesa native.

Tagline: "Simamia Chama Yako Vizuri." (Manage Your Chama Well.)
Target: Chama chairpersons, treasurers, secretaries. Any group savings scheme in Kenya and East Africa.

Pricing:
- Free: 1 chama, up to 5 members, basic tracking only
- Small (KES 500/mo): 1 chama, up to 10 members, full features
- Standard (KES 1,000/mo): 3 chamas, up to 30 members, PDF statements, meeting minutes
- Large (KES 2,000/mo): Unlimited chamas, unlimited members, full feature set

═══════════════════════════════════════
TECH STACK
═══════════════════════════════════════
- Next.js 14 App Router + TypeScript
- Supabase (auth + DB + storage)
- Stripe (for international payments) + M-Pesa Daraja API (document, build with mock if no sandbox)
- OpenAI GPT-4o-mini (meeting minutes assistant)
- Resend (email notifications)
- @react-pdf/renderer (member statements, meeting minutes PDF)
- shadcn/ui + Tailwind (dark, gold/amber accent #f59e0b)
- Recharts (savings growth charts)
- Framer Motion + Sonner
- papaparse (CSV import for bulk member add)

═══════════════════════════════════════
ALL PAGES TO BUILD
═══════════════════════════════════════

1. LANDING PAGE (src/app/page.tsx)
   - Navbar: ChamaVault logo, Features, Pricing, Login, "Anza Bure" (Start Free)
   - Hero section: TWO language versions side by side or tabbed (English/Kiswahili)
     English: "Manage Your Chama. No More Spreadsheets."
     Kiswahili: "Simamia Chama Yako Vizuri. Acha Kutumia Excel."
   - Gold CTA button. Background with subtle kanga-inspired geometric pattern in CSS (not image)
   - Social proof: "Trusted by 500+ chamas in Kenya, Uganda, Tanzania"
   - Feature list: 8 features with icons (Contributions tracker, Loan management, Meeting minutes, Member statements PDF, WhatsApp reminders, Fines, Dividends, Investment tracking)
   - "How it works" for a treasurer: 3 steps (Create chama → Add members → Record contributions every month)
   - Pricing in KES: 4 cards (Free / KES 500 / KES 1,000 / KES 2,000)
   - Testimonials: 3 in mix of English and Kiswahili, from real-sounding Kenyan names
   - FAQ: 8 questions (does it work with M-Pesa, can members log in too, is data safe, etc.)
   - Footer: English + Kiswahili mix

2. AUTH: login, signup, reset, callback

3. CHAMA SELECTOR (src/app/dashboard/page.tsx)
   - If user belongs to multiple chamas: show a card grid — click to enter that chama's dashboard
   - If user belongs to 1 chama: go directly to that chama's dashboard
   - "Create New Chama" card button
   - Create chama modal: name, meeting day (Mon–Sun), frequency (weekly/bi-weekly/monthly), contribution amount (KES), objective

4. CHAMA DASHBOARD (src/app/dashboard/[chamaId]/page.tsx)
   - Chama header: name, photo/logo, founding date badge, member count, your role badge (Chairperson / Treasurer / Secretary / Member)
   - Treasury balance card: large KES amount, calculated as (total contributions + loan interest paid - loans disbursed - expenses)
   - Stats: This month's collection %, Outstanding contributions (KES), Active loans, Meetings this quarter
   - Contribution status grid: mini table showing each member and whether they've paid this month (green = paid, red = overdue, gray = not yet due)
   - Quick actions: Record Contribution, Record Expense, View Loans, Schedule Meeting
   - Activity feed: last 10 transactions/events

5. CONTRIBUTIONS (src/app/dashboard/[chamaId]/contributions/page.tsx)
   - Matrix grid view (most important UI): rows = members, columns = months (last 12 months)
   - Each cell: green checkmark (paid), red X (unpaid/overdue), gray dot (future)
   - Click cell → record payment modal: confirm member, month, amount, payment method (Cash/M-Pesa/Bank), notes
   - Summary row at bottom: total collected per month, % collection rate
   - Monthly total card: this month KES X collected of KES Y expected (X% rate)
   - Export to PDF: generates a clean table for printing at meetings
   - WhatsApp reminder button: opens wa.me with pre-filled message "Ndugu [name], nakukumbusha mchango wa [month]. KES [amount]. Tafadhali lipa haraka."

6. LOANS (src/app/dashboard/[chamaId]/loans/page.tsx)
   - Tabs: Active Loans | Applications | Repayments | History
   - Active loans table: member name, amount, disbursed date, due date, interest rate, total repaid, outstanding balance, status badge
   - New loan application: member selector, amount (must be ≤ some limit based on their contributions), purpose, disbursement date, due date, interest rate (default 10%)
   - Approve/Reject buttons for pending applications
   - Record repayment: loan selector, amount, date, payment method
   - Loan balance calculation: principal + accrued interest - total repaid = outstanding

7. FINES (src/app/dashboard/[chamaId]/fines/page.tsx)
   - Fines table: member, reason, amount, issued date, status (paid/unpaid)
   - Add fine: member selector, reason (dropdown: Missed Meeting/Late Contribution/Late Loan Payment/Other), amount, notes
   - Mark paid: button on each unpaid fine
   - Total outstanding fines shown in header

8. EXPENSES (src/app/dashboard/[chamaId]/expenses/page.tsx)
   - Table: date, description, category, amount (KES), recorded by, receipt thumbnail
   - Add expense: description, amount, category (Venue/Food & Drinks/Admin/Transport/Other), date, receipt upload (Supabase storage)
   - Total expenses this month / year
   - Net treasury = contributions - loans disbursed - expenses (running total)

9. MEETINGS (src/app/dashboard/[chamaId]/meetings/page.tsx)
   - List of past and upcoming meetings
   - Create meeting: date, agenda (textarea), venue
   - Meeting detail: agenda, attendance list (check off members), minutes text editor
   - "Generate Minutes with AI" button: takes attendance data + agenda → AI generates draft formal minutes → editable
   - Export minutes as PDF (react-pdf)
   - Meeting history with attendance rate per member

10. MEMBERS (src/app/dashboard/[chamaId]/members/page.tsx)
    - Member cards: photo/initials, name, role badge, phone, join date, contribution score (% paid on time)
    - Add member: name, phone (required), email, role
    - Bulk add via CSV: upload CSV → papaparse → map columns → import
    - Edit member: change role, phone, email
    - Member statement: per member, generates PDF showing all their contributions, loans, fines for a year
    - Invite member: sends SMS/email invitation link to join the chama portal

11. MEMBER PORTAL (src/app/portal/[chamaId]/page.tsx) — no auth for now
    - Member enters their phone number → sees their personal summary
    - Personal contribution history (which months paid/unpaid)
    - Outstanding loans and repayment schedule
    - Upcoming meeting details
    - This creates the "wow" moment: members can check their status without calling the treasurer

12. FINANCIALS / REPORTS (src/app/dashboard/[chamaId]/reports/page.tsx)
    - Annual summary: total collected, total loans, total expenses, net treasury growth
    - Member contribution compliance ranking (who pays most consistently)
    - Line chart: treasury balance growth over 12 months
    - Dividend calculator: year-end, distribute treasury profit → each member's share based on contribution units
    - "Generate Annual Report" → PDF with all charts and tables (react-pdf)

13. SETTINGS (src/app/dashboard/[chamaId]/settings/page.tsx)
    - Chama info: name, photo upload, objective, meeting schedule
    - Contribution rules: default amount, grace period (days), late fine amount
    - Loan rules: max loan amount (as multiplier of contributions), interest rate, max term
    - Notifications: monthly reminder day, WhatsApp/email toggle

14. BILLING (src/app/dashboard/billing/page.tsx)
    - Current plan (shows in KES), upgrade options, Stripe checkout

═══════════════════════════════════════
KEY FEATURE IMPLEMENTATIONS
═══════════════════════════════════════

TREASURY BALANCE CALCULATION — src/lib/treasury.ts:
getTreasuryBalance(chamaId): 
  totalContributions = SUM(contributions.amount_paid)
  totalLoansDisbursed = SUM(loans.amount WHERE status != 'rejected')
  totalLoanRepayments = SUM(loan_repayments.amount)
  totalInterestEarned = totalLoanRepayments - totalLoansDisbursed (simplified)
  totalExpenses = SUM(expenses.amount)
  balance = totalContributions + totalInterestEarned - totalExpenses - (totalLoansDisbursed - totalLoanRepayments)

WHATSAPP REMINDERS — src/lib/whatsapp.ts:
generateReminderLink(member, chama, month): 
  message = `Ndugu ${member.full_name}, tunakukumbusha mchango wako wa ${chama.name} kwa mwezi wa ${month}. Kiasi: KES ${chama.contribution_amount}. Tafadhali lipa mapema. Asante.`
  return `https://wa.me/254${member.phone.replace(/^0/, '')}?text=${encodeURIComponent(message)}`

AI MEETING MINUTES — src/app/api/ai/minutes/route.ts:
Input: { agenda, attendees, absentees, chamaName, date, discussionPoints }
Prompt: "Generate formal meeting minutes for {chamaName} meeting on {date}. Format as proper meeting minutes with: Header (name, date, venue, chair), Members Present (list), Apologies (absent list), Agenda items with brief discussion notes, Any Other Business, Next Meeting date, Signed fields. Keep it professional and concise. Discussion points for each agenda item: {discussionPoints}"

M-PESA INTEGRATION (document even if not live):
Create src/lib/mpesa.ts with full Daraja API implementation:
- STK Push: initiateStkPush(phoneNumber, amount, accountReference, transactionDesc)
- Callback handler: /api/payments/mpesa/callback
- If MPESA_CONSUMER_KEY not in env: use mock responses and log a console warning
- Document in README: how to get Safaricom sandbox credentials

CONTRIBUTION MATRIX (most complex UI):
- Get all members for a chama
- Get all contribution records for last 12 months
- Build a 2D map: memberMap[memberId][monthYear] = contribution record
- Render as a CSS grid table
- Each cell: click to open record/edit modal

PDF GENERATION (server-only):
Member statement: /api/statements/[memberId]/route.ts
- Use @react-pdf/renderer on the server
- Include: member name, chama name, contribution history table, loan history, fines
- Return as PDF download

SEED DATA:
1 chama "Wema Savings Group" (8 members, meeting every 1st Saturday, KES 2,000/mo contribution)
8 members with Kenyan names (mix of Kikuyu, Luo, Kamba, Luhya, Swahili names)
6 months of contribution history (some paid, some with arrears)
2 active loans
3 past expenses
2 past meetings with minutes

CURRENCY:
All amounts in KES. Format: new Intl.NumberFormat('en-KE', {style: 'currency', currency: 'KES'}).format(amount)
Never show raw numbers without KES prefix.

═══════════════════════════════════════
DESIGN SYSTEM
═══════════════════════════════════════
Dark theme. Warm, trustworthy, African aesthetic.
Background: #0a0900, Surface: #14120a, Border: #2a2510
Accent: gold/amber #f59e0b, Secondary: orange #f97316
Font: Use "Nunito" (Google Fonts — friendly, rounded, approachable). Import via next/font/google.
Contribution matrix: green cells (#10b981 bg with white checkmark), red cells (#ef4444 bg/10 with X), gray (neutral)
Treasury balance: displayed in a prominent card with a golden gradient background
Swahili strings: key UI labels should appear in both English and Kiswahili (e.g. "Mchango / Contribution", "Mkopo / Loan")
Background: subtle CSS geometric pattern inspired by kanga fabric (repeating diamond/triangle pattern using CSS gradients)
Mobile-first: this app is primarily used on phones. All tables must have horizontal scroll or card layout at 375px.

Build order: auth → chama selector → dashboard → contributions matrix (MOST IMPORTANT UI) → loans → members → meetings → reports → member portal → landing.

The contribution matrix is what every treasurer will use every month. Make it beautiful, fast to read, and effortless to update. A treasurer should be able to record a month's contributions for 8 members in under 2 minutes.
```

---

## PROMPT 5 — BUILD SOLOCRM
*(Open solocrm/ in a new CMD → paste this)*

---

```
You are a senior fullstack engineer. Build SoloCRM — a dead-simple, fully-featured CRM for solopreneurs at $10/month flat — in this Next.js project. YOLO MODE. Build everything. No questions.

═══════════════════════════════════════
PRODUCT OVERVIEW
═══════════════════════════════════════
SoloCRM kills HubSpot's bait-and-switch pricing model. HubSpot starts free then demands $800/mo to unlock real features. SoloCRM is $10/mo, nothing ever gated, no upsells, no surprise limits. Everything a solo founder needs to manage their pipeline.

Tagline: "Every lead. Every deal. No BS pricing."
Target: Solopreneurs, freelancers, consultants, indie hackers, small agency owners, anyone who tracks sales without a team.

Pricing:
- Free: 250 contacts, 1 pipeline, no AI, no email sequences
- Pro ($10/mo): Unlimited everything, AI assistant, email sequences, bulk import, full analytics

═══════════════════════════════════════
TECH STACK
═══════════════════════════════════════
- Next.js 14 App Router + TypeScript
- Supabase (auth + DB)
- Stripe (subscriptions)
- OpenAI GPT-4o-mini (AI email writer, deal summary)
- Resend (sequence emails)
- shadcn/ui + Tailwind (dark, cyan accent #06b6d4)
- @dnd-kit/core + @dnd-kit/sortable (Kanban drag-and-drop)
- @tanstack/react-table (contacts table, sortable/filterable)
- papaparse (CSV import)
- Recharts (revenue forecast chart)
- Framer Motion + Sonner

═══════════════════════════════════════
ALL PAGES TO BUILD
═══════════════════════════════════════

1. LANDING PAGE (src/app/page.tsx)
   - Navbar: SoloCRM logo, Features, Pricing, Login, "Start Free — No Card"
   - Hero: "Every Lead. Every Deal. No BS Pricing." Big headline. Subtitle: "HubSpot starts free, then charges $800/mo. SoloCRM is $10/mo. Forever. Nothing gated. No surprises."
   - Show a kanban board screenshot mockup in the hero
   - Feature highlights: 6 features (Contacts, Kanban Pipeline, Task Manager, Email Sequences, AI Assistant, Analytics)
   - "HubSpot trap" explainer section: visual showing HubSpot free → features locked → $800/mo. Then: SoloCRM $10/mo, everything unlocked.
   - Comparison table: SoloCRM vs HubSpot vs Pipedrive vs Monday CRM (SoloCRM wins on price+simplicity)
   - Pricing: 2 cards only (Free / Pro $10) — keep it extremely simple
   - Testimonials: 3 from indie hackers / consultants / freelancers
   - FAQ: 6 questions (can I import from HubSpot, is there a contract, how many pipelines, etc.)
   - Footer

2. AUTH: login, signup, reset, callback (standard)

3. DASHBOARD (src/app/dashboard/page.tsx)
   - Sidebar: logo, nav links (Dashboard, Contacts, Pipeline, Tasks, Sequences, Analytics, Settings, Billing)
   - Stats: Open Deals (count + total value), Deals Won This Month (count + value), Overdue Tasks, Contacts Added This Week
   - Revenue Forecast: recharts bar chart showing (sum of deal values × probability) per month for next 6 months
   - Pipeline health: small kanban preview showing count and value per stage
   - Tasks due today and tomorrow: list with contact name, task type, contact link
   - Recent activity feed: deal moved, contact added, task completed (last 10 events)

4. CONTACTS (src/app/dashboard/contacts/page.tsx)
   - @tanstack/react-table powered table (virtual scrolling for large lists)
   - Columns: select checkbox, name, company, email, phone, source, tags, created date, actions
   - Sortable columns, resizable (optional)
   - Filter bar: search by name/email/company, filter by tag (multi-select), filter by source
   - Row click → opens contact detail sidebar (not new page — sidebar overlay)
   - Bulk actions: delete selected, add tag to selected, add to sequence
   - "Add Contact" button → modal form
   - "Import CSV" button → upload → papaparse → column mapping UI → import with progress bar
   - Export CSV button

5. CONTACT DETAIL SIDEBAR (component):
   - Slides in from right (framer-motion)
   - Header: name, company, email, phone, tags, edit button
   - Tabs within sidebar: Overview | Deals | Tasks | Emails | Notes
   - Overview: source, created date, all contact details
   - Deals: list of deals linked to this contact, total value
   - Tasks: upcoming tasks for this contact, add task button
   - Emails: emails sent via sequences, with sent dates and open status
   - Notes: textarea per note, timeline of notes with dates

6. PIPELINE (src/app/dashboard/pipeline/page.tsx)
   - Full-width kanban board (THE core feature — make it perfect)
   - Stages as columns with stage name header, deal count, total value in header
   - Deal cards: title, contact name (with avatar initials), value, close date, probability badge, days in stage counter
   - Drag and drop between columns (@dnd-kit): onDragEnd → update deal.stage_id in Supabase + add activity log entry
   - Optimistic UI: move card instantly client-side, sync to DB in background, rollback if error
   - Click deal card → deal detail modal (not new page)
   - "Add Deal" button on each column + global add button
   - Stage totals recalculate live on drag
   - Won/Lost buttons on deal detail → move to special won/lost column with timestamp

7. DEAL DETAIL MODAL (component):
   - Title, contact selector, pipeline/stage, value, currency, close date, probability slider (0-100%)
   - Notes textarea
   - Activity timeline: moves between stages, tasks completed, emails sent, notes added (auto-generated from events)
   - Tasks tab: tasks linked to this deal
   - "AI Deal Summary" button: sends deal info + activity to OpenAI → returns "Deal is in [stage] for [X days]. Last activity: [Y]. Probability: [Z]%. Suggested next step: [suggestion]."

8. TASKS (src/app/dashboard/tasks/page.tsx)
   - Tabs: Today | Tomorrow | This Week | Overdue | All
   - List view: task name, contact/deal link, type icon (📞 call / 📧 email / 🤝 meeting / 👤 follow-up), due date
   - Status: overdue = red border, today = amber border, future = default
   - Checkbox to complete (with strikethrough animation)
   - Add task: title, type, due date, linked contact/deal, notes
   - Quick add: floating "+" button, minimal form

9. EMAIL SEQUENCES (src/app/dashboard/sequences/page.tsx)
   - Sequences list: name, steps count, enrolled count, active toggle
   - Create/edit sequence: name, then a step builder:
     * Each step: delay (Day 0, Day 3, Day 7 etc.), subject, body textarea
     * Body has merge tag buttons: {{firstName}}, {{lastName}}, {{company}}, {{dealTitle}}
     * Add/remove/reorder steps
   - Enroll contacts: button opens contact multi-select → enrolls them in sequence
   - Enrolled contacts per sequence: table showing contact, current step, last email sent, next email scheduled

10. ANALYTICS (src/app/dashboard/analytics/page.tsx)
    - Win rate: (won deals / total closed deals) × 100
    - Average deal size: running average over time (line chart)
    - Deal velocity: average days from created to won/lost (per stage breakdown)
    - Revenue by month: bar chart of won deals by month
    - Pipeline funnel: visual funnel showing deal count and value at each stage
    - Top contacts by deal value (table)
    - Source breakdown: which contact source (cold/referral/inbound) produces the most won deals

11. SETTINGS (src/app/dashboard/settings/page.tsx)
    - Tabs: Profile, Pipeline Setup, Notifications
    - Profile: name, email, company
    - Pipeline Setup: rename stages, add stages, reorder stages, set default probability per stage
    - Default pipeline setup seed: Lead → Contacted → Proposal Sent → Negotiation → Won / Lost

12. BILLING (src/app/dashboard/billing/page.tsx)
    - Current plan, contact count (X/250 on free), upgrade CTA, Stripe portal

═══════════════════════════════════════
KEY FEATURE IMPLEMENTATIONS
═══════════════════════════════════════

KANBAN DRAG-AND-DROP — use @dnd-kit/core:
import { DndContext, DragEndEvent, closestCorners } from '@dnd-kit/core'
import { SortableContext, verticalListSortingStrategy } from '@dnd-kit/sortable'
onDragEnd(event: DragEndEvent):
  const { active, over } = event
  if (!over || active.id === over.id) return
  const newStageId = over.id as string
  const dealId = active.id as string
  // Optimistic update: update local state immediately
  setDeals(prev => prev.map(d => d.id === dealId ? {...d, stage_id: newStageId} : d))
  // Sync to DB
  supabase.from('deals').update({stage_id: newStageId}).eq('id', dealId)
  // Log activity
  supabase.from('deal_activities').insert({deal_id: dealId, event_type: 'stage_change', description: `Moved to ${stageName}`})

EMAIL SEQUENCE ENGINE — src/lib/sequence-engine.ts:
processScheduledEmails(): 
  1. SELECT * FROM scheduled_emails WHERE scheduled_at <= now() AND sent_at IS NULL LIMIT 50
  2. For each: replace merge tags, send via Resend, mark sent_at = now()
  3. Enroll in next step: find next sequence_step, insert new scheduled_email with correct delay
  Call this on every dashboard page load (or set up Vercel cron)

MERGE TAG REPLACEMENT — src/lib/merge-tags.ts:
replaceMergeTags(template: string, contact: Contact, deal?: Deal): string:
  return template
    .replace(/{{firstName}}/g, contact.first_name || '')
    .replace(/{{lastName}}/g, contact.last_name || '')
    .replace(/{{company}}/g, contact.company || '')
    .replace(/{{dealTitle}}/g, deal?.title || '')

CSV IMPORT — src/app/api/contacts/import/route.ts:
  - Accept multipart form with CSV file
  - Parse with papaparse server-side (papaparse.parse(csv, {header: true}))
  - Map detected columns to contact fields
  - Bulk insert via supabase.from('contacts').insert(mappedRows)
  - Return: {imported: n, errors: [...]}

AI EMAIL WRITER — src/app/api/ai/email/route.ts:
Input: {contactName, contactCompany, context, goalOfEmail}
Prompt: "Write a short, personalized sales email to {contactName} at {contactCompany}. Context: {context}. Goal: {goalOfEmail}. Tone: conversational and genuine, not salesy. Keep it under 150 words. Subject line + body. Return JSON: {subject: string, body: string}"

AI DEAL SUMMARY — src/app/api/ai/deal-summary/route.ts:
Input: {dealTitle, stage, value, daysSinceCreated, lastActivity, probability}
Prompt: "Summarize this deal status for a solopreneur. Deal: {dealTitle}, Stage: {stage}, Value: ${value}, Days in pipeline: {daysSinceCreated}, Last activity: {lastActivity}, Probability: {probability}%. Write 2-3 sentences: where the deal stands, momentum assessment, and the single best next action. Be direct and practical."

SEED DATA:
1 default pipeline "Main Pipeline" with stages: Lead (10%) → Contacted (25%) → Proposal Sent (50%) → Negotiation (75%) → Won (100%) / Lost (0%)
15 fake contacts (realistic global names — mix of Kenyan, American, British)
12 fake deals spread across stages, with varied values ($500–$25,000)
6 tasks (some overdue, some today, some future)
1 sample email sequence "Cold Outreach" with 3 steps

═══════════════════════════════════════
DESIGN SYSTEM
═══════════════════════════════════════
Dark theme. Efficient, no-nonsense aesthetic. Anti-enterprise.
Background: #09100f, Surface: #0f1a1c, Border: #1a2e30
Accent: cyan #06b6d4, Secondary: indigo #6366f1
Won = #10b981 (green), Lost = #ef4444 (red), Overdue = #f59e0b (amber)
Font: Geist Sans (clean, modern, trustworthy)
Deal cards: subtle left border in stage color, value in large font, clean minimal info
Kanban columns: semi-transparent header with stage name, deal count chip, total value
Drag: card being dragged gets slight scale-up + shadow elevation + rotation (2 degrees)
Contact table: sticky header, row hover = subtle cyan highlight
Sidebar detail: 400px wide, slides from right, backdrop blur

Build order: layout → auth → pipeline kanban (CORE — this is what people will show others) → contacts table → contact detail sidebar → tasks → sequences → analytics → landing.

The pipeline kanban IS SoloCRM. Someone should be able to drag a deal from "Lead" to "Won" and feel a small dopamine hit. Make the drag smooth, the card beautiful, and the stage totals satisfying to watch update in real time.
```

---

## 📁 Folder Layout After Prompt 0

```
your-dev-folder/
├── reviewpilot/    ← CMD Window 1 → Paste Prompt 1
├── studiopilot/    ← CMD Window 2 → Paste Prompt 2
├── academiaai/     ← CMD Window 3 → Paste Prompt 3
├── chamavault/     ← CMD Window 4 → Paste Prompt 4
└── solocrm/        ← CMD Window 5 → Paste Prompt 5
```

## ⚡ After Building — Same 3 Steps Per Project
1. Supabase project → SQL editor → run schema.sql → copy URL + keys to .env.local
2. Stripe → create products → copy price IDs to .env.local
3. Vercel → import repo → add env vars → deploy
