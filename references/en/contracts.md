# Part 4: Contract Template System

> **Disclaimer:** These templates are for educational and reference purposes only. They do not constitute legal advice. Contract law varies by jurisdiction, and the consequences of poorly drafted agreements can be severe. Have a qualified attorney review any contract before you sign it. This is especially true for IP, liability, and data processing clauses.

---

## Contract System Overview

| Document | Description |
|:---|:---|
| **SOR** (Statement of Requirements) | Written by client, describes business goals and requirements |
| **SOW** (Statement of Work) | Written by vendor, defines scope, deliverables, timeline |
| **MSA** (Master Service Agreement) | Legal master contract, defines general terms |
| **PCR** (Project Change Request) | Manages scope changes during a project |
| **Quote** | Fee structure, payment terms, pricing options |
| **NDA** (Non-Disclosure Agreement) | Protects confidential information shared between parties |
| **SaaS Agreement** | Subscription terms for hosted software services |
| **Partner/Reseller Agreement** | Governs channel partnerships and resale relationships |

---

## 1. Statement of Requirements (SOR) Template

**Acme Corp AI Agent Service Requirements**
- Document ID: SOR-20250115-001
- Version: V1.0
- Date: 2025-01-15
- Author: Jane Chen, VP of Customer Operations
- Reviewers: IT Director, Legal, Finance

### 1. Project Overview

**1.1 Background:**
Acme Corp currently handles 12,000 customer support tickets per month across email and chat. Average first-response time is 4.7 minutes. 62% of tickets are repetitive (password resets, order status, return policies). The support team of 15 agents costs $1.2M annually. We need an AI agent to handle Tier 1 queries, freeing human agents for complex issues.

**1.2 Objectives:**

Write objectives using SMART criteria — Specific, Measurable, Achievable, Relevant, Time-bound:

| Objective | Metric | Target | Deadline |
|:---|:---|:---|:---|
| Reduce average first-response time | Seconds from ticket creation to first reply | < 30 seconds for AI-handled tickets | 90 days post go-live |
| Automate Tier 1 ticket resolution | % of tickets fully resolved without human | ≥ 60% | 90 days post go-live |
| Maintain customer satisfaction | CSAT score on AI-handled tickets | ≥ 4.2 / 5.0 | Ongoing |
| Reduce support costs | Annual support spend | 30% reduction ($360K savings) | Year 1 |

**1.3 Scope:**

| In Scope | Out of Scope |
|:---|:---|
| AI agent for chat and email channels | Phone/voice support |
| English and Spanish language support | Other languages |
| Integration with Zendesk and Salesforce | Custom CRM builds |
| Knowledge base ingestion from existing docs | Content creation for knowledge base |
| Dashboard for agent performance metrics | BI tool integration beyond API |

### 2. Requirements Detail

**2.1 Functional Requirements**

Write each requirement as a user story with acceptance criteria:

**FR-001: Natural Language Understanding & Intent Recognition**
- *As a* customer, *I want to* describe my issue in plain language *so that* the AI agent understands and routes my request correctly.
- Acceptance Criteria:
  - Intent classification accuracy ≥ 95% on the top 20 intent categories
  - Entity extraction accuracy ≥ 90% (order numbers, dates, product names)
  - Handles multi-intent messages (e.g., "Where's my order and can I change the address?")
  - Graceful fallback to human agent when confidence score < 0.7

**FR-002: Conversation Context Management**
- *As a* customer, *I want to* continue a conversation across messages *so that* I don't repeat myself.
- Acceptance Criteria:
  - Maintains context for at least 20 conversation turns
  - References previous tickets from same customer within 30-day window
  - Handles mid-conversation topic switches without losing context

**FR-003: Knowledge Base Integration**
- *As a* support manager, *I want the* AI agent to pull answers from our knowledge base *so that* responses are accurate and consistent.
- Acceptance Criteria:
  - Ingests existing Zendesk Help Center articles (approx. 500 articles)
  - Updates within 1 hour of article changes
  - Cites source article in internal notes for audit trail
  - Handles conflicting information by using most recently updated article

**2.2 Non-Functional Requirements**

| Category | Requirement | Metric |
|:---|:---|:---|
| **Performance** | Average response latency | < 1 second (p95) |
| **Performance** | Concurrent conversations | ≥ 500 simultaneous sessions |
| **Performance** | Throughput | ≥ 100 queries per second |
| **Security** | Transport encryption | TLS 1.3 minimum |
| **Security** | Data at rest | AES-256 encryption |
| **Security** | PII handling | Automatic detection and masking in logs |
| **Security** | Authentication | OAuth 2.0 / SAML 2.0 SSO |
| **Availability** | Core service uptime | ≥ 99.9% (measured monthly) |
| **Availability** | Planned maintenance window | Max 4 hours/month, off-peak only |
| **Compliance** | Data residency | US data centers only |
| **Compliance** | Regulations | SOC 2 Type II, GDPR, CCPA |

### 3. Existing Systems & Environment

| System | Version | Integration Type |
|:---|:---|:---|
| Zendesk Support | Enterprise plan | REST API (bi-directional) |
| Salesforce CRM | Lightning Enterprise | REST API (read customer data) |
| AWS infrastructure | us-east-1 | VPC peering or PrivateLink |
| Okta SSO | N/A | SAML 2.0 |
| Snowflake data warehouse | N/A | Write analytics events via Kafka |

### 4. Delivery Requirements

| Deliverable | Phase | Acceptance Method |
|:---|:---|:---|
| System architecture document | Design | Reviewed and approved by IT Director |
| Working AI agent (chat channel) | Development | UAT with 50 test conversations, ≥ 90% correct |
| Working AI agent (email channel) | Development | UAT with 100 test emails, ≥ 85% correct |
| Zendesk + Salesforce integration | Development | End-to-end test with production-mirrored data |
| Admin dashboard | Development | Functional walkthrough with stakeholders |
| Runbook and operations documentation | Deployment | Reviewed by ops team, covers all alert scenarios |
| Knowledge transfer sessions (3x) | Deployment | Attendance by designated team, recorded |

### 5. Budget & Constraints
- Budget ceiling: $150,000 for implementation, $3,000/month ongoing
- Timeline constraint: Must be in production before Q3 FY2025
- Legal constraint: No customer PII may leave US data centers
- Vendor constraint: Vendor must have SOC 2 Type II certification

### Writing Effective Requirements — Guidance

**Use SMART criteria for every objective:**
- **Specific:** "Reduce Tier 1 ticket volume" not "Improve support"
- **Measurable:** Include a number. If you can't measure it, you can't accept it.
- **Achievable:** Talk to potential vendors before setting targets
- **Relevant:** Every requirement should trace to a business objective
- **Time-bound:** "Within 90 days of go-live" not "eventually"

**User story format:**
```
As a [role], I want to [action] so that [business value].
```

**Acceptance criteria patterns:**
- **Given/When/Then:** "Given a customer asks about order status, when they provide an order number, then the system returns the current status within 1 second."
- **Rule-based:** "The system SHALL [do X] when [condition Y] is true."
- **Boundary conditions:** Always specify what happens at the edges — what if input is missing, malformed, or exceeds limits?

**Common SOR mistakes to avoid:**
- Describing solutions instead of problems (let the vendor propose solutions)
- Omitting non-functional requirements (performance, security, availability)
- Failing to specify acceptance criteria (leads to disputes during UAT)
- Not listing existing systems (vendor discovers integration complexity late, costs go up)

---

## 2. Statement of Work (SOW) Template

**NovaMind Solutions — AI Agent Implementation SOW**
- Project: Acme Corp AI Customer Support Agent
- SOW ID: SOW-20250201-001
- Related SOR: SOR-20250115-001
- Effective Date: 2025-02-01
- Prepared By: Alex Rivera, Solutions Architect, NovaMind Solutions

### 1. Scope

**1.1 Objectives**
NovaMind will design, develop, and deploy an AI-powered customer support agent for Acme Corp that handles Tier 1 support queries across chat and email channels. The system will integrate with Acme's existing Zendesk and Salesforce environments.

**1.2 Scope Overview**

| Work Area | Description |
|:---|:---|
| NLU Model Configuration | Fine-tune intent classification and entity extraction for Acme's domain |
| Conversation Engine | Build multi-turn dialogue flows for top 20 support intents |
| Knowledge Base Pipeline | Ingest, index, and keep current Acme's Zendesk Help Center |
| Channel Integration | Zendesk chat widget and email processing |
| CRM Integration | Read customer context from Salesforce |
| Analytics Dashboard | Real-time metrics on AI agent performance |
| Testing & QA | Unit, integration, UAT, and load testing |
| Deployment & Handover | Production deployment, runbook, knowledge transfer |

**1.3 Exclusions** (What is NOT included)

This section is critical. Disputes almost always stem from ambiguity about what's out of scope.

| Excluded Item | Rationale |
|:---|:---|
| Phone/voice channel support | Not in SOR; can be added via PCR |
| Knowledge base content creation | Acme's responsibility; NovaMind ingests existing content |
| Ongoing model retraining after go-live | Covered under separate support agreement |
| Hardware procurement | Acme provides AWS infrastructure |
| Languages beyond English and Spanish | Can be added via PCR at additional cost |
| Custom BI integrations beyond dashboard API | Third-party BI tool setup is Acme's responsibility |
| Regulatory compliance filings | Acme's legal team handles; NovaMind provides documentation |

### 2. Methodology & Activities

**2.1 Methodology:**
Agile (Scrum) with 2-week sprints. Waterfall gates for phase transitions (each phase requires client sign-off before proceeding).

**2.2 Phases:**

**Phase 1: Discovery & Design (Weeks 1–4)**
- Stakeholder interviews and requirements clarification
- Technical architecture design
- Data flow and integration design
- Intent taxonomy and conversation flow design
- Security review and threat modeling
- Deliverable: Architecture Design Document (ADD), signed off by Acme IT

**Phase 2: Development & Integration (Weeks 5–14)**
- Sprint 1–2: NLU model configuration, knowledge base pipeline
- Sprint 3–4: Conversation engine, Zendesk integration
- Sprint 5: Salesforce integration, analytics dashboard
- Bi-weekly demos to Acme stakeholders
- Deliverable: Working system in staging environment

**Phase 3: Testing & UAT (Weeks 15–17)**
- Integration testing against Acme's staging environment
- Load testing (simulate 500 concurrent sessions)
- UAT: Acme support team runs 200 test conversations
- Bug fixes and tuning
- Deliverable: UAT sign-off document

**Phase 4: Deployment & Handover (Weeks 18–20)**
- Production deployment (blue-green, zero downtime)
- 2-week hypercare period with NovaMind on standby
- 3 knowledge transfer sessions (recorded)
- Deliverable: Runbook, admin guide, KT recordings

### 3. Deliverables & Acceptance

| # | Deliverable | Phase | Acceptance Criteria | Accept/Reject Deadline |
|:---|:---|:---|:---|:---|
| D1 | Architecture Design Document | 1 | Reviewed by Acme IT, all comments resolved | 5 business days after delivery |
| D2 | Working AI Agent (staging) | 2 | Passes 50 scripted test conversations with ≥ 90% accuracy | 5 business days |
| D3 | Integration test results | 3 | All critical and high-severity test cases pass | 3 business days |
| D4 | UAT sign-off | 3 | Acme runs 200 conversations, ≥ 85% resolved correctly | 10 business days |
| D5 | Production deployment | 4 | System live, monitoring active, no P1 incidents for 48 hours | 3 business days |
| D6 | Runbook + KT sessions | 4 | Runbook covers all alert scenarios; KT attended by designated staff | 5 business days |

**Acceptance process:** Acme has the specified number of business days to review each deliverable. If Acme does not respond within the deadline, the deliverable is deemed accepted. Rejection must include specific, written reasons referencing acceptance criteria.

### 4. Timeline

| Phase | Start | End | Duration | Key Milestone |
|:---|:---|:---|:---|:---|
| Discovery & Design | Week 1 | Week 4 | 4 weeks | ADD sign-off |
| Development & Integration | Week 5 | Week 14 | 10 weeks | Staging demo |
| Testing & UAT | Week 15 | Week 17 | 3 weeks | UAT sign-off |
| Deployment & Handover | Week 18 | Week 20 | 3 weeks | Go-live |
| **Total** | | | **20 weeks** | |

### 5. Team & Governance

**NovaMind Team:**

| Role | Name | Allocation | Responsibilities |
|:---|:---|:---|:---|
| Project Manager | Sarah Kim | 50% | Schedule, budget, status reporting, escalation |
| Solutions Architect | Alex Rivera | 30% | Architecture, technical decisions, integration design |
| ML Engineer | Jordan Lee | 100% | NLU model, knowledge base pipeline |
| Backend Developer | Priya Patel | 100% | APIs, conversation engine, CRM integration |
| Frontend Developer | Marcus Chen | 50% | Dashboard, chat widget customization |
| QA Engineer | Dana Rossi | 100% (Phase 3–4) | Test planning, execution, automation |

**Acme Team (Client Responsibilities):**

| Role | Responsibilities |
|:---|:---|
| Project Sponsor | Final decisions, budget approval, escalation resolution |
| Project Manager | Day-to-day coordination, acceptance decisions |
| IT Lead | AWS access, network config, security reviews |
| Support Lead | UAT execution, intent taxonomy review, KT attendance |
| Legal | DPA review, compliance sign-off |

**Communication cadence:**
- Weekly status meeting (30 min, every Tuesday 10 AM ET)
- Bi-weekly sprint demo (60 min, end of each sprint)
- Monthly steering committee (60 min, project sponsor + NovaMind director)
- Slack channel for async communication (response within 4 business hours)
- Status report delivered via email every Friday by 5 PM ET

**Escalation path:**
1. Project Manager → Project Manager (resolve within 2 business days)
2. Solutions Architect → IT Lead (technical disputes, 3 business days)
3. NovaMind Director → Project Sponsor (budget/scope disputes, 5 business days)

### 6. Fees & Payment
See Quote QT-20250201-001 (attached).

### 7. Assumptions & Dependencies

**Assumptions:**
- Acme provides AWS access within 5 business days of contract signing
- Zendesk and Salesforce sandbox environments available from Day 1
- Acme's knowledge base has at least 300 articles in publishable state
- Acme provides 500 sample support tickets for model training within Week 2
- Acme stakeholders are available for scheduled meetings and reviews
- No major changes to Acme's Zendesk or Salesforce configuration during the project

**Dependencies:**
- Phase 2 cannot start until ADD is signed off (Phase 1 deliverable)
- Salesforce integration requires Acme to provision API credentials
- Production deployment requires Acme's change management board approval (Acme to schedule)

**If assumptions are broken:** Vendor will issue a PCR documenting timeline and cost impact. Client is responsible for delays caused by broken assumptions (e.g., late access provisioning does not compress the vendor's delivery schedule).

### 8. Signatures

| | Name | Title | Signature | Date |
|:---|:---|:---|:---|:---|
| **Vendor** | Maria Gonzalez | CEO, NovaMind Solutions | _______________ | __________ |
| **Client** | David Park | VP Operations, Acme Corp | _______________ | __________ |

### Scope Management — Guidance

**Defining scope boundaries:**
- Write the exclusions list before the inclusions list. It forces you to think about what people will assume is included.
- If a requirement is ambiguous, it's in scope. Tighten your language.
- Use the "newspaper test": if you had to explain to a journalist what the vendor promised to deliver, would the SOW make it clear?

**Handling scope creep:**
Scope creep kills projects. It happens when:
1. The client asks for "small" additions verbally, and the vendor does them to maintain goodwill
2. Requirements were ambiguous, and the client's interpretation is broader than the vendor's
3. Stakeholders who weren't involved in scoping surface new requirements mid-project

**How to prevent it:**
- Every request that isn't explicitly in the SOW goes through a PCR (see Section 4)
- The PM has authority to say "yes, we can do that — here's the PCR with cost and timeline impact"
- Never agree to scope changes in meetings. Always follow up in writing.
- Maintain a "parking lot" list of deferred requests for a future phase

**Change management process:**
1. Request → PCR submitted (see PCR template)
2. Impact assessment → Vendor estimates cost, timeline, risk impact (3 business days)
3. Review → Both PMs review
4. Approve/Reject → Both PMs sign (or escalate to sponsors)
5. Execute → Amend SOW, update timeline, adjust invoicing

**Realistic timeline estimation:**
- Add 20% buffer to every engineering estimate. Engineers are optimistic.
- Account for dependencies outside your control (client reviews, third-party APIs, procurement)
- If the client says "we need this in 6 weeks" but the work takes 10, say 10. Compressing timelines doesn't compress the work — it compresses the quality.
- Phase gates (requiring sign-off before proceeding) prevent wasted work but add calendar time. Plan for 3–5 business days per review cycle.

---

## 3. MSA Core Clauses

The Master Service Agreement is the legal backbone. Individual SOWs, quotes, and PCRs operate under the MSA. This section provides clause-by-clause guidance with example language.

### 3.1 Services

**Purpose:** Define how work is structured and how SOWs relate to the MSA.

**Example clause:**
> Vendor shall provide the Services described in one or more Statements of Work ("SOW") executed by both parties. Each SOW is incorporated into and governed by this Agreement. In the event of a conflict between an SOW and this Agreement, the terms of this Agreement shall prevail unless the SOW explicitly states that it supersedes a specific MSA provision.

**Key points:**
- The MSA sets the defaults; SOWs can override specific terms only if they say so explicitly
- Number your SOWs and reference them by ID
- Include a clause stating that no work is authorized until an SOW is signed by both parties

### 3.2 Payment Terms

**Purpose:** Define when and how the vendor gets paid, and what happens when they don't.

**Example clause:**
> Client shall pay undisputed invoices within thirty (30) calendar days of receipt ("Net 30"). Invoices shall be submitted upon completion of milestones defined in the applicable SOW. Late payments shall accrue interest at the lesser of 1.5% per month or the maximum rate permitted by law. If payment is more than sixty (60) days overdue, Vendor may suspend Services upon fifteen (15) days' written notice.

**Common structures:**

| Structure | When to Use |
|:---|:---|
| Time & Materials (T&M) | Scope is unclear, discovery/R&D work |
| Fixed Price | Scope is well-defined, both parties want cost certainty |
| Milestone-based | Fixed price broken into payments at defined checkpoints |
| Retainer | Ongoing advisory, maintenance, fractional roles |
| Hybrid | Fixed price for core scope, T&M for change requests |

**Expense policy:**
> Pre-approved, reasonable out-of-pocket expenses (travel, hosting, third-party tools) are reimbursable at cost with receipts. Expenses exceeding $500 per item require prior written approval. Travel requires economy class; lodging at or below GSA per diem rates.

### 3.3 Intellectual Property

This is the clause that starts the most fights. Get it right.

**IP Assignment (client owns everything):**
> All Work Product created by Vendor specifically for Client under this Agreement shall be considered "work made for hire" to the extent permitted by law. To the extent any Work Product does not qualify as work made for hire, Vendor hereby irrevocably assigns to Client all right, title, and interest in such Work Product, including all intellectual property rights therein. Vendor shall execute any documents reasonably necessary to perfect Client's ownership.

**IP License (vendor retains ownership, client gets a license):**
> Vendor retains all right, title, and interest in the Work Product. Vendor grants Client a non-exclusive, perpetual, irrevocable, royalty-free, worldwide license to use, modify, and sublicense the Work Product for Client's internal business purposes.

**When to use each:**

| Model | Use When | Risk to Client | Risk to Vendor |
|:---|:---|:---|:---|
| **Assignment** | Client is paying for custom, bespoke development; competitive advantage matters | Low — client owns it | Vendor can't reuse for other clients |
| **License** | Vendor is adapting their existing platform/tools; client benefits from ongoing improvements | Vendor could license to competitors; dependency on vendor | Low — vendor keeps their IP |
| **Hybrid** | Most common. Custom work → assigned; vendor's pre-existing tools/frameworks → licensed | Moderate — need clear line between custom and pre-existing | Moderate — need to clearly define pre-existing IP upfront |

**Pre-existing IP carve-out (essential in assignment deals):**
> Notwithstanding the foregoing, Vendor retains all rights in Vendor's pre-existing intellectual property ("Vendor IP"), which is listed in Exhibit B. To the extent any Vendor IP is incorporated into the Work Product, Vendor grants Client a non-exclusive, perpetual, irrevocable, royalty-free license to use such Vendor IP solely as embedded in the Work Product. Vendor shall identify any Vendor IP incorporated into Work Product before delivery.

**Open source disclosure:**
> Vendor shall disclose all open-source components incorporated into the Work Product, including license type, prior to delivery. Vendor shall not incorporate any open-source component with a copyleft license (e.g., GPL, AGPL) without Client's prior written consent.

### 3.4 Confidentiality

**Example clause:**
> "Confidential Information" means any non-public information disclosed by either party ("Disclosing Party") to the other ("Receiving Party") in connection with this Agreement, whether disclosed orally, in writing, or by inspection, including but not limited to: technical data, trade secrets, business plans, customer lists, pricing, financial information, and the terms of this Agreement. The Receiving Party shall: (a) use Confidential Information solely for purposes of this Agreement; (b) not disclose it to any third party without prior written consent, except to employees, contractors, and advisors who need to know and are bound by confidentiality obligations at least as protective as these; and (c) protect it with at least the same degree of care it uses for its own confidential information, but no less than reasonable care. These obligations survive for three (3) years after termination of this Agreement.

**Standard exclusions:**
> Confidential Information does not include information that: (a) is or becomes publicly available through no fault of the Receiving Party; (b) was known to the Receiving Party before disclosure; (c) is independently developed by the Receiving Party without reference to the Confidential Information; or (d) is rightfully received from a third party without restriction.

### 3.5 Data Protection & Security

**Data ownership:**
> Client Data (defined as any data provided by Client or collected from Client's end users in the course of providing Services) is and remains the property of Client. Vendor shall not use Client Data for any purpose other than providing the Services. Upon termination, Vendor shall return or destroy all Client Data within thirty (30) days and certify destruction in writing.

**Data Processing Addendum (DPA) — GDPR/CCPA essentials:**

If the vendor processes personal data on behalf of the client, you need a DPA. Key provisions:

| DPA Provision | What It Covers |
|:---|:---|
| **Roles** | Client is the data controller; Vendor is the data processor |
| **Processing instructions** | Vendor processes data only on documented instructions from Client |
| **Sub-processors** | Vendor must list sub-processors; Client can object to new ones with 30 days' notice |
| **Security measures** | Vendor implements TOMs (Technical and Organizational Measures) — list them specifically |
| **Breach notification** | Vendor notifies Client within 72 hours of discovering a data breach (GDPR requirement) |
| **Data subject rights** | Vendor assists Client in responding to data subject access/deletion requests |
| **Data transfers** | If data crosses borders, specify the legal mechanism (SCCs, adequacy decisions, etc.) |
| **Audit rights** | Client or its auditor may audit Vendor's data processing activities (see Section 3.10) |
| **Deletion/return** | Upon termination, Vendor deletes all personal data within 30 days |

**CCPA-specific additions:**
> Vendor shall not sell, share, or use Client's personal information for any purpose other than providing the Services. Vendor shall not combine Client's personal information with personal information received from other sources, except as permitted by the CCPA. Vendor certifies that it understands and will comply with these restrictions.

**Security requirements:**
> Vendor shall maintain information security controls consistent with SOC 2 Type II standards, including but not limited to: access controls (role-based, MFA), encryption in transit (TLS 1.3) and at rest (AES-256), logging and monitoring, vulnerability management (patch critical vulnerabilities within 14 days), and annual penetration testing. Vendor shall provide Client with its most recent SOC 2 Type II report within ten (10) business days of request.

### 3.6 Service Level Agreement (SLA)

**Uptime commitments:**

| Tier | Monthly Uptime | Max Downtime/Month | Credit |
|:---|:---|:---|:---|
| Standard | 99.5% | ~3.6 hours | 10% of monthly fee |
| Professional | 99.9% | ~43 minutes | 10% of monthly fee |
| Enterprise | 99.95% | ~22 minutes | 25% of monthly fee |
| Mission Critical | 99.99% | ~4.3 minutes | 30% of monthly fee |

**Response time commitments:**

| Severity | Definition | Response Time | Resolution Target |
|:---|:---|:---|:---|
| P1 — Critical | Service is down; no workaround | 15 minutes | 4 hours |
| P2 — High | Major feature degraded; workaround exists | 1 hour | 8 business hours |
| P3 — Medium | Minor feature issue; limited impact | 4 business hours | 2 business days |
| P4 — Low | Cosmetic or enhancement request | 1 business day | Next release |

**SLA credit example clause:**
> If Vendor fails to meet the uptime SLA in a given calendar month, Client is entitled to a service credit calculated as follows: (Monthly Uptime Percentage − Actual Uptime Percentage) × 10 × Monthly Fee, capped at 30% of the monthly fee for that month. Service credits are Client's sole and exclusive remedy for downtime. Credits are applied to the next invoice and do not carry over beyond 12 months.

**SLA exclusions (typical):**
- Scheduled maintenance (with 48 hours' advance notice)
- Client-caused issues (e.g., misconfigured integrations)
- Force majeure events
- Beta or preview features
- Third-party service outages (e.g., cloud provider downtime)

### 3.7 Warranties

**Vendor warranties:**
> Vendor warrants that: (a) it has the authority to enter into this Agreement; (b) the Services will be performed in a professional and workmanlike manner consistent with generally accepted industry standards; (c) the Work Product will materially conform to the specifications in the applicable SOW for a period of ninety (90) days following acceptance ("Warranty Period"); (d) to Vendor's knowledge, the Work Product will not infringe any third party's intellectual property rights; and (e) Vendor will comply with all applicable laws in performing the Services.

**Client warranties:**
> Client warrants that: (a) it has the authority to enter into this Agreement; (b) it has the right to provide Client Data to Vendor for the purposes described herein; and (c) Client's use of the Work Product will comply with applicable laws.

**Warranty disclaimer:**
> EXCEPT AS EXPRESSLY SET FORTH IN THIS AGREEMENT, VENDOR DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT.

**Why the disclaimer matters:** Without it, implied warranties under the UCC (in the US) or equivalent laws could expose the vendor to claims beyond what was negotiated. The express warranties above are what you're actually promising.

### 3.8 Indemnification

Indemnification means one party agrees to cover the other's losses in specific scenarios. It's one of the most heavily negotiated clauses.

**Vendor indemnification (vendor protects client):**
> Vendor shall defend, indemnify, and hold harmless Client and its officers, directors, employees, and agents ("Client Indemnitees") from and against any third-party claims, damages, losses, liabilities, costs, and expenses (including reasonable attorneys' fees) arising from: (a) Vendor's breach of this Agreement; (b) Vendor's negligence or willful misconduct; (c) any claim that the Work Product infringes a third party's intellectual property rights; or (d) Vendor's violation of applicable law. If any Work Product is held or is reasonably likely to be held infringing, Vendor shall, at its expense: (i) obtain the right for Client to continue using it; (ii) modify it to be non-infringing; or (iii) replace it with a functional equivalent. If none of the foregoing is commercially reasonable, Vendor may terminate the applicable SOW and refund fees paid for the infringing Work Product.

**Client indemnification (client protects vendor):**
> Client shall defend, indemnify, and hold harmless Vendor and its officers, directors, employees, and agents from and against any third-party claims arising from: (a) Client Data, including any claim that Client Data infringes a third party's rights; (b) Client's use of the Work Product in a manner not authorized by this Agreement; or (c) Client's negligence or willful misconduct.

**Indemnification procedure:**
> The indemnified party shall: (a) promptly notify the indemnifying party in writing (failure to notify does not relieve the indemnifying party except to the extent of actual prejudice); (b) grant the indemnifying party sole control of the defense and settlement; and (c) cooperate reasonably at the indemnifying party's expense. The indemnifying party shall not settle any claim in a manner that imposes obligations on the indemnified party without prior written consent.

### 3.9 Limitation of Liability

**Purpose:** Cap the maximum financial exposure for both parties. Without this, a $100K project could theoretically result in millions in damages.

**Example clause:**
> EXCEPT FOR (A) INDEMNIFICATION OBLIGATIONS UNDER SECTION [X], (B) BREACH OF CONFIDENTIALITY OBLIGATIONS, (C) INFRINGEMENT OF INTELLECTUAL PROPERTY RIGHTS, AND (D) GROSS NEGLIGENCE OR WILLFUL MISCONDUCT:
>
> (i) NEITHER PARTY SHALL BE LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR PUNITIVE DAMAGES, INCLUDING LOSS OF PROFITS, REVENUE, DATA, OR BUSINESS OPPORTUNITY, REGARDLESS OF THE THEORY OF LIABILITY;
>
> (ii) EACH PARTY'S TOTAL AGGREGATE LIABILITY UNDER THIS AGREEMENT SHALL NOT EXCEED THE TOTAL FEES PAID OR PAYABLE BY CLIENT UNDER THIS AGREEMENT IN THE TWELVE (12) MONTHS PRECEDING THE CLAIM ("LIABILITY CAP").

**Common liability cap structures:**

| Structure | Example | When to Use |
|:---|:---|:---|
| 1x contract value | Cap = $100K on a $100K project | Standard for fixed-price projects |
| 12-month trailing fees | Cap = fees paid in prior 12 months | SaaS and recurring revenue deals |
| 2x contract value | Cap = $200K on a $100K project | When client has higher risk exposure |
| Per-SOW cap | Each SOW has its own cap | Multi-SOW relationships with varying risk |
| Uncapped for certain breaches | No cap on confidentiality, IP infringement, willful misconduct | Common carve-out for the most serious breaches |

**Super-cap:** Some agreements have a "super-cap" for the carved-out items (e.g., 3x contract value for confidentiality breaches). This prevents truly unlimited exposure while acknowledging that some breaches deserve higher limits.

**What to never agree to:**
- Unlimited liability in any direction
- Liability caps that are lower than a single milestone payment (vendor can just walk away)
- Waiving consequential damages with no carve-outs (if the vendor leaks your data, you can't recover business losses)

### 3.10 Audit Rights

**Example clause:**
> Client (or its designated independent auditor, subject to reasonable confidentiality obligations) may audit Vendor's compliance with this Agreement, including data processing activities, security controls, and financial records related to the Services, upon thirty (30) days' prior written notice. Audits shall: (a) occur no more than once per twelve-month period (unless triggered by a security incident or regulatory requirement); (b) be conducted during normal business hours; (c) be at Client's expense (unless the audit reveals a material breach, in which case Vendor bears the cost); and (d) not unreasonably interfere with Vendor's operations. Vendor shall cooperate reasonably and provide requested documentation within ten (10) business days.

### 3.11 Force Majeure

**Example clause:**
> Neither party shall be liable for delays or failures in performance resulting from causes beyond its reasonable control, including but not limited to: acts of God, natural disasters, pandemics, war, terrorism, government actions, labor disputes, utility failures, or internet backbone failures ("Force Majeure Events"). The affected party shall: (a) notify the other party in writing within five (5) business days; (b) use commercially reasonable efforts to mitigate the impact; and (c) resume performance as soon as practicable. If a Force Majeure Event continues for more than sixty (60) days, either party may terminate the affected SOW without penalty.

**What is NOT force majeure:**
- Vendor's staffing problems (they quit, got hired away, went on leave)
- Budget shortfalls
- Failure to plan for foreseeable risks
- Subcontractor failures (unless the subcontractor itself is affected by a force majeure event)

### 3.12 Non-Solicitation

**Example clause:**
> During the term of this Agreement and for twelve (12) months thereafter, neither party shall directly solicit or hire any employee of the other party who was involved in the performance of Services under this Agreement, without the other party's prior written consent. This restriction does not apply to: (a) general job postings not specifically targeted at the other party's employees; or (b) employees who have been separated from the other party for more than six (6) months.

**Practical notes:**
- Courts in some jurisdictions (e.g., California) limit enforceability of non-solicitation clauses. Know your jurisdiction.
- The restriction should be mutual — clients poach vendor engineers just as often as vendors poach client staff.
- "Involved in the performance of Services" is a reasonable scope. Don't try to restrict hiring of all employees at the other company.

### 3.13 Insurance Requirements

**Example clause:**
> Vendor shall maintain the following insurance coverage throughout the term of this Agreement:
>
> | Coverage | Minimum Amount |
> |:---|:---|
> | Commercial General Liability | $1,000,000 per occurrence / $2,000,000 aggregate |
> | Professional Liability (E&O) | $2,000,000 per claim / $2,000,000 aggregate |
> | Cyber Liability / Tech E&O | $2,000,000 per claim |
> | Workers' Compensation | As required by applicable law |
> | Employer's Liability | $1,000,000 per accident |
>
> Vendor shall provide certificates of insurance upon request and shall name Client as an additional insured on the Commercial General Liability policy. Vendor shall provide thirty (30) days' prior written notice of any material change or cancellation of coverage.

**Guidance on amounts:** The amounts above are typical for mid-market B2B tech deals ($100K–$1M contract value). For larger deals, enterprise clients often require $5M+ in cyber liability coverage. For smaller deals (<$50K), requiring $2M in cyber liability may price out smaller vendors — adjust proportionally.

### 3.14 Term & Termination

**Example clause:**
> **Term:** This Agreement is effective as of the Effective Date and continues for an initial term of two (2) years ("Initial Term"). Thereafter, it automatically renews for successive one (1) year periods ("Renewal Terms") unless either party provides written notice of non-renewal at least ninety (90) days before the end of the then-current term.
>
> **Termination for Convenience:** Either party may terminate this Agreement upon ninety (90) days' prior written notice. Client shall pay for all Services performed through the termination date.
>
> **Termination for Cause:** Either party may terminate this Agreement if the other party: (a) materially breaches this Agreement and fails to cure such breach within thirty (30) days of written notice; or (b) becomes insolvent, files for bankruptcy, or ceases to do business.
>
> **Effect of Termination:** Upon termination: (a) Client pays all outstanding invoices for work performed; (b) Vendor delivers all completed and in-progress Work Product; (c) each party returns or destroys the other's Confidential Information within thirty (30) days; (d) Sections [Confidentiality, IP, Indemnification, Limitation of Liability, Governing Law] survive termination.

**Termination for convenience — important detail:** If the vendor has a 90-day termination for convenience right, they can walk away from a project. If this is unacceptable, make termination for convenience client-only, or add a penalty (e.g., vendor must refund fees for undelivered milestones plus 10% as liquidated damages).

### 3.15 Governing Law & Dispute Resolution

**Example clause:**
> This Agreement shall be governed by and construed in accordance with the laws of the State of Delaware, without regard to its conflict of laws principles. Any dispute arising under this Agreement shall be resolved as follows:
>
> (a) **Negotiation:** The parties shall attempt to resolve the dispute through good-faith negotiation between senior executives within thirty (30) days of written notice.
>
> (b) **Mediation:** If negotiation fails, the parties shall submit the dispute to mediation administered by JAMS under its Mediation Rules. The mediation shall take place in New York, NY.
>
> (c) **Arbitration (or Litigation):** If mediation fails within sixty (60) days, the dispute shall be resolved by binding arbitration administered by JAMS under its Streamlined Arbitration Rules. The arbitration shall take place in New York, NY, before a single arbitrator. Judgment on the award may be entered in any court of competent jurisdiction.

**Arbitration vs. litigation:**

| Factor | Arbitration | Litigation |
|:---|:---|:---|
| Speed | Generally faster (6–12 months) | Can take years |
| Cost | Lower for simple disputes; can be expensive for complex ones | Discovery costs can be enormous |
| Privacy | Private proceedings | Public record |
| Appeal | Very limited | Full appellate rights |
| Injunctive relief | Arbitrator can grant; but court may be needed for emergency orders | Court can issue temporary restraining orders |

**Practical advice:** If you're the smaller party, arbitration is usually better — litigation costs can be used as a weapon by larger companies. If injunctive relief might be needed (e.g., IP theft), include a carve-out allowing either party to seek injunctive relief in court regardless of the arbitration clause.

---

## 4. Project Change Request (PCR) Template

**PCR ID:** PCR-20250401-001
**Related SOW:** SOW-20250201-001
**Requestor:** Acme Corp (Client)
**Date:** 2025-04-01
**Priority:** Medium

### Change Description
Acme requests the addition of French language support to the AI customer support agent. The initial SOW (SOR-20250115-001) specified English and Spanish only. Acme's Quebec operations are launching in Q3 2025, requiring French-language support by go-live.

### Justification
Acme is expanding into Quebec, Canada, where French-language support is legally required under Quebec's Charter of the French Language. This was not anticipated at the time of SOR creation.

### Impact Analysis

| Dimension | Current Baseline | Proposed Change | Impact |
|:---|:---|:---|:---|
| **Scope** | English + Spanish NLU models, conversation flows, KB | Add French NLU model, translate conversation flows, French KB ingestion | +1 language across all components |
| **Timeline** | Go-live: Week 20 | French support adds 3 weeks to Phase 2 | Go-live delayed to Week 23 (+3 weeks) |
| **Cost** | $89,100 total project | French language addition: $18,000 (20 person-days × $900 avg rate) | Total increases to $107,100 (+$18,000) |
| **Risk** | Low — 2 languages well-tested | French NLU model has less training data; accuracy may initially lag English/Spanish | Medium — may need additional tuning post-launch |
| **Resources** | Existing team | No additional headcount; ML Engineer allocation extends by 3 weeks | No new hires needed |

### Alternatives Considered
1. **Defer to Phase 2:** Launch English/Spanish on schedule, add French in a follow-up SOW. Risk: Quebec launch delayed.
2. **Translation-only (no NLU):** Use machine translation on English flows. Risk: Poor quality, doesn't meet regulatory requirements.
3. **Approved approach:** Native French NLU support with translated flows and KB.

### Amended Deliverables
- D2 (amended): Working AI Agent now includes French language support
- D4 (amended): UAT includes 50 French test conversations with ≥ 80% accuracy target (lower than English/Spanish due to less training data)

### Approval

| Role | Name | Decision | Signature | Date |
|:---|:---|:---|:---|:---|
| Vendor PM | Sarah Kim | Approve / Reject | _______________ | __________ |
| Client PM | David Park | Approve / Reject | _______________ | __________ |

### PCR Guidance

**When to issue a PCR vs. push back:**

Issue a PCR when:
- The request is genuinely out of scope (not in the SOW)
- It changes timeline, cost, or resource requirements
- It changes acceptance criteria
- It introduces new risk

Push back (no PCR needed) when:
- The request is already in scope and the client is confused about what was agreed
- The request is a bug fix during the warranty period
- The client is asking for a clarification, not a change

**How to estimate impact:**
1. Break the change into tasks with the engineering team
2. Estimate each task independently (don't anchor on the client's expected cost)
3. Add 20% buffer for integration and testing ripple effects
4. Consider the opportunity cost — does this change delay other work?
5. Document assumptions (e.g., "Assumes French training data provided by client")

**Getting stakeholder buy-in:**
- Present the cost of the change alongside the cost of NOT doing it
- Provide alternatives (e.g., "We can do a limited version for $8K or the full version for $18K")
- Frame timeline impact in business terms ("Go-live moves from June 15 to July 6")
- Get sign-off in writing before starting work. Verbal approval is not approval.
- If a stakeholder other than the designated PM requests a change, route it through the PM. Side-channel requests cause chaos.

---

## 5. Development Project Quote Template

**NovaMind Solutions — Project Quote**
- Client: Acme Corp
- Quote ID: QT-20250201-001
- Date: 2025-02-01
- Valid Until: 2025-03-03 (30 days)
- Currency: USD
- Related SOW: SOW-20250201-001

### Option A: Standard (Recommended)

Full implementation as specified in SOW-20250201-001.

| Service | Description | Rate | Qty (days) | Total |
|:---|:---|:---|:---|:---|
| **Phase 1: Discovery & Design** | | | | |
| | Requirements analysis & stakeholder interviews | $900 | 5 | $4,500 |
| | Architecture & integration design | $1,100 | 5 | $5,500 |
| | Security review & threat modeling | $1,100 | 3 | $3,300 |
| **Phase 2: Development** | | | | |
| | NLU model configuration & training | $1,000 | 15 | $15,000 |
| | Conversation engine development | $900 | 15 | $13,500 |
| | Knowledge base pipeline | $900 | 8 | $7,200 |
| | Zendesk integration | $900 | 8 | $7,200 |
| | Salesforce integration | $900 | 7 | $6,300 |
| | Analytics dashboard | $800 | 10 | $8,000 |
| **Phase 3: Testing & QA** | | | | |
| | Test planning & automation | $700 | 5 | $3,500 |
| | Integration & load testing | $700 | 5 | $3,500 |
| | UAT support | $700 | 5 | $3,500 |
| **Phase 4: Deployment** | | | | |
| | Production deployment | $1,000 | 3 | $3,000 |
| | Runbook & documentation | $800 | 3 | $2,400 |
| | Knowledge transfer (3 sessions) | $800 | 3 | $2,400 |
| **Project Management** | | | | |
| | PM (10% of delivery cost) | | | $8,880 |
| **Subtotal** | | | **100 days** | **$97,680** |
| **Contingency (10%)** | Buffer for unforeseen complexity | | | $9,768 |
| **Total — Option A** | | | | **$107,448** |

### Option B: Essential

Reduced scope — chat channel only, no Salesforce integration, basic dashboard.

| Service | Description | Total |
|:---|:---|:---|
| Phase 1: Discovery & Design | Same scope, but no Salesforce design | $10,800 |
| Phase 2: Development | Chat only, no Salesforce integration, basic analytics | $43,200 |
| Phase 3: Testing & QA | Reduced test scope | $7,500 |
| Phase 4: Deployment | Same | $7,800 |
| PM (10%) | | $6,930 |
| **Total — Option B** | | **$76,230** |

### Option C: Premium

Full scope plus: voice channel support, 3 additional languages, custom BI integration, 6-month post-launch support.

| Service | Description | Total |
|:---|:---|:---|
| Everything in Option A | | $107,448 |
| Voice channel integration | Telephony integration via Twilio | $28,000 |
| 3 additional languages | NLU + conversation flows + KB | $45,000 |
| Custom BI integration | Snowflake + Looker dashboards | $18,000 |
| 6-month post-launch support | 20 hours/month included | $36,000 |
| **Total — Option C** | | **$234,448** |

### Payment Schedule (Option A)

| Milestone | Trigger | % | Amount | Due Date |
|:---|:---|:---|:---|:---|
| M1 | Contract execution | 30% | $32,234 | Upon signing |
| M2 | Phase 1 complete (ADD sign-off) | 10% | $10,745 | ~Week 4 |
| M3 | Phase 2 complete (staging demo) | 30% | $32,234 | ~Week 14 |
| M4 | UAT sign-off | 20% | $21,490 | ~Week 17 |
| M5 | Go-live + 14-day hypercare | 10% | $10,745 | ~Week 20 |
| **Total** | | **100%** | **$107,448** | |

### Terms & Conditions
- Prices are exclusive of applicable taxes
- Travel expenses billed separately at cost, pre-approved
- Rate lock: Rates are valid for 12 months from contract signing; annual increases capped at 5%
- Change requests billed at T&M rates specified above, subject to PCR approval

### Pricing Strategy — Guidance

**Three-tier pricing (Good/Better/Best):**
Always present three options. Research shows most buyers pick the middle option ("compromise effect"). Structure your tiers so that:
- **Option B (Essential)** is priced to make Option A look like a better deal
- **Option A (Standard)** is what you actually want to sell, at your target margin
- **Option C (Premium)** anchors the price high and captures clients with bigger budgets

**How to set rates:**
1. Start with your cost (salary + overhead + tools + office)
2. Add your target margin (25–40% for services firms)
3. Benchmark against market rates for your geography and specialization
4. Adjust based on perceived value — if the client will save $1M/year, a $100K implementation fee is easy to justify

**Payment milestone best practices:**
- Never collect less than 20% upfront — it qualifies the client's commitment and covers your initial costs
- Tie payments to deliverables, not calendar dates — you don't want to be pressured to rush just to hit a payment date
- Keep the final payment ≤ 20% — if a client goes dark after go-live, you don't want to be chasing a large balance
- If the project is >6 months, consider monthly billing with milestone gates — it smooths cash flow for both parties
- Always include a "deemed acceptance" clause for milestone payments — if the client doesn't respond within X days, the milestone is accepted and payment is due

**Discounting:**
- Don't discount the rate — discount the scope. "We can remove the Salesforce integration to bring it under $80K" preserves your rate card integrity.
- Volume/multi-year discounts are fine: "Sign a 2-year support agreement and we'll discount the implementation by 10%"
- Never discount more than 15% on a first deal. It sets an anchor you'll never escape.

---

## 6. SaaS Subscription Agreement

This section covers the key terms for a hosted SaaS product. It's structured from the vendor's perspective but includes notes on what enterprise buyers will redline.

### 6.1 Subscription Terms

**Example clause:**
> Client subscribes to the [Product Name] service ("Service") at the tier and pricing specified in the applicable Order Form. The subscription term begins on the Effective Date and continues for the period specified in the Order Form ("Subscription Term"). Unless either party provides written notice of non-renewal at least sixty (60) days before the end of the Subscription Term, the subscription automatically renews for successive periods equal to the initial Subscription Term at the then-current list price, provided that renewal pricing shall not increase by more than 7% over the prior term's pricing.

**Buyer watch-out:** Auto-renewal with price increases is standard but can be aggressive. Negotiate a renewal price cap (5–7%) and longer notice periods (90 days) for enterprise deals.

### 6.2 Acceptable Use Policy

Typical restrictions:

> Client shall not: (a) sublicense, resell, or time-share the Service; (b) use the Service to store or transmit material that infringes third-party rights; (c) attempt to reverse-engineer, decompile, or disassemble the Service; (d) use the Service to transmit malware or conduct denial-of-service attacks; (e) exceed documented rate limits or use automated means to access the Service in a manner that degrades performance for other users; (f) use the Service for any purpose prohibited by applicable law; or (g) use the Service to build a competing product.

### 6.3 Data Ownership & Portability

**Example clause:**
> Client retains all right, title, and interest in Client Data. Vendor acquires no rights in Client Data except the limited right to process it to provide the Service. Upon termination or non-renewal, Vendor shall make Client Data available for export in a standard, machine-readable format (CSV, JSON, or SQL dump) for thirty (30) days. After this period, Vendor shall delete all Client Data and certify deletion in writing.

**Usage data / telemetry:**
> Vendor may collect anonymized, aggregated usage data ("Service Data") for purposes of improving, benchmarking, and marketing the Service. Service Data shall not identify Client or any individual user. Client may opt out of Service Data collection by written request.

### 6.4 SLA & Uptime Guarantees

**Uptime calculation:**
> "Monthly Uptime Percentage" = (Total Minutes in Month − Downtime Minutes) / Total Minutes in Month × 100. "Downtime" means the Service is materially unavailable as measured by Vendor's external monitoring (StatusPage). Downtime excludes: (a) scheduled maintenance with 48 hours' notice; (b) Client-caused issues; (c) force majeure; (d) features designated as "beta."

**Credit schedule:**

| Monthly Uptime | Service Credit (% of monthly fee) |
|:---|:---|
| 99.9% – 99.5% | 10% |
| 99.5% – 99.0% | 20% |
| Below 99.0% | 30% |

**Credit process:**
> Client must request credits within thirty (30) days of the downtime event. Credits are applied to the next invoice and are Client's sole remedy for downtime. Credits do not accrue beyond 30% of the monthly fee and cannot be exchanged for cash or refunds.

### 6.5 Support Tiers

| Feature | Free Tier | Standard | Premium |
|:---|:---|:---|:---|
| Support hours | Business hours (M–F 9–5 ET) | Business hours | 24/7/365 |
| Response time (P1) | 8 hours | 1 hour | 15 minutes |
| Support channel | Email | Email + Chat | Email + Chat + Phone + Slack |
| Dedicated CSM | No | No | Yes |
| Uptime SLA | 99.5% | 99.9% | 99.95% |
| Monthly price | Included | +20% of subscription | +40% of subscription |

### 6.6 Suspension & Termination

**Example clause:**
> Vendor may suspend Client's access to the Service if: (a) Client's payment is more than thirty (30) days overdue; (b) Client materially breaches the Acceptable Use Policy; or (c) continued provision of the Service would pose a security risk to other users. Vendor shall provide at least five (5) business days' prior written notice before suspension (except in cases of imminent security risk, where suspension may be immediate with notice provided as soon as practicable). Client's obligation to pay fees continues during suspension.

---

## 7. Partner / Reseller Agreement

### 7.1 Appointment & Territory

**Example clause:**
> Vendor appoints Partner as a non-exclusive [authorized reseller / referral partner / value-added reseller] for the Territory defined in Exhibit A. Partner shall not actively solicit customers outside the Territory. This appointment does not prevent Vendor from selling directly or appointing other partners within the Territory.

**Territory models:**

| Model | Description | When to Use |
|:---|:---|:---|
| Non-exclusive, no territory | Partner can sell anywhere; Vendor can too | Default for early-stage partner programs |
| Non-exclusive, named territory | Partner focuses on a region; Vendor can still sell there | Established markets with direct sales presence |
| Exclusive territory | Only this Partner can sell in the region | Emerging markets where you need a committed local partner |

### 7.2 Commission Structures

**Common models:**

| Model | How It Works | Example |
|:---|:---|:---|
| **Referral fee** | Partner refers lead, Vendor closes | 10–20% of first-year ACV |
| **Resale margin** | Partner buys at discount, sells at list price | 20–30% discount off list |
| **Revenue share** | Ongoing percentage of customer payments | 15–25% of recurring revenue, ongoing |
| **Tiered commission** | Rate increases with volume | 15% for first $100K, 20% for $100K–$500K, 25% above $500K |

**Example clause (revenue share):**
> Vendor shall pay Partner a commission equal to twenty percent (20%) of Net Revenue received from Partner-sourced customers during the first twenty-four (24) months of each customer's subscription ("Commission Period"). "Net Revenue" means gross subscription fees less refunds, credits, and taxes. Commissions are calculated monthly and paid within thirty (30) days of month-end. After the Commission Period, no further commissions are payable on renewals unless Partner actively supports the renewal.

**Key considerations:**
- Define "Partner-sourced" precisely — first touch? Last touch? Registered deal?
- Deal registration prevents channel conflict — Partner registers the opportunity with Vendor, who confirms no existing relationship
- Commission on renewals is a big negotiation point. Partners want it forever; vendors want it for 1–2 years.

### 7.3 Obligations

**Partner obligations:**
- Maintain at least one certified sales representative and one certified technical resource
- Complete Vendor's partner certification program within 90 days
- Achieve minimum quarterly booking target of $[X] (or lose exclusivity/tier status)
- Participate in quarterly business reviews with Vendor
- Use only Vendor-approved marketing materials
- Report pipeline and customer feedback monthly

**Vendor obligations:**
- Provide sales training and certification program
- Provide demo environment and sandbox accounts
- Co-marketing fund (MDF): Vendor matches Partner's marketing spend up to $[X]/quarter for approved activities
- Assign a Partner Account Manager as single point of contact
- Protect registered deals for 90 days
- Not undercut Partner pricing on registered deals

### 7.4 Non-Compete

**Example clause:**
> During the term of this Agreement and for twelve (12) months thereafter, Partner shall not develop, market, or resell any product that directly competes with the Vendor's Service in the same market category. This restriction applies only to the specific product category covered by this Agreement and does not restrict Partner's general business activities.

**Practical notes:** Non-competes in partner agreements are contentious. A partner that sells CRM tools won't agree to stop selling all CRM tools. Narrow the non-compete to specific, named competing products, or drop it entirely and rely on economic incentives instead.

### 7.5 Certification & Quality

> Partner shall maintain its certification status by: (a) completing annual recertification training; (b) maintaining a customer satisfaction rating of at least 4.0/5.0 as measured by Vendor's post-engagement surveys; and (c) resolving any customer escalations within the timeframes specified in Vendor's Partner Standards. Vendor may suspend or terminate this Agreement if Partner fails to maintain certification or if Partner's customer satisfaction rating falls below 3.5/5.0 for two consecutive quarters.

---

## 8. NDA Template

### 8.1 Mutual NDA

Use a mutual NDA when both parties will share confidential information (which is almost always the case in B2B sales and partnerships).

**Example:**

> **MUTUAL NON-DISCLOSURE AGREEMENT**
>
> This Mutual Non-Disclosure Agreement ("Agreement") is entered into as of [Date] by and between [Party A] and [Party B] (each a "Party," collectively the "Parties").
>
> **1. Purpose.** The Parties wish to explore a potential business relationship ("Purpose") and may need to share confidential information.
>
> **2. Confidential Information.** "Confidential Information" means any non-public information disclosed by either Party to the other, whether orally, in writing, electronically, or by inspection, that is designated as confidential or that a reasonable person would understand to be confidential given the nature of the information and circumstances of disclosure. Confidential Information includes, but is not limited to: source code, algorithms, product roadmaps, customer lists, pricing, financial data, business strategies, and the terms of this Agreement.
>
> **3. Exclusions.** Confidential Information does not include information that: (a) is or becomes publicly available through no fault of the Receiving Party; (b) was already known to the Receiving Party at the time of disclosure, as evidenced by written records; (c) is independently developed by the Receiving Party without reference to the Disclosing Party's Confidential Information; or (d) is rightfully received from a third party without restriction on disclosure.
>
> **4. Obligations.** Each Receiving Party shall: (a) use Confidential Information solely for the Purpose; (b) restrict disclosure to its employees, contractors, and advisors who need to know and who are bound by confidentiality obligations at least as protective as those herein; (c) protect Confidential Information with at least the same degree of care as its own confidential information, but no less than reasonable care; and (d) promptly notify the Disclosing Party upon discovery of any unauthorized use or disclosure.
>
> **5. Compelled Disclosure.** If the Receiving Party is compelled by law, regulation, or legal process to disclose Confidential Information, the Receiving Party shall: (a) provide prompt prior written notice to the Disclosing Party (to the extent legally permitted); (b) cooperate with the Disclosing Party's efforts to obtain a protective order; and (c) disclose only the minimum information legally required.
>
> **6. Term.** This Agreement is effective for two (2) years from the date above. The confidentiality obligations survive for three (3) years after expiration or termination of this Agreement.
>
> **7. Return of Materials.** Upon request or termination, the Receiving Party shall promptly return or destroy all Confidential Information and certify destruction in writing.
>
> **8. No License.** Nothing in this Agreement grants any license to the Receiving Party under any patent, copyright, trade secret, or other intellectual property right.
>
> **9. No Obligation.** This Agreement does not obligate either Party to enter into any further agreement or transaction.
>
> **10. Remedies.** Each Party acknowledges that breach of this Agreement may cause irreparable harm for which monetary damages are inadequate. The Disclosing Party is entitled to seek equitable relief, including injunction, in addition to any other available remedies.
>
> **11. Governing Law.** This Agreement shall be governed by the laws of [State/Country], without regard to conflict of laws principles.

### 8.2 One-Way NDA

Use when only one party is disclosing confidential information. Same structure as above, but only one party has obligations. Common in:
- Vendor demos where the prospect shares data but the vendor doesn't
- Due diligence (acquirer reviews target's books)
- Contractor onboarding

### 8.3 NDA Guidance

**Reasonable timeframes:**
- NDA duration (how long you'll share info): 1–3 years
- Confidentiality obligation survival (how long the info must stay secret): 2–5 years after NDA expiration
- Trade secrets: Should be protected indefinitely, or "for as long as they remain trade secrets"

**What to protect:**
- Source code, algorithms, architectures
- Customer lists, pricing, financial data
- Product roadmaps and strategy
- Unpublished patent applications
- Training data and models
- Deal terms

**What NOT to agree to:**
- Unlimited duration confidentiality obligations (except for trade secrets)
- NDA terms that prevent you from working with competitors
- Non-compete clauses embedded in NDAs (these should be separate, heavily negotiated)
- NDAs that require you to track and return all "mental impressions" — this is unenforceable and a red flag
- Penalties or liquidated damages clauses in NDAs — standard NDAs rely on equitable relief

**Who signs:**
- Both parties should sign. An NDA signed by only one party is a one-way promise.
- Make sure signers have authority. A sales rep may not have authority to bind the company.
- Date it. An undated NDA is messy to enforce.

---

## 9. Negotiation Playbook

### 9.1 Know What You're Negotiating

Before you enter a negotiation, classify the contract:

| Contract Type | Who Has Leverage | Typical Duration |
|:---|:---|:---|
| Enterprise SaaS (you're the vendor) | Buyer — they have options | 2–6 months |
| Custom development SOW | Balanced — vendor has expertise, buyer has budget | 2–4 weeks |
| Partnership/reseller | Balanced — both need each other | 4–8 weeks |
| NDA | Neither — should be quick | 1–3 days |
| Procurement-driven (RFP response) | Buyer — take it or leave it | 2–3 months |

### 9.2 Common Redlines by Company Size

**Startups (1–50 employees):**
- Often won't have insurance requirements — negotiate alternatives (e.g., SOC 2 Type II in progress)
- Won't agree to unlimited liability or uncapped indemnification
- Likely won't have a legal team — expect founder to sign
- Usually flexible on IP and terms; won't fight over boilerplate
- Redlines: liability cap below contract value, onerous insurance requirements, audit rights with no cost protection

**Mid-Market (50–500 employees):**
- Have legal counsel but may use outside firms (slower review)
- Standard redlines: IP assignment (want license instead), liability caps, data processing terms
- Usually have cyber insurance but amounts may not meet enterprise requirements
- Redlines: IP assignment of pre-existing tools, unlimited indemnification, US-only governing law for non-US companies

**Enterprise (500+ employees):**
- Procurement departments with standard contract templates — they'll want you on their paper
- Legal review takes 4–8 weeks minimum
- Standard redlines: EVERYTHING. They redline for a living.
- Key battles: whose paper (their MSA vs yours), liability caps (want uncapped for IP/data), audit rights (want broad), governing law (want their home jurisdiction), data processing (have strict DPA requirements)
- Accept their paper if the deal is worth it, but negotiate the commercial terms hard

### 9.3 What to Concede vs. Hold Firm

**Concede freely:**
- Governing law (within the same country — the legal differences between US states are rarely material for services contracts)
- Communication and reporting requirements (easy to comply with)
- Format of deliverables and documentation
- Insurance certificate naming (adding them as additional insured is routine)
- Non-solicitation (mutual, reasonable timeframe)
- Cosmetic changes to warranty language

**Negotiate but be flexible:**
- Liability cap amount (fight for 1x contract value; accept 2x if pressed)
- Payment terms (Net 30 is standard; accept Net 45 for enterprise; resist Net 60+)
- Indemnification scope (try for mutual; accept asymmetric if justified)
- Audit rights (accept annual audits; resist unlimited/unannounced)
- Termination for convenience notice period (60–90 days is reasonable)
- Auto-renewal terms (acceptable if price cap is in place)

**Hold firm — do not concede:**
- Unlimited liability (this can bankrupt you)
- IP assignment of your pre-existing tools and frameworks
- Broad non-compete clauses (you need to keep serving other clients)
- Right to withhold payment indefinitely for "dissatisfaction" (all disputes should have a resolution mechanism)
- Penalty clauses without caps
- Unilateral contract amendment rights ("Vendor may modify terms at any time")
- Requirements to carry insurance beyond what's commercially available or reasonable for your size

### 9.4 Legal Review Process

**Internal checklist before sending to legal:**
1. Read the entire contract yourself first. Don't send a 40-page MSA to legal without a summary of what you're concerned about.
2. Highlight the clauses you want to negotiate (IP, liability, indemnification, data processing)
3. Note any unusual or non-standard clauses
4. Provide context: deal value, strategic importance, relationship with counterparty
5. Set a deadline: "We need to sign by [date]. Please review by [date - 1 week]."

**Timeline expectations:**

| Contract Type | Your Legal Review | Counterparty Legal Review | Total |
|:---|:---|:---|:---|
| NDA | 1–2 days | 1–2 days | 3–5 days |
| SOW (under existing MSA) | 2–3 days | 3–5 days | 1–2 weeks |
| MSA (your paper) | Done (it's your template) | 2–4 weeks | 2–4 weeks |
| MSA (their paper) | 1–2 weeks | 1–2 weeks (redline back) | 4–8 weeks |
| Enterprise procurement | 2–3 weeks | 4–8 weeks | 6–12 weeks |

### 9.5 Negotiation Tactics

**For vendors:**
- Send your paper first. The party whose template is used has the structural advantage — the other side is making changes to your defaults.
- Pair every concession with a request. "We'll accept your liability cap if you agree to our payment terms."
- When they redline, don't respond point by point. Batch your responses and send one comprehensive redline.
- If legal is dragging, escalate to the business sponsor. "We're ready to start. Legal has had the contract for 6 weeks. Can you help move this forward?"
- Don't bluff. If you say "this is a dealbreaker," it has to actually be one.

**For buyers:**
- Get the vendor's standard contract first and redline it. This tells you how reasonable they are to work with.
- Use competitive bids as leverage — but only if you actually have them
- If the vendor is a startup, check their financial stability. A great contract is worthless if the vendor goes under.
- Negotiate for data portability and exit rights upfront. You'll never have more leverage than before you sign.
- If the vendor resists a DPA, that's a red flag. Walk away from vendors who can't meet basic data protection requirements.

---

## 10. Post-Launch Support Agreement

### 10.1 SLA Tiers

| Feature | Silver | Gold | Platinum |
|:---|:---|:---|:---|
| **Hours** | Business hours (M–F 9 AM–6 PM ET) | Extended (M–F 7 AM–10 PM ET) | 24/7/365 |
| **P1 Response** | 2 hours | 30 minutes | 15 minutes |
| **P1 Resolution Target** | 8 business hours | 4 hours | 2 hours |
| **P2 Response** | 4 business hours | 2 hours | 1 hour |
| **P3 Response** | 1 business day | 4 business hours | 2 business hours |
| **Included Hours** | 10 hours/month | 20 hours/month | 40 hours/month |
| **Uptime SLA** | 99.5% | 99.9% | 99.95% |
| **Named Contacts** | 2 | 5 | Unlimited |
| **Monthly Price** | $2,000 | $4,500 | $9,000 |
| **Overage Rate** | $200/hour | $180/hour | $150/hour |

### 10.2 Incident Response Procedures

**Severity definitions:**

| Severity | Definition | Examples |
|:---|:---|:---|
| **P1 — Critical** | Production system is down or a core function is completely unusable. No workaround exists. | AI agent not responding; all conversations failing; data breach detected |
| **P2 — High** | Core function is severely degraded. Workaround exists but is unsustainable. | Response latency >10 seconds; accuracy dropped below 70%; integration failure with Zendesk |
| **P3 — Medium** | Non-critical function is impaired. Limited user impact. | Dashboard metrics not updating; one intent category misclassifying; slow KB indexing |
| **P4 — Low** | Minor issue or enhancement request. No immediate business impact. | UI cosmetic issues; documentation error; feature request |

**Incident lifecycle:**

```
Detection → Triage → Acknowledge → Investigate → Resolve → Post-mortem
```

1. **Detection:** Client reports via support channel, or Vendor's monitoring detects automatically
2. **Triage:** Assign severity (P1–P4), assign owner, notify stakeholders per escalation matrix
3. **Acknowledge:** Response within SLA window; confirm issue, provide ticket number
4. **Investigate:** Root cause analysis, status updates every [30 min for P1, 2 hours for P2, daily for P3/P4]
5. **Resolve:** Deploy fix, confirm with client, update status page
6. **Post-mortem:** For all P1 and P2 incidents — written root cause analysis within 5 business days, including preventive measures. Shared with client.

### 10.3 Escalation Path

| Level | Who | When | Authority |
|:---|:---|:---|:---|
| L1 | Support Engineer | First response | Troubleshoot known issues, apply documented fixes |
| L2 | Senior Engineer | L1 unable to resolve within 2 hours (P1) or 4 hours (P2) | Deep investigation, access to production systems, deploy hotfixes |
| L3 | Engineering Lead / Architect | L2 unable to resolve within 4 hours (P1) or 1 business day (P2) | Architecture-level changes, emergency releases, engage vendor partners |
| Management | VP Engineering + Client Sponsor | L3 engaged for 2+ hours (P1) or issue spans multiple systems | Resource allocation, priority override, business decisions |

**After-hours escalation (Platinum only):**
- On-call engineer reachable within 5 minutes via PagerDuty
- On-call rotation published monthly, shared with client

### 10.4 Maintenance Windows

**Scheduled maintenance:**
> Vendor shall perform scheduled maintenance during the designated maintenance window: Sundays 2:00 AM – 6:00 AM ET. Vendor shall provide at least 48 hours' advance notice for standard maintenance and 7 days' notice for maintenance expected to cause downtime exceeding 30 minutes. Scheduled maintenance during the maintenance window does not count against uptime SLA.

**Emergency maintenance:**
> Vendor may perform emergency maintenance outside the scheduled window to address critical security vulnerabilities or system stability issues. Vendor shall provide as much advance notice as practicable (minimum 2 hours) and limit the maintenance duration to what is strictly necessary.

**Change freeze periods:**
> No deployments or system changes (except emergency fixes) during the following periods: (a) Client's fiscal quarter-end (last 3 business days); (b) Major shopping holidays (Black Friday through Cyber Monday, December 20–January 2); (c) Any period designated by Client with at least 30 days' notice.

### 10.5 End-of-Life (EOL) Policy

**Example clause:**
> Vendor shall provide at least twelve (12) months' written notice before ending support for any major version of the Service ("End of Life Notice"). During the notice period, Vendor shall: (a) continue to provide security patches and critical bug fixes; (b) provide migration assistance to the successor version at no additional charge (up to 20 hours); (c) maintain data export capabilities. After the EOL date, the deprecated version receives no further updates, patches, or support.

**Version support lifecycle:**

| Phase | Duration | What's Included |
|:---|:---|:---|
| **Active** | Current version | Full feature development, all bug fixes, full support |
| **Maintenance** | Current − 1 version (12 months after next major release) | Security patches, critical bug fixes, support |
| **Extended** | Current − 2 version (6 months after entering Extended) | Security patches only, best-effort support |
| **EOL** | After Extended period ends | No patches, no support, no SLA |

### 10.6 Reporting

Vendor provides the following reports to Client:

| Report | Frequency | Contents |
|:---|:---|:---|
| Uptime & Performance | Monthly | Uptime %, latency percentiles, error rates, throughput |
| Incident Summary | Monthly | All incidents with severity, resolution time, root cause |
| SLA Compliance | Monthly | SLA targets vs actuals, credits owed |
| Capacity & Usage | Quarterly | Trends, capacity forecasts, scaling recommendations |
| Security | Quarterly | Vulnerability scans, patch status, access audit logs |
| Executive Summary | Quarterly | Business-level metrics, recommendations, roadmap updates |

---

## Appendix: Document Relationships

```
MSA (governs all)
 ├── NDA (often standalone, can be exhibit to MSA)
 ├── DPA (exhibit to MSA)
 ├── SOW #1 (references SOR)
 │    ├── Quote #1
 │    ├── PCR #1a
 │    └── PCR #1b
 ├── SOW #2
 │    └── Quote #2
 ├── Support Agreement (post-launch)
 ├── SaaS Subscription Agreement (if applicable)
 └── Partner/Reseller Agreement (if applicable)
```

**Execution order:**
1. NDA first (before sharing any confidential info)
2. MSA + DPA (establishes the legal relationship)
3. SOW + Quote (defines and prices specific work)
4. PCRs as needed (manages changes)
5. Support Agreement (before go-live)

**Hierarchy of documents (in case of conflict):**
1. PCRs (most recent amendment wins)
2. SOW (specific terms override general)
3. MSA (general terms)
4. DPA (data-specific terms; may override MSA on data matters)
5. Exhibits and attachments
