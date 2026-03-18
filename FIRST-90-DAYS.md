# First 90 Days: B2B SaaS Growth Playbook

A week-by-week action plan. Not frameworks — things to actually do.

---

## Week 1-2: Orient

Your only job right now is to absorb context. Don't propose changes yet. Learn how the business actually works.

### Who to talk to

- [ ] Schedule 1:1s with every founder/co-founder. Ask: "What do you think is the single biggest growth lever we're not pulling?" and "What have you already tried that didn't work?"
- [ ] Interview 5-10 recent customers. Ask: "How did you find us? What almost stopped you from signing up? What made you stay?" Record these calls (Grain, Fireflies, or Otter.ai).
- [ ] Sit with the sales team (if one exists) for a full day. Listen to calls. Read lost-deal notes in the CRM. Ask: "What objections come up every single time?"
- [ ] Talk to support/CS. Ask: "What do new users struggle with in the first week? What feature requests come up constantly?"
- [ ] Meet with engineering leads. Understand deployment cadence, what's feasible to ship in 2 weeks vs. 2 months, and any tracking/analytics debt.

### Data to pull and analyze

- [ ] Export full funnel data: visitor → signup → activation → paid conversion → expansion → churn. Use whatever exists (Mixpanel, Amplitude, PostHog, even raw SQL). Get at least 6 months of history.
- [ ] Pull cohort retention curves. Do users who sign up in January retain differently than March? Is retention improving or degrading?
- [ ] Get the revenue breakdown: new MRR, expansion MRR, contraction MRR, churned MRR for each of the last 6 months. If this doesn't exist in a dashboard, build it in a spreadsheet.
- [ ] Export the full customer list with signup date, plan, MRR, and source/channel if tracked. Sort by MRR descending — your top 20 customers will teach you more than your bottom 200.
- [ ] Pull Google Analytics / Search Console data. What pages drive traffic? What keywords rank? What's the organic trend line?

### Tools to set up

- [ ] Get admin access to: CRM (HubSpot/Salesforce), analytics (Mixpanel/Amplitude/PostHog), billing (Stripe/Chargebee), email (Customer.io/Intercom/SendGrid), ad accounts (Google/LinkedIn/Meta).
- [ ] Set up Hotjar or FullStory on the marketing site and key in-app pages. You need session recordings and heatmaps to see where users actually get stuck.
- [ ] Create a personal Notion/Google Doc called "Growth Context" — dump every insight, quote, and data point you find. This becomes your source of truth.

### Questions to ask the founders/CEO

- [ ] "What's our ICP? Who's our best customer and why?" — Get specific. Job title, company size, industry, use case.
- [ ] "What's our current CAC and LTV? How confident are you in those numbers?" — Most early-stage companies don't actually know.
- [ ] "What channels are working today? What have we tried and killed?" — Prevents you from re-running failed experiments without understanding why they failed.
- [ ] "What does the competitive landscape look like? Who do we lose deals to and why?" — Get the real answer, not the pitch deck answer.
- [ ] "What's the sales cycle length? Is it product-led, sales-led, or hybrid?" — This determines your entire strategy.

---

## Week 3-4: Diagnose

Now you have context. Time to find the bottleneck.

### Audit the current funnel

- [ ] Map the full funnel with actual conversion rates at each stage. Example: 10,000 visitors → 500 signups (5%) → 150 activated (30%) → 45 paid (30%) → 40 retained at month 3 (89%). Write these numbers on a whiteboard or in a doc. Stare at them.
- [ ] Identify the biggest drop-off. If 5% of visitors sign up but only 10% of those activate, activation is your bottleneck — not top-of-funnel. Don't pour traffic into a leaky bucket.
- [ ] Define "activation" if it isn't defined. What action correlates with retention? For Slack it was "2,000 messages sent." For Dropbox it was "1 file in 1 folder on 1 device." Find your equivalent by comparing retained vs. churned users' first-week behavior.
- [ ] Analyze time-to-value. How long does it take a new user to reach their "aha moment"? If it's more than a few minutes for a PLG product, that's a problem.
- [ ] Segment conversion rates by channel. Organic search signups might convert to paid at 8% while paid ad signups convert at 2%. This changes where you invest.

### Baseline your metrics

- [ ] Document these numbers in a "Growth Dashboard" (Google Sheet is fine to start): MRR, MRR growth rate, signup volume, activation rate, trial-to-paid conversion, net revenue retention, CAC by channel, payback period.
- [ ] Set up weekly automated reports if they don't exist. Use Metabase, Looker, or even a scheduled SQL query that emails a CSV. You need to see these numbers every Monday without asking anyone.
- [ ] Calculate your quick ratio (new MRR + expansion MRR) / (contraction MRR + churned MRR). Above 4 is great. Below 2 means you have a retention problem that growth can't outrun.

### Competitive audit

- [ ] Sign up for every competitor's free trial. Go through their onboarding. Screenshot everything. Time how long it takes to reach value. Document what they do better and worse.
- [ ] Run competitors through SimilarWeb or Ahrefs. Where does their traffic come from? What keywords do they rank for that you don't? What content are they producing?
- [ ] Review competitor pricing pages on the Wayback Machine. How has their pricing evolved? What plans do they offer that you don't?
- [ ] Check G2, Capterra, and TrustRadius reviews for competitors. What do their customers complain about? Those complaints are your positioning opportunities.
- [ ] Audit competitor email sequences by signing up with a burner email and saving every message for 30 days. Tools like MailCharts can help.

### Synthesize findings

- [ ] Write a 2-page "Growth Diagnostic" doc. State the biggest bottleneck, supporting data, and your proposed focus for the next 60 days. Share with founders for alignment before you start executing.
- [ ] Rank opportunities by impact (how much will this move the needle?) and effort (how long will it take?). Use a simple 2x2 matrix. High impact / low effort goes first.

---

## Week 5-6: Quick Wins

Ship things that work across almost every B2B SaaS. These aren't creative bets — they're proven patterns you're implementing.

### Onboarding email sequence

- [ ] Write a 7-email onboarding sequence triggered by signup. Day 0: welcome + single CTA to complete setup. Day 1: tip on the core feature. Day 3: social proof (case study or testimonial). Day 5: "need help?" from a real person. Day 7: value reminder + upgrade prompt. Day 10: breakup email if inactive. Day 14: final nudge with an incentive (extended trial, discount, concierge onboarding).
- [ ] Set up behavioral triggers, not just time-based. If a user completes activation, skip the "need help?" email and send a "here's what power users do next" email instead. Use Customer.io, Intercom, or HubSpot workflows.
- [ ] A/B test subject lines on the Day 0 and Day 3 emails first — those have the highest volume and will reach significance fastest.

### Pricing page optimization

- [ ] Add a pricing FAQ section if one doesn't exist. Address the top 5 objections from your sales/CS conversations. "Is there a free trial?" "Can I cancel anytime?" "What happens to my data if I cancel?" "Do you offer annual discounts?"
- [ ] Add social proof to the pricing page: logos, testimonial quotes, "X companies trust us" counter. The pricing page is the highest-intent page on your site — treat it accordingly.
- [ ] Test adding a "most popular" badge to your target plan. This anchoring effect consistently lifts conversion by 5-15%.
- [ ] If you don't have annual pricing, add it with a 15-20% discount. Annual plans reduce churn mechanically and improve cash flow.

### Trial-to-paid nudges

- [ ] Implement in-app upgrade prompts that trigger when users hit feature limits or usage caps — not on a timer. "You've used 4 of 5 free projects. Upgrade to unlock unlimited projects" converts better than "Your trial ends in 3 days."
- [ ] Add a persistent but non-annoying banner showing trial status and days remaining. Link directly to checkout, not the pricing page.
- [ ] Send a "trial ending" email at 3 days and 1 day before expiration with a clear CTA. Include a summary of what they've built/done in the product — loss aversion is powerful.

### Other quick wins

- [ ] Fix the signup form. Remove every field that isn't strictly necessary. Every field you remove increases conversion. Name + email + password is the max. Company name and phone number can come later.
- [ ] Add exit-intent popups on high-traffic pages (homepage, pricing, features) offering a lead magnet or demo booking. Use Sumo, OptinMonster, or build it yourself.
- [ ] Set up Calendly or Chili Piper for inbound demo scheduling. Remove friction from the "talk to sales" flow. Every hour of lag between request and meeting costs you deals.
- [ ] If you have a blog with traffic but no conversion mechanism, add content upgrades (PDF guides, templates, checklists) gated behind email capture. Use them to build a nurture list.

---

## Week 7-8: Build the Engine

Quick wins buy you credibility. Now build the system that compounds.

### Growth meeting cadence

- [ ] Establish a weekly 30-minute growth meeting. Attendees: you, product lead, engineering lead (or whoever builds experiments), and the founder/CEO. Agenda: metrics review (10 min), experiment results (10 min), upcoming experiments (10 min). No status updates — async those in Slack.
- [ ] Create a shared experiment tracker. Columns: hypothesis, metric, status (backlog / in-progress / analyzing / shipped / killed), start date, end date, result, learnings. Google Sheet works. Notion works. Airtable works. Pick one and use it.
- [ ] Set up a monthly growth review for the broader team. 30 minutes. Cover: key metrics trend, top 3 learnings from experiments, upcoming priorities. This builds organizational buy-in.

### Experiment backlog

- [ ] Brainstorm 20-30 experiment ideas. Sources: customer interviews, competitor analysis, team suggestions, your own experience, growth communities (Reforge, Lenny's Newsletter, GrowthHackers). Quantity over quality at this stage.
- [ ] Score each experiment using ICE: Impact (1-10), Confidence (1-10), Ease (1-10). Average the scores. Sort descending. This is your prioritized backlog.
- [ ] Commit to running 2-3 experiments per week. Not all need engineering — many are copy changes, email tests, or landing page variants you can ship with Webflow, Unbounce, or your email tool.
- [ ] Define your minimum sample size and significance threshold before you run anything. Use Evan Miller's sample size calculator. Most B2B SaaS experiments need 2-4 weeks to reach significance at reasonable traffic levels. Accept this — don't call experiments early.

### Hiring your first SDR (if applicable)

- [ ] Write the job description focused on outcomes, not experience. "You'll book 30 qualified demos per month" is better than "3+ years of SaaS sales experience." Look for curiosity, coachability, and writing ability over pedigree.
- [ ] Build the outbound playbook before you hire. Write the email sequences, define the ICP, build the target account list (Apollo, ZoomInfo, or LinkedIn Sales Navigator). Your SDR should execute a playbook, not create one from scratch.
- [ ] Set up the SDR tech stack: Apollo or Outreach for sequencing, LinkedIn Sales Navigator for prospecting, Gong or Chorus for call recording, Calendly for booking.
- [ ] Plan a 2-week onboarding: week 1 is product training + shadowing existing sales calls, week 2 is supervised outreach with daily coaching.

### Attribution and analytics

- [ ] Implement UTM tracking on every link you control: ads, emails, social posts, partner links. Use a UTM builder template to enforce consistency. Store UTMs in your CRM on the contact record.
- [ ] Set up proper conversion tracking: Google Ads conversion pixel, LinkedIn Insight Tag, Meta pixel — even if you're not running ads yet. Historical data is valuable when you start.
- [ ] Define your attribution model. For most early-stage B2B SaaS, first-touch attribution is fine to start. Last-touch attribution undervalues content and overvalues direct/branded search. Don't overthink this — pick one and be consistent.
- [ ] Build a channel performance dashboard: spend, leads, MQLs, opportunities, closed-won, CAC by channel. Update monthly. This is how you decide where to invest more and where to cut.
- [ ] Set up event tracking for key product actions if it's missing: signup, activation event, feature usage, upgrade, invite sent. Use Segment if you can, or fire events directly to your analytics tool. You can't optimize what you don't measure.

---

## Week 9-10: Execute

You've diagnosed, shipped quick wins, and built the system. Now run real experiments.

### First major experiments

- [ ] Run a landing page test targeting your highest-traffic acquisition page. Test the headline, hero image, and primary CTA simultaneously (not individually — you don't have enough traffic for sequential single-variable tests). Use Google Optimize (free), VWO, or Optimizely.
- [ ] Launch a referral or invite flow if one doesn't exist. Keep it simple: "Invite a teammate, both get [incentive]." B2B referrals work best when the incentive is product-related (extra seats, extended trial, feature unlock) rather than cash.
- [ ] Test a new pricing tier or packaging change. If you only have 2 plans, add a third. If you don't have a free tier, test a limited free plan. If you have a free tier with low conversion, test restricting it. Use a price testing tool like Corrily or run it as an A/B test with a flag.
- [ ] Experiment with your activation flow. Identify the 3 steps between signup and "aha moment" and try to remove one, automate one, or simplify one. Measure impact on 7-day retention.
- [ ] Run an outbound campaign to 200-500 targeted prospects if you haven't already. Test 2 different value props in the email copy. Measure open rate, reply rate, and meetings booked. A good cold email gets 40%+ open rate and 5%+ reply rate.

### Standing up the content engine

- [ ] Identify your top 10 target keywords using Ahrefs, SEMrush, or even Google's "People also ask" and autocomplete. Focus on bottom-of-funnel keywords first: "[competitor] alternative," "[category] software," "best [tool] for [use case]." These have buying intent.
- [ ] Write (or commission) 4 high-quality articles targeting those keywords. Each should be 1,500-2,500 words, include original data or insights, and have a clear CTA. Don't publish SEO filler — publish things your ICP would actually bookmark.
- [ ] Create 1-2 "comparison" pages: "Us vs. [Competitor]." These rank well, convert well, and help your sales team. Be honest about where competitors are better — it builds trust.
- [ ] Set up a content calendar. Commit to a sustainable cadence — 2 posts per month is better than 8 posts in one month then nothing. Use a freelance writer from Superpath, Verblio, or your network for scale.
- [ ] Repurpose every piece of content: blog post becomes a LinkedIn post becomes a Twitter thread becomes a newsletter section becomes a sales enablement one-pager. One insight, five formats.

### Partner/affiliate program foundation

- [ ] Identify 10-15 potential integration partners (tools your customers already use alongside yours). Reach out to their partnerships team with a specific co-marketing proposal, not a vague "let's partner" email.
- [ ] Set up a basic affiliate program using PartnerStack, FirstPromoter, or Rewardful. Offer 20-30% recurring commission for the first year. Recruit your happiest customers, relevant bloggers, and consultants in your space.
- [ ] Build an integrations page on your website even if you only have 2-3 integrations. This page ranks well for "[your category] + [partner category] integration" searches and signals ecosystem maturity to buyers.

---

## Week 11-12: Report & Iterate

Show what you've done, what you've learned, and where you're going.

### Present results to leadership

- [ ] Write a "First 90 Days" report. Structure: context (what you inherited), actions (what you did), results (what happened), learnings (what you now know), and plan (what's next). Keep it under 5 pages. Use charts, not tables — trends matter more than individual data points.
- [ ] Lead with the metrics that moved. Even if the absolute numbers are small, show the trajectory. "Trial-to-paid conversion improved from 8% to 12% (+50%)" tells a story.
- [ ] Be honest about what didn't work. Every failed experiment has a learning. "We tested gating the product behind a demo request and conversion dropped 40% — confirmed that our users want self-serve access" is valuable.
- [ ] Quantify the pipeline you've built, not just the results you've shipped. "We have 15 experiments in the backlog, an SDR ramping to full capacity in 3 weeks, and a content engine producing 2 posts/month" shows momentum.

### What a good growth review looks like

- [ ] Present the growth model: where revenue comes from today, where it will come from in 6 months, and what needs to be true for that to happen. Use a simple spreadsheet model, not a 50-tab financial forecast.
- [ ] Review each active channel: what's working, what's not, where you're investing next. For each channel, state: current CAC, volume, trend, and planned experiments.
- [ ] Share the experiment velocity: how many experiments you ran, win rate, and average impact of winners. Aim for 2-4 experiments per week with a 20-30% win rate. If everything is winning, you're not being bold enough.
- [ ] Highlight organizational blockers. If experiments are stuck waiting for engineering, say so. If you need budget for a tool, make the case. This meeting is your venue to ask for what you need.

### Plan the next quarter

- [ ] Set 2-3 growth OKRs for Q2. Example: "Increase trial-to-paid conversion from 12% to 18%" or "Grow inbound signups from 500/month to 800/month." Each OKR should have 3-4 key results with specific targets.
- [ ] Prioritize the experiment backlog for the quarter. Group experiments by theme (activation, acquisition, monetization, retention) and allocate roughly: 50% to your biggest bottleneck, 30% to your second, 20% to exploratory bets.
- [ ] Build the hiring plan if needed. Common next hires after the first growth person: content marketer, growth engineer, demand gen specialist. Justify each hire with projected ROI.
- [ ] Write a 1-page "Growth Strategy" doc that any new team member can read and understand in 10 minutes. It should answer: who is our customer, how do they find us, what makes them buy, what makes them stay, and what are we betting on next.
- [ ] Schedule a retrospective on your own process. What took too long? What would you skip next time? What do you wish you'd done in week 1? Write it down — you'll reference it when you hire your next growth person.

---

## Recommended tools by category

**Analytics**: Mixpanel, Amplitude, PostHog (open source), Google Analytics 4
**CRM**: HubSpot (free tier is solid for early stage), Salesforce (if you have a sales team > 5)
**Email/lifecycle**: Customer.io, Intercom, HubSpot, Loops
**Experimentation**: Google Optimize, VWO, Optimizely, Statsig, LaunchDarkly (feature flags)
**SEO**: Ahrefs, SEMrush, Clearscope (content optimization), SurferSEO
**Outbound**: Apollo, Outreach, SalesLoft, LinkedIn Sales Navigator
**Session recording**: Hotjar, FullStory, PostHog
**Attribution**: HubSpot, Segment, Ruler Analytics, Dreamdata
**Content**: Superpath (freelance writers), Verblio, Jasper (AI drafts), Webflow (landing pages)
**Partnerships**: PartnerStack, FirstPromoter, Rewardful
**Scheduling**: Calendly, Chili Piper, SavvyCal
**Surveys**: Typeform, SurveyMonkey, in-app via Intercom or Pendo
