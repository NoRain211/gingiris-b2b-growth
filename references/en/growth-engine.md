# Part 2: Building the Growth Engine

## 1. PLG + SLG Hybrid Model

| Model | Definition | Advantage |
|:---|:---|:---|
| **PLG** | Product as core marketing tool | Ultra-low CAC, high scalability |
| **SLG** | Sales team as driver | Win complex deals, high LTV |

Most successful B2B companies don't pick one — they run both simultaneously. PLG feeds the top of funnel with volume. SLG captures the high-value accounts that self-serve won't close. The hard part is the handoff between them.

### Conversion Benchmarks

| Motion | Metric | Typical Range | Top Quartile |
|:---|:---|:---|:---|
| **Freemium → Paid** | Free-to-paid conversion | 2–5% | 7–10% |
| **Free Trial (no CC)** | Trial-to-paid conversion | 8–15% | 18–25% |
| **Free Trial (CC required)** | Trial-to-paid conversion | 30–50% | 55–65% |
| **Reverse Trial** | Downgrade prevention rate | 40–60% | 65%+ |
| **PQL → SQL** | Sales acceptance rate | 20–35% | 40–50% |
| **SQL → Closed Won** | Win rate (PLG-sourced) | 25–40% | 45%+ |
| **PLG-sourced ACV** | Average contract value | Lower than outbound | Comparable after expansion |

Reverse trials (full features for N days, then downgrade to free) consistently outperform both pure freemium and standard free trials. Notion, Airtable, and Figma all moved toward this model.

### PQL (Product Qualified Lead) Scoring Model

PQLs replace the traditional MQL. Instead of measuring marketing engagement (downloaded a whitepaper), you measure product engagement (actually using the thing). This is the core advantage of PLG — you know who's getting value before sales ever talks to them.

#### Scoring Dimensions and Weights

| Dimension | Signal | Points | Weight | Rationale |
|:---|:---|:---|:---|:---|
| **Activation** | Completed core value action (e.g., exported 3+ videos, created first workflow) | 0–25 | High | Proves they experienced the product's value proposition |
| **Frequency** | Login frequency over rolling 14 days | 0–20 | High | Daily/weekly usage = workflow integration |
| **Depth** | Number of features used beyond core action | 0–15 | Medium | Breadth of adoption signals stickiness |
| **Collaboration** | Invited 3+ team members, created shared workspace | 0–20 | High | Multi-user = organizational adoption, much harder to churn |
| **Firmographic Fit** | Company size, industry, domain (Fortune 500 email vs. gmail) | 0–10 | Medium | Ability to pay ≠ willingness, but it matters |
| **Expansion Signals** | Hitting usage limits, viewing pricing page, API usage | 0–10 | Medium | Intent signals that complement behavioral data |

**Total: 100 points**

#### PQL Thresholds

| Score Range | Classification | Action |
|:---|:---|:---|
| **0–30** | Nurture | In-app education, onboarding emails, no sales touch |
| **31–55** | Warm PQL | Automated nudges, in-app upgrade prompts, low-touch sales (pooled CSM) |
| **56–75** | Hot PQL | SDR outreach within 24 hours, personalized based on usage data |
| **76–100** | Sales Emergency | AE direct engagement within 4 hours, white-glove treatment |

#### Behavioral Triggers for Sales Outreach

Don't wait for a score threshold — these specific events should trigger immediate sales action regardless of cumulative score:

| Trigger | Why It Matters | Response Time |
|:---|:---|:---|
| **Pricing page visited 3+ times in 7 days** | Active purchase evaluation | SDR email within 4 hours |
| **Usage limit hit** | Needs more than free tier provides | In-app upgrade prompt + SDR outreach within 24 hours |
| **Admin invited 5+ users in one session** | Organizational rollout beginning | AE call within same business day |
| **Enterprise SSO or SCIM configuration attempted** | IT/security evaluation underway | SE + AE joint outreach within 4 hours |
| **API key generated + first API call** | Developer integration starting | Developer relations + AE within 24 hours |
| **Export or download of data** | Could be evaluating competitors, or preparing to present internally | SDR outreach within 24 hours |
| **Billing page visited by non-original signup** | Finance/procurement involved | AE outreach with ROI materials within 4 hours |

### PLG → SLG Handoff Process

This is where most hybrid models break down. Sales contacts a self-serve user who doesn't want to talk to sales. Or worse, sales never contacts someone who desperately needs help buying.

#### Handoff Workflow

**Step 1: PQL Identification (Automated)**
- Product analytics platform (Amplitude, Mixpanel, Heap) feeds usage data to your data warehouse
- Scoring model runs on a schedule (hourly for hot triggers, daily for cumulative scores)
- PQLs are pushed to CRM (Salesforce, HubSpot) with full usage context

**Step 2: Enrichment (Automated)**
- Clearbit/ZoomInfo enrichment fires on PQL creation
- Company size, industry, tech stack, funding stage appended
- Existing account matching: is this user from a company already in pipeline?

**Step 3: Routing**
- Score 56–75: Round-robin to SDR team
- Score 76+: Route to named AE if account is already owned, otherwise to SDR team lead for assignment
- Enterprise domain detected: Route to enterprise AE regardless of score
- Existing customer (expansion): Route to assigned CSM

**Step 4: Context-Rich Outreach**
The sales rep must reference the user's actual product usage. Generic outreach to a PQL is worse than no outreach.

Bad: "Hi, I noticed you signed up for [Product]. Would you like to schedule a demo?"
Good: "Hi, I saw your team has built 12 workflows this week and you're approaching the 50-workflow limit on your current plan. Teams at your stage typically need [specific feature on paid plan]. Want me to walk through how [similar company] handled this?"

**Step 5: Feedback Loop**
- Sales marks PQL outcome in CRM: Converted, Disqualified (with reason), Not Ready (recycled to nurture)
- Data team reviews PQL→SQL conversion rates monthly
- Scoring model is recalibrated quarterly based on what actually converts

#### Common Failure Modes

| Failure | Symptom | Fix |
|:---|:---|:---|
| Sales ignores PQLs | Low contact rate, PQLs age out | Make PQL follow-up a tracked KPI, show reps that PQL win rates are 2–3x outbound |
| Sales contacts too early | High opt-out rate, negative NPS from sales touch | Raise PQL threshold, add mandatory activation criteria |
| No usage context in CRM | Reps send generic outreach | Build dashboards that show per-account usage, embed in CRM |
| PLG and SLG teams compete | Channel conflict over attribution | Clear rules: if user self-serves before sales contact, PLG gets credit. Comp plans should not penalize either channel. |
| Free tier is too generous | Low conversion rate, high infrastructure cost | Time-bound trials of premium features, usage limits on collaboration features specifically |

---

## 2. Affiliate Marketing

| Company | Model | Cookie Duration | Best For |
|:---|:---|:---|:---|
| **InVideo** | **50% first order** | 120 days | Mid-low price, high conversion tools |
| **HeyGen** | **20% for 12 months** | 90 days | Subscription, high retention SaaS |
| **Deel** | **$500–$1500 fixed bounty** | 90 days | High ticket enterprise services |

### Choosing Your Commission Model

The three models above represent fundamentally different bets:

**Percentage of first order** works when your product has a low price point and high trial-to-paid conversion. You're paying for volume. The affiliate's incentive is to drive as many signups as possible.

**Recurring percentage** works when your product has strong retention. You're aligning the affiliate's incentive with yours — they benefit from referring customers who stick around. This is the best model for most B2B SaaS.

**Fixed bounty** works for high-ACV products where the commission on a percentage basis would either be absurdly high (making fraud attractive) or where the sales cycle is long and you want affiliates motivated to refer enterprise leads.

### Calculating Optimal Commission Rates

The math:

```
Maximum Commission = (Customer LTV × Target Profit Margin Remaining) − Other CAC Components

Example:
- Average customer LTV: $6,000 (over 3 years)
- Target blended gross margin after CAC: 70%
- Budget available for acquisition: $6,000 × 30% = $1,800
- Other CAC components (onboarding, tooling, attribution platform fees): $200
- Maximum affiliate commission: $1,600

If recurring: $1,600 ÷ 36 months = ~$44/month
If your average MRR is $167/month, that's ~26% recurring commission
If first-order only: $1,600 on a $167 first month is 958%, which is absurd
  → so for first-order %, use a fraction: e.g., 30–50% of first payment ($50–$83)
```

**Rules of thumb:**
- Recurring commission: 15–30% of MRR for 12–24 months
- First order commission: 30–100% of first month's payment
- Fixed bounty: 10–25% of first-year ACV
- Always ensure payback period stays under 12 months for affiliate-sourced customers
- Start conservative — it's easy to raise commissions but painful to lower them

### Affiliate Recruitment Strategies

#### Where to Find Affiliates

| Channel | Type of Affiliate | Expected Quality | Volume |
|:---|:---|:---|:---|
| **Your own customer base** | Power users who already evangelize | Highest (authentic advocacy) | Low–Medium |
| **YouTube reviewers in your category** | Content creators with tutorial channels | High (targeted audience) | Medium |
| **Comparison/review sites** (G2, Capterra affiliates) | Professional reviewers | Medium (mercenary but effective) | High |
| **Industry bloggers and newsletter operators** | Niche authority sites | High (trusted by audience) | Low |
| **Affiliate networks** (PartnerStack, Impact, ShareASale, CJ) | Professional affiliates | Variable (lots of low-quality) | Very High |
| **Competitors' affiliate programs** | Affiliates already selling to your ICP | Medium–High (may split loyalty) | Medium |
| **LinkedIn/Twitter influencers** | Thought leaders in your space | High if genuine, low if bought | Low |

#### Recruitment Outreach Template

Subject: [Their Content Title] + partnership opportunity

```
Hi [Name],

I found your [article/video/newsletter] on [topic]. Your breakdown of [specific thing
they covered] was [genuine compliment — be specific, not generic].

We built [Product] — [one sentence on what it does]. Given your audience of [their
audience description], I think there's a natural fit.

Our affiliate program pays [commission structure]. Our top affiliates earn [$X/month]
with an average conversion rate of [X%] on their referral links.

Interested? I can set you up with:
- A free [plan tier] account so you can try it yourself
- Custom landing page for your audience
- Early access to new features for review content

[Your name]
```

Key points: personalize genuinely, lead with their content quality, be specific about earnings potential, offer product access.

### Performance Tiers and Incentive Structures

| Tier | Monthly Referrals | Commission Rate | Bonus Perks |
|:---|:---|:---|:---|
| **Standard** | 1–10 | Base rate (e.g., 20%) | Affiliate dashboard, standard creatives |
| **Silver** | 11–25 | Base + 5% bonus | Dedicated affiliate manager, custom landing pages |
| **Gold** | 26–75 | Base + 10% bonus | Early feature access, co-branded content, quarterly bonus |
| **Platinum** | 76+ | Base + 15% bonus | Custom commission negotiation, joint webinars, annual retreat invite, product advisory board seat |

Accelerators that work:
- **Launch bonuses**: 2x commission for the first 90 days after a new affiliate joins
- **Seasonal pushes**: Bonus commission during your slow months to smooth revenue
- **SPIFs** (Sales Performance Incentive Funds): One-time bonus for hitting a stretch goal within a time window
- **Tiered unlock**: Higher commission rate kicks in retroactively to all that month's referrals once a threshold is hit (motivates pushing past the tier boundary)

### Affiliate Resource Kit

Give affiliates everything they need so they don't create off-brand or inaccurate content:

- **Creatives**: Banner ads (standard IAB sizes), social media images, email templates
- **Copy**: Pre-written descriptions (short, medium, long), key differentiators, competitor comparison talking points
- **Landing pages**: Custom co-branded landing pages that convert better than your generic homepage
- **Demo videos**: Short product walkthroughs they can embed or link to
- **Data sheets**: ROI calculators, case study summaries, industry stats
- **Tracking links**: UTM-tagged links with unique affiliate IDs, deep links to specific pages/features
- **Discount codes**: Exclusive codes for their audience (also helps with attribution)
- **Content calendar**: Upcoming launches, features, and promotions they can align content with

### Attribution Models

| Model | How It Works | Best For | Risk |
|:---|:---|:---|:---|
| **Last-click** | Credit goes to the last affiliate link clicked before conversion | Simple programs, low-touch products | Ignores top-of-funnel affiliates who drive awareness |
| **First-click** | Credit goes to the first affiliate link clicked | Rewarding awareness/discovery | Ignores affiliates who close the deal |
| **Linear** | Credit split equally across all affiliate touches | Fair but complex | Dilutes commissions, harder to understand |
| **Time-decay** | More credit to touches closer to conversion | Balanced approach | Requires sophisticated tracking |
| **Last-click with lookback window** | Last click, but only within cookie duration | Most B2B SaaS programs (pragmatic default) | Window length matters: too short loses credit, too long over-attributes |

For most B2B SaaS: use **last-click with a 60–90 day lookback window**. It's simple enough for affiliates to understand, and the window is long enough to capture the B2B evaluation cycle.

### Affiliate Fraud Detection

Fraud will happen. Plan for it.

| Fraud Type | How It Works | Detection Method | Prevention |
|:---|:---|:---|:---|
| **Cookie stuffing** | Affiliate drops cookies via hidden iframes/images on high-traffic sites, claiming credit for organic conversions | Abnormally high impression-to-click ratios, conversions without genuine clicks | Use server-side tracking, require actual click events, monitor click-to-conversion correlation |
| **Self-referrals** | Affiliate signs up through their own link | Match affiliate email/payment details against customer records | Explicitly prohibit in TOS, auto-flag matching domains/IPs, require minimum 30-day gap between affiliate signup and referred customer |
| **Click fraud** | Bots or click farms generating fake clicks to inflate metrics (relevant for CPC models) | Traffic analysis: look for impossible geographic patterns, uniform time-between-clicks, abnormal bounce rates | Don't pay per click — pay per conversion. If you must use CPC, require minimum session duration |
| **Trademark bidding** | Affiliate buys Google Ads on your brand name, claims credit for people already searching for you | Monitor brand SEM via tools like SEMrush or SpyFu | Explicitly prohibit brand bidding in affiliate agreement, enforce with regular audits |
| **Incentivized signups** | Affiliate pays people to sign up through their link | Very high signup volume with near-zero activation/engagement | Require activation milestones before commission triggers (not just signup, but first value action) |
| **Lead recycling** | Submitting the same leads through multiple channels or re-submitting expired leads | Duplicate detection on email, phone, company domain | Deduplicate against existing pipeline, enforce 90-day exclusion windows |

**Baseline fraud rate to expect:** 5–15% of affiliate-driven conversions will be fraudulent or low-quality. Build this into your financial model and audit aggressively. Hold commissions for 30–60 days before payout (clawback window).

### Platform Selection

| Platform | Best For | Pricing | Key Feature |
|:---|:---|:---|:---|
| **PartnerStack** | B2B SaaS | % of payouts + base fee | Built for SaaS, handles partner types beyond affiliates |
| **Impact** | Mid-market to enterprise | Custom pricing | Strong fraud detection, flexible attribution |
| **ShareASale** | SMB, wide affiliate network | $625 setup + transaction fees | Large existing affiliate network |
| **Rewardful** | Early-stage SaaS | From $49/month | Stripe integration, simple setup |
| **FirstPromoter** | SaaS with recurring revenue | From $49/month | Built specifically for recurring commission tracking |

---

## 3. Channel Partner Ecosystem

### Four Core Partner Types

| Partner Type | Core Value | Collaboration Model |
|:---|:---|:---|
| **Tech Integration** | Extend product capabilities | API integration, marketplace listing |
| **Solution Partner** | Industry solutions and implementation | Consulting, implementation, resale |
| **Cloud Marketplace** | Leverage cloud giant channels | List on AWS/Azure/GCP Marketplace |
| **Strategic Alliance** | Brand endorsement and co-selling | Joint marketing, co-selling, co-development |

### Partner Recruitment Playbook

#### Identifying Potential Partners

Look for companies that:
- Sell to your ICP but don't compete with you
- Have a services business that needs product differentiation
- Are already integrating with you informally (check your API logs)
- Show up in your "how did you hear about us?" responses
- Are mentioned by customers as part of their stack

#### Recruitment Process

**Phase 1: Research and Targeting (Weeks 1–2)**
- Build a target list of 50–100 potential partners
- Score by: audience overlap with your ICP, technical capability, market presence, strategic alignment
- Identify the right contact: partnerships/BD team lead, not the CEO (unless it's a small firm)

**Phase 2: Outreach (Weeks 3–4)**
- Lead with what you can do for them, not what you need
- Show data: "Our mutual customers who use [their product] + [your product] have 40% higher retention"
- Offer a low-commitment pilot: joint webinar, integration project, co-authored content

**Phase 3: Pilot (Weeks 5–12)**
- Define success metrics upfront: number of joint customers, revenue influenced, integration adoption
- Assign a dedicated partner manager (not a shared resource)
- Run a joint go-to-market motion on a single campaign or segment

**Phase 4: Formalize (Week 13+)**
- If pilot hits metrics, formalize with a partner agreement
- Define tier placement, training requirements, revenue commitments
- Announce partnership publicly (press release, joint blog, marketplace listing)

### Partner Tiers and Requirements

| Tier | Annual Revenue Requirement | Certified Reps | Requirements | Benefits |
|:---|:---|:---|:---|:---|
| **Registered** | $0 (new partners) | 0 | Sign partner agreement, complete onboarding | Partner portal access, basic training, 10% referral fee |
| **Silver** | $50K influenced revenue | 2 | Complete sales certification, 1 joint customer win | 15% referral/resale margin, co-marketing funds ($2K/quarter), listed in partner directory |
| **Gold** | $200K influenced revenue | 5 | Complete technical certification, quarterly business reviews, dedicated customer success | 20% referral/resale margin, co-marketing funds ($10K/quarter), joint case studies, priority support, beta access |
| **Platinum** | $500K+ influenced revenue | 10+ | Executive sponsor alignment, annual planning, joint product roadmap input | 25%+ margins (negotiated), $25K+/quarter MDF, co-selling with your AEs, partner advisory board, executive briefings |

These numbers are calibrated for a SaaS product with $50K–$200K ACV. Scale the thresholds proportionally for your price point.

### Partner Enablement Program

#### Certification Curriculum

**Sales Certification (Required for Silver+)**
- Module 1: Product overview and positioning (2 hours)
- Module 2: ICP and buyer personas (1 hour)
- Module 3: Competitive landscape and objection handling (2 hours)
- Module 4: Demo delivery (2 hours + practical exam)
- Module 5: Pricing, packaging, and deal structuring (1 hour)
- Assessment: Deliver a mock demo to your team, score 80%+ to pass
- Recertification: Annual, with update modules for new features

**Technical Certification (Required for Gold+)**
- Module 1: Architecture and integration patterns (4 hours)
- Module 2: Implementation methodology (4 hours)
- Module 3: API deep dive and custom development (4 hours)
- Module 4: Security, compliance, and data handling (2 hours)
- Module 5: Troubleshooting and escalation procedures (2 hours)
- Assessment: Complete a reference implementation, pass technical review
- Recertification: Annual

**Delivery Certification (Optional, for implementation partners)**
- Module 1: Project scoping and SOW development (2 hours)
- Module 2: Migration and data onboarding playbook (4 hours)
- Module 3: Change management for end users (2 hours)
- Module 4: Post-go-live success measurement (1 hour)
- Assessment: Lead a supervised implementation

#### Sales Training for Partners

Give partners the same materials your own sales team uses, plus:
- Battle cards vs. competitors (including scenarios where your product isn't the right fit — partners respect honesty)
- ROI calculator they can customize for their prospects
- Reference customer list they can offer for prospect calls
- Pricing guidelines with approved discount authority by tier

### Co-Selling Motions

#### Deal Registration

Deal registration prevents channel conflict and gives partners confidence to invest time in opportunities.

**Rules:**
- Partner registers a deal by submitting: company name, contact info, estimated deal size, expected close date
- Your team checks for conflicts within 48 hours (is this account already in your pipeline?)
- If approved: partner has exclusive protection for 90 days (renewable once)
- If the account is already in pipeline: partner can still participate in a co-sell motion, but your direct AE leads
- If the partner's deal stalls (no activity for 30 days), protection lapses with notice

#### Revenue Sharing Models

| Model | How It Works | When to Use |
|:---|:---|:---|
| **Referral fee** | Partner refers lead, you close. Partner gets 10–20% of first-year ACV. | Partner has relationships but not sales capacity |
| **Reseller margin** | Partner sells, bills customer, pays you wholesale (typically 70–80% of list). | Partner wants to own the customer relationship. Common with large consulting firms. |
| **Influence/co-sell** | Partner is involved in the deal alongside your AE. Partner gets 5–15% of ACV. | Complex enterprise deals where partner adds credibility or implementation expertise |
| **Marketplace revenue share** | Cloud marketplace takes 3–5% (negotiable at scale). Customer uses committed cloud spend. | Enterprise customers with cloud commits they need to burn down |

### Partner Portal Requirements

Minimum viable partner portal:
- Deal registration form and status tracking
- Lead distribution and acceptance workflow
- Training modules and certification tracking
- Marketing asset library (co-brandable templates)
- Commission/margin statements and payout history
- Support ticket escalation path
- Performance dashboard: pipeline, revenue, conversion rates

Don't build this from scratch. Use Crossbeam or Reveal for account mapping, and PartnerStack or Allbound for the portal.

### Handling Channel Conflict

Channel conflict is inevitable. Plan for it.

| Conflict Type | Scenario | Resolution |
|:---|:---|:---|
| **Direct vs. partner** | Your AE is working an account that a partner also registered | First-registered wins (check timestamps). If concurrent, co-sell with partner and split. |
| **Partner vs. partner** | Two partners both claim the same opportunity | First-registered wins. If concurrent, let the customer decide who they want to work with. |
| **Self-serve vs. partner** | Customer found you through PLG but partner claims they influenced it | If customer activated in PLG before partner registered, partner gets reduced influence fee (5%), not full referral. |
| **Renewal conflict** | Partner brought the initial deal but hasn't been involved for 2 years. Claims renewal commission. | Commissions on renewals only if partner remains active in account (defined as: quarterly check-in with customer, maintains certification). |

The meta-rule: be transparent about your conflict resolution policy, publish it in the partner agreement, and apply it consistently. Partners will tolerate losing a specific deal if they trust the system is fair.

### Market Development Funds (MDF)

MDF is money you give partners to fund joint marketing activities. It's not a gift — it requires co-investment and proof of execution.

**How to structure MDF:**

| Category | Eligible Activities | Funding Model | Proof Required |
|:---|:---|:---|:---|
| **Demand generation** | Joint webinars, events, email campaigns, digital ads | 50/50 co-investment or 100% funded at Gold+ | Registration/attendance lists, lead outcomes |
| **Content** | Co-authored whitepapers, case studies, blog posts | 100% funded (you control quality) | Published asset, distribution metrics |
| **Events** | Conference sponsorship, partner-hosted dinners, roadshows | 50/50 co-investment | Attendee list, pipeline generated within 90 days |
| **Enablement** | Partner's internal training sessions, hackathons | 100% funded | Attendance records, certification completions |

**MDF budget rule of thumb:** allocate 2–5% of partner-sourced revenue back into MDF. Track ROI per MDF dollar — pipeline generated per dollar spent should be 5–10x minimum.

---

## 4. Direct Sales

### Sales Team Structure: SDR + AE + SE + CSM

| Role | Responsibility | Key Metrics |
|:---|:---|:---|
| **SDR** | Outbound prospecting, inbound lead qualification, BANT/MEDDPICC initial assessment, hand off SQL to AE | Meetings booked, SQL generated, response rates |
| **AE** | Discovery, demo, negotiation, closing | Pipeline generated, win rate, ACV, sales cycle length |
| **SE** | Technical validation, PoC/pilot management, integration architecture | PoC win rate, technical close rate, time-to-value |
| **CSM** | Onboarding, adoption, retention, expansion, renewal | Net revenue retention, NPS, time-to-value, expansion revenue |

**Ratios (rough benchmarks):**
- 2–3 SDRs per AE (mid-market)
- 1 SDR per AE (enterprise, where quality > quantity)
- 1 SE per 2–3 AEs
- 1 CSM per $1–2M ARR under management (mid-market), 1 per $500K–$1M (enterprise)

### SDR Outreach Cadence: 30-Day Multi-Channel Sequence

This is a proven sequence for cold outbound to mid-market and enterprise prospects. Adjust timing for your audience — shorter cadence for SMB, longer for enterprise.

| Day | Channel | Action | Notes |
|:---|:---|:---|:---|
| **1** | Email | Personalized cold email #1 — problem-focused, no product pitch | Reference a specific trigger: funding round, job posting, tech stack signal, industry event |
| **2** | LinkedIn | Connect request with personalized note (under 300 chars) | Reference same trigger as email |
| **3** | Phone | Call attempt #1 — if voicemail, leave a 30-second message referencing email | Don't pitch on voicemail. Goal: curiosity, not a meeting |
| **5** | Email | Email #2 — share a relevant case study or data point | "Companies in [their industry] typically see [specific result]" |
| **7** | LinkedIn | Engage with their content (like, thoughtful comment) | Don't pitch in comments. Be a human. |
| **9** | Phone | Call attempt #2 | If you connect: ask about the problem, don't pitch the product |
| **11** | Email | Email #3 — short, different angle, ask a question | "Curious how you're currently handling [specific problem]?" |
| **14** | LinkedIn | Send a relevant article, report, or insight via DM | Not your content. Third-party credibility. |
| **17** | Email | Email #4 — social proof from their peer group | "[Competitor/peer company] reduced [metric] by X% — happy to share how" |
| **21** | Phone | Call attempt #3 | Last call attempt in the sequence |
| **24** | Email | Email #5 — breakup email | "I'll stop reaching out. If [problem] becomes a priority, here's my calendar link." |
| **30** | LinkedIn | Final touchpoint — share something genuinely useful, no ask | Close the loop warmly |

**Key principles:**
- Never send more than one touch per day
- Every email should be under 125 words
- Every touch should offer value, not just ask for time
- Personalization must be specific: company name and job title are not personalization
- Track reply rates per step. If step N has <1% reply rate, rewrite it.
- After the sequence ends, recycle to a quarterly nurture drip

### Qualification Frameworks

#### BANT (Budget, Authority, Need, Timeline)

BANT is the baseline. It's simple and works for transactional sales. For complex enterprise deals, layer MEDDPICC on top.

| Criterion | Key Questions | Qualified If... |
|:---|:---|:---|
| **Budget** | "Do you have budget allocated for this?" / "What's the typical approval process for investments in this range?" | Budget exists or can be created. Prospect can describe their procurement process. |
| **Authority** | "Who else is involved in this decision?" / "Walk me through how your team has made similar purchasing decisions." | You've identified the economic buyer and they're accessible. Decision process is clear. |
| **Need** | "What's driving the evaluation?" / "What happens if you don't solve this?" | There's a real problem with measurable impact. Status quo has a cost. |
| **Timeline** | "When do you need this in place?" / "Is there an event driving the timeline?" | There's a forcing function — contract renewal, board mandate, compliance deadline, competitive pressure. |

#### MEDDPICC (for Enterprise and Complex Deals)

| Element | What It Means | Discovery Questions | Red Flag |
|:---|:---|:---|:---|
| **Metrics** | Quantifiable business outcomes the buyer needs | "What KPIs will this impact? By how much?" | Buyer can't articulate measurable outcomes |
| **Economic Buyer** | The person who can sign the check | "Who has final budget authority? Have we met them?" | You've never spoken to the EB, only a champion |
| **Decision Process** | How they'll evaluate and decide | "Walk me through the steps from here to a signed contract." | "We'll figure it out" — no defined process means no real deal |
| **Decision Criteria** | What they're evaluating against | "What are the must-have requirements? Nice-to-haves?" | Their criteria perfectly match a competitor's feature set |
| **Paper Process** | Legal, procurement, security review | "What does your procurement process look like? Who reviews contracts?" | They don't know or won't discuss — the deal will stall at legal |
| **Identified Pain** | The specific problem driving the purchase | "What's the cost of the current situation? Who feels it most?" | Pain is theoretical, not felt by someone with budget authority |
| **Champion** | Internal advocate who sells when you're not in the room | "Who internally is sponsoring this initiative?" | Your "champion" can't get you a meeting with the EB |
| **Competition** | Who else they're evaluating | "What other approaches are you considering, including doing nothing?" | They won't tell you, or they're already deep in a competitor's PoC |

**MEDDPICC scoring:** Score each element 0 (unknown), 1 (partially identified), 2 (fully confirmed). Deals scoring below 10/16 should not be in your commit forecast.

### Discovery Call Framework

A discovery call is not a demo. You should talk less than 30% of the time.

**Structure (30 minutes):**

1. **Rapport and agenda** (3 min): Set expectations. "I'd love to understand your situation before showing you anything. Can I ask some questions first?"
2. **Current state** (8 min): How they do things today. What tools they use. What the workflow looks like.
3. **Problems and pain** (8 min): What's broken. What frustrates them. What the business impact is. Quantify everything.
4. **Desired future state** (5 min): What would good look like? What would change if this problem were solved?
5. **Process and timeline** (4 min): Decision process, stakeholders, timeline, budget.
6. **Next steps** (2 min): Agree on a specific next action with a specific date. "Can we schedule a technical deep-dive with your team lead on Thursday at 2pm?"

**Rules:**
- Ask open-ended questions. Never ask "Do you have this problem?" (they'll say yes to be polite)
- Take notes visibly — it shows you're listening and gives you material for follow-up
- Confirm understanding by playing it back: "So if I'm hearing you right, the core issue is..."
- Don't demo during discovery unless they explicitly ask. Even then, keep it under 5 minutes.

### Demo Best Practices

- **Tailor to their pain**: If discovery revealed three problems, demo exactly those three solutions. Nothing else.
- **Start with the "wow" moment**: Don't build up to it. Show the most impressive thing in the first 2 minutes.
- **Use their data if possible**: A demo with the prospect's actual data is 3x more effective than a generic one.
- **Keep it under 20 minutes**: Attention drops sharply after 20 minutes. Save time for Q&A.
- **Pause after each key feature**: "How does that compare to how you do it today?" Forces engagement and surfaces objections early.
- **Record and share**: Send the recording after. Your champion will use it to sell internally.

### Multi-Threading for Enterprise

Simultaneously build relationships with multiple key roles. Single-threaded deals (where you only know one person) have a 30–40% lower win rate.

| Stakeholder | Role in Decision | What They Care About | How to Engage |
|:---|:---|:---|:---|
| **Champion** | Internal advocate, sells when you're not there | Making themselves look good, solving their team's problem | Arm them with materials, make them the hero |
| **Economic Buyer** | Signs the check (usually VP+ or C-suite) | ROI, strategic alignment, risk mitigation | Executive briefing, ROI model, peer references |
| **Technical Buyer** | Evaluates technical fit (usually IT, engineering, security) | Integration, security, scalability, maintenance burden | SE-led technical deep dive, architecture review, security questionnaire |
| **End Users** | Will actually use the product daily | Ease of use, workflow fit, won't make their job harder | Hands-on trial, pilot program, user feedback sessions |
| **Procurement** | Manages the buying process | Compliance, pricing benchmarks, contract terms | Pre-fill their requirements, be responsive on paperwork |
| **Legal** | Reviews contracts | Data handling, liability, SLA terms | Provide redline-ready contracts, DPA, security certifications |

**Multi-threading tactics:**
- Ask your champion to introduce you to other stakeholders
- Host a "lunch and learn" or workshop that gives you exposure to the broader team
- Send different content to different stakeholders (technical content to technical buyer, ROI to economic buyer)
- If your champion leaves the company, you need other threads or the deal dies

### Negotiation Tactics

**Principles:**
- Never negotiate against yourself. If they ask for a discount, ask what they'd give in return (longer contract, case study, larger scope, faster signature).
- Anchor high. Your first offer should be full list price. Discounting from list is a concession; starting below list is leaving money on the table.
- Time pressure works both ways. If they have a deadline, so do you. "This pricing is valid through end of quarter."
- Walk-away power is real power. If you can't walk away, you can't negotiate.

**Common Discount Structures:**

| Concession They Want | What to Ask For in Return |
|:---|:---|
| 10–15% discount | Annual upfront payment (instead of monthly/quarterly) |
| 15–25% discount | Multi-year commitment (2–3 year term) |
| Extended pilot | Defined success criteria and automatic conversion if met |
| Free additional seats | Commitment to expand to full department within 6 months |
| Custom payment terms | Public case study + logo rights |
| Feature requests | Joint development agreement with co-marketing rights |

**Enterprise pricing strategies:**
- Always quote annual pricing, not monthly (anchors higher)
- Create three tiers; most buyers choose the middle one
- Bundle implementation/training into the contract (increases ACV, reduces risk of poor adoption)
- For very large deals: usage-based or consumption-based pricing de-risks the purchase for the buyer while aligning your incentives with their growth

### Contract Negotiation Playbook

| Stage | Your Goal | Common Pushback | Response |
|:---|:---|:---|:---|
| **MSA/Terms** | Standard terms, minimal redlines | "Our legal requires XYZ" | Pre-build a redline-ready contract with common enterprise terms already included. Have a "pre-approved concessions" list your AE can offer without legal review. |
| **SLA** | Commit to what you can deliver | "We need 99.99% uptime" | Show your actual uptime track record. Offer 99.9% with defined credits. 99.99% = 52 min downtime/year — only promise if you can deliver. |
| **Data Processing** | Standard DPA | "We need data residency in [region]" | If you support it, great. If not, be honest and offer encryption + access controls as alternatives. Don't promise what you can't deliver. |
| **Liability** | Capped liability | "Unlimited liability for data breach" | Cap at 12 months of fees paid. Carry cyber insurance and share the certificate. Most legal teams will accept this. |
| **Termination** | Annual minimum, pro-rata refund | "We want termination for convenience at any time" | Offer termination with 90-day notice and pro-rata refund of unused prepaid term. Never agree to immediate termination of annual contracts. |
| **Auto-renewal** | Auto-renew with 30-day opt-out notice | "No auto-renewal" | Accept it — forcing auto-renewal on an unhappy customer creates churn anyway. Notify 90 days before term end. |

---

## 5. Content-Led Growth

Content-led growth is not "having a blog." It's building a systematic content operation that captures demand at every funnel stage and compounds over time. For B2B SaaS, content is often the highest-ROI channel after year one, because content keeps generating traffic and leads long after it's published.

### SEO Strategy for B2B SaaS

#### Keyword Strategy by Intent

| Intent Type | Example Keywords | Content Type | Conversion Expectation |
|:---|:---|:---|:---|
| **Navigational** | "[Your product name] login", "[Your product] pricing" | Product pages, pricing page | High (already a user or evaluator) |
| **Commercial investigation** | "best [category] software", "[competitor] alternatives", "[product A] vs [product B]" | Comparison pages, alternatives pages, review roundups | High (active buying decision) |
| **Informational (problem-aware)** | "how to [solve problem your product solves]" | How-to guides, tutorials, templates | Medium (captures demand at problem stage) |
| **Informational (unaware)** | Broad industry topics | Thought leadership, research reports | Low (top of funnel, brand building) |

**Prioritize commercial investigation keywords first.** These convert at 5–10x the rate of informational content and are often neglected because they feel "competitive" or "salesy." A well-built "[Competitor] alternatives" page can be your highest-converting organic page.

#### Technical SEO Checklist for B2B

- Programmatic pages for integrations, use cases, templates (these scale organically)
- Schema markup: FAQ, HowTo, SoftwareApplication, Organization
- Core Web Vitals: LCP under 2.5s, CLS under 0.1
- Internal linking: every blog post links to at least 2 product pages and 2 related blog posts
- Canonical tags on all duplicate/similar content
- XML sitemap segmented by content type (blog, docs, product pages)
- Hreflang tags if you have multi-language content

### Content Types by Funnel Stage

| Funnel Stage | Content Type | Goal | Distribution Channel |
|:---|:---|:---|:---|
| **Top of Funnel** | Industry reports, original research, broad how-to guides, podcast | Brand awareness, email capture | SEO, social media, paid social (LinkedIn) |
| **Middle of Funnel** | Comparison pages, use case deep-dives, webinars, templates, calculators | Evaluate and consider your product | SEO, email nurture, retargeting |
| **Bottom of Funnel** | Case studies, ROI calculators, demo videos, security/compliance docs | Remove objections, enable purchase | Sales enablement, email nurture, website |
| **Post-Sale** | Documentation, academy courses, community content, changelog | Adoption, expansion, advocacy | In-app, email, community platform |

### Developer Marketing and Technical Content

If your buyers are developers or technical users, generic marketing content will actively hurt you. Developers can smell marketing from a mile away and will dismiss your product.

**What works for developers:**
- **Documentation that's actually good**: This is your #1 marketing asset. Clear, complete, with working code examples. If your docs are bad, nothing else matters.
- **Interactive tutorials**: Embed a sandbox or playground. Let developers try your API without signing up.
- **Open source contributions**: Open-source a library, tool, or framework adjacent to your product. Build goodwill and distribution.
- **Technical blog posts by engineers**: Written by your actual engineers about real problems they solved. Not ghostwritten marketing fluff.
- **CLI tools and SDKs**: Make integration frictionless. If a developer has to read a 20-page PDF to get started, you've lost them.
- **Community**: Discord, Slack community, or forum where developers help each other. Your community is a moat.

**What doesn't work for developers:**
- Gated content (developers will just leave)
- "Request a demo" as the only CTA (developers want to try, not watch)
- Case studies written in marketing language ("synergy", "leverage", "transform")
- Pricing that's hidden or "contact sales" (developers assume it means "expensive and annoying")

### Thought Leadership That Actually Works

Thought leadership is not rewriting what everyone else says. It's having a contrarian or novel point of view backed by evidence.

**Framework for thought leadership content:**
1. **Identify a widely held belief in your industry** that you disagree with or can nuance
2. **Support your contrarian view with data**: your own product data, customer data, original research, or credible third-party data
3. **Make it actionable**: don't just be contrarian for the sake of it. Tell people what to do differently.
4. **Publish under a named human**: thought leadership from a brand account is generic content. Thought leadership from a named founder/executive builds a personal brand that benefits the company.

**Distribution for thought leadership:**
- LinkedIn posts (800–1200 word posts perform best for B2B, post 2–3x per week)
- Industry conference talks (apply to speak, or host your own events)
- Podcast guest appearances (find podcasts your ICP listens to)
- Syndication to industry publications

---

## 6. Product-Led Sales

Product-led sales (PLS) is not the same as PLG. PLG is about self-serve acquisition. PLS is about using product usage data to drive expansion revenue within existing accounts. This is where the real money is — net revenue retention above 120% comes from PLS.

### Usage-Based Expansion Playbook

#### Expansion Triggers

| Trigger | Signal | Who Owns It | Action |
|:---|:---|:---|:---|
| **Seat limit approaching** | Account at 80%+ of licensed seats | CSM | Proactive outreach: "Your team is growing — let's make sure everyone who needs access has it." |
| **Usage limit approaching** | Account at 80%+ of API calls, storage, workflows, etc. | Automated + CSM | In-app warning at 80%, CSM outreach at 90%. Upgrade path should be one click. |
| **New team/department adoption** | Users from new email groups or cost centers appearing | AE | Expansion opportunity: new business unit. Run a new discovery for their specific needs. |
| **Feature gate hit** | User repeatedly encounters a paid feature gate | Automated | In-app: show what the feature does, offer a 7-day trial of the premium feature. |
| **Power user emergence** | Individual user with 3x average engagement | CSM | Recruit as internal champion. Invite to customer advisory board. Use them to drive adoption in other teams. |
| **Integration expansion** | Account connects new third-party tools via your API | SE + CSM | Premium integration support, discuss enterprise integration tier. |

#### Seat Expansion Strategy

Seat expansion is the easiest expansion motion because the value proposition is self-evident: more people need access.

**Viral loops that drive seat expansion:**
- **Collaboration features that require accounts**: Sharing a document, dashboard, or workspace requires the recipient to sign up
- **@mentions and notifications**: Mentioning a non-user in a comment triggers an email invitation
- **Team templates and shared resources**: New hires need access to team templates, creating natural expansion
- **Permission controls**: Admin features (audit logs, role-based access) require upgrading to a plan with admin capabilities

**Pricing for seat expansion:**
- Don't give volume discounts too early — the first 50 seats should be at full price
- Offer volume discounts at natural breakpoints: 50, 100, 250, 500+ seats
- Consider "platform fee + per-seat fee" model to maintain a revenue floor
- Annual commit with quarterly true-up for seat additions (customer adds seats mid-quarter, pays pro-rata immediately, reconciles at renewal)

### In-App Upgrade Prompts

**Where to place upgrade prompts (ranked by conversion rate):**

1. **At the moment of value delivery**: User completes a task successfully → "You've used 8 of your 10 free [things]. Upgrade to unlimited." (Highest conversion — user just experienced value)
2. **Feature gate**: User clicks a premium feature → Show what it does with a preview, offer trial or upgrade (High conversion — expressed intent)
3. **Usage milestone**: "You've saved 40 hours this month with [Product]. Your team could save 200+ hours on the Pro plan." (Medium conversion — social proof + extrapolation)
4. **Settings/admin page**: When admin is managing the workspace → upsell admin features (Medium conversion — admin context)
5. **Dashboard/home page**: Persistent banner → avoid this. Banner blindness sets in quickly. (Low conversion — no contextual relevance)

**Anti-patterns:**
- Don't interrupt workflows with modal popups
- Don't show upgrade prompts to users who can't make purchasing decisions (identify the admin/billing contact)
- Don't gate features that users have already been using (triggers rage, not upgrades)
- Don't show the same upgrade prompt more than once per session

### Usage Limit Design

How you design usage limits determines your free-to-paid conversion rate more than almost any other product decision.

**Good limits** restrict things that scale with business value:
- Number of active projects or workflows
- Team members (collaboration)
- Integrations connected
- Data retention period
- API call volume
- Storage

**Bad limits** restrict things that feel punishing:
- Number of logins
- Basic features that are table stakes in your category
- Export of the user's own data
- Core functionality after a time period with no warning

**The 80/20 rule for limits:** Your free tier should give users 80% of the functionality but only 20% of the scale. They should be able to do everything (proving value) but not at the volume they need for real work.

---

## 7. International Expansion

### Market Selection Criteria

Don't expand internationally because it sounds impressive. Expand because the data says there's demand.

#### Market Scoring Matrix

| Criterion | Weight | How to Measure |
|:---|:---|:---|
| **Existing organic demand** | 30% | Website traffic from that country, inbound inquiries, existing customers |
| **Market size (TAM)** | 20% | Number of companies in your ICP in that market (use LinkedIn Sales Nav, Statista, local industry reports) |
| **Competitive landscape** | 15% | Are local competitors dominant? Is the market greenfield or crowded? |
| **Ease of doing business** | 15% | Payment infrastructure, legal complexity, language barriers, time zone overlap |
| **Willingness to pay** | 10% | Average SaaS spend in that market, price sensitivity, foreign currency stability |
| **Strategic value** | 10% | Does winning this market unlock adjacent markets? (e.g., UK → Europe, Singapore → SEA) |

**Typical expansion order for US-based B2B SaaS:**
1. UK and Canada (English-speaking, similar business culture, minimal localization)
2. Australia and Western Europe (Germany, France, Netherlands, Nordics)
3. Japan and Southeast Asia (Singapore as hub)
4. Latin America (Brazil and Mexico)
5. Middle East and Africa (UAE as hub)

### Localization Strategy

Localization is not translation. It's adapting your product, marketing, pricing, and go-to-market for local expectations.

#### Localization Tiers

| Tier | What to Localize | Investment | When to Do It |
|:---|:---|:---|:---|
| **Tier 1: Minimum viable** | Website in local language, local currency pricing, local payment methods, basic support in local business hours | $50K–$100K | When you have 20+ paying customers in the market (organic) |
| **Tier 2: Serious** | Product UI translated, local case studies, local content/SEO, in-market SDR or partner, local domain (e.g., .de, .co.jp) | $200K–$500K | When market contributes 5%+ of revenue |
| **Tier 3: Full** | Local entity, local team (sales + CS + marketing), local data residency, full product localization (including date/time/number formats, RTL support), local partnerships | $1M+ | When market contributes 15%+ of revenue or strategic priority |

### Compliance Considerations by Region

| Region | Key Regulations | What It Means For You |
|:---|:---|:---|
| **EU/EEA** | GDPR, ePrivacy Directive, Digital Services Act | Data processing agreements, cookie consent, right to erasure, data portability, potential DPO appointment, EU data residency may be required |
| **UK** | UK GDPR (post-Brexit), Data Protection Act 2018 | Similar to EU GDPR but separate regime. Need UK-specific privacy policy and potentially a UK representative. |
| **Germany** | GDPR + stricter local interpretation, works councils, Handelsgesetzbuch | German courts interpret GDPR more strictly. Works councils may need to approve software that monitors employee activity. Invoicing requirements are specific. |
| **Japan** | APPI (Act on Protection of Personal Information) | Cross-border data transfer restrictions (essentially need adequacy or consent). Privacy policy must be in Japanese. |
| **Brazil** | LGPD (Lei Geral de Proteção de Dados) | Similar framework to GDPR. Need a local DPO equivalent. Portuguese-language privacy disclosures. |
| **India** | DPDP Act 2023 | Data localization requirements for certain categories. Consent management. Still evolving — monitor for new rules. |
| **Middle East (UAE/KSA)** | UAE PDPL, KSA PDPL | Relatively new data protection laws. Data localization requirements in some sectors. Arabic disclosures may be required. |
| **Australia** | Privacy Act 1988, APPs | Cross-border disclosure requirements. Notifiable data breach scheme. Less strict than GDPR but real enforcement. |
| **Canada** | PIPEDA (federal), Quebec Law 25 | Quebec's Law 25 is GDPR-like. French language requirements in Quebec. Privacy impact assessments for certain processing. |

### Local Partnerships for International Expansion

In most non-English-speaking markets, local partners are your fastest path to revenue. They bring:
- Language and cultural fluency
- Existing customer relationships in your ICP
- Knowledge of local procurement processes
- Credibility that a foreign vendor entering the market doesn't have

**Types of local partners to recruit:**

| Partner Type | What They Do | How to Find Them |
|:---|:---|:---|
| **Local system integrators** | Implementation, customization, resale | Industry conferences, LinkedIn, ask your existing customers who they work with locally |
| **Local consulting firms** | Advisory, change management, resale | Big 4 local offices, boutique consultants who specialize in your category |
| **Local technology distributors** | Billing, support, resale (handle local payment, invoicing, support) | Cloud marketplace programs, distributor networks (Ingram Micro, TD Synnex) |
| **Local ISVs** | Integrate your product into their local solution | Check which local products your target customers are already using |

**Partnership deal structure for international:**
- Higher margins than domestic (typically 25–35% vs. 15–25%) to compensate for market development effort
- Exclusivity only for specific verticals or regions within the country, never country-wide exclusivity
- Minimum revenue commitments with annual review
- Co-investment in local marketing (MDF funded at higher rate than domestic)
