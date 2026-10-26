# Fadil Nizar — IT Support / Implementation Portfolio

Target roles: IT Support Tier 1, SaaS Technical Support, Implementation / Onboarding Specialist — GTA, Canada.

All projects below are honestly labelled lab/demo work with synthetic data, unless stated otherwise. No paying clients. No invented metrics — where a number would help but is not verified, it is left out.

Upload status (26 Oct 2026): the three project folders in this draft now each contain a README — Zendesk tickets, n8n descriptions, and the Entra project, completed as a lab on 26 Oct 2026 (see entra-user-lifecycle/README.md). No raw JSON is included. GitHub account confirmed: Fadilniz. Publish the 5 markdown files in this draft only — do not publish tickets-6-10-draft.md, which is draft-only and not done.

## Projects

### 1. Zendesk ticket simulation (lab/demo, synthetic data)
- Diagnosed, documented, and resolved 5 support tickets: POS terminal frozen mid-order, receipt printer offline, POS login locked out, card reader failing, menu item price wrong on POS vs menu board.
- For each ticket: report, checks, fix or escalation, priority (High / Medium / Low), and close as Solved, using internal notes only — no public replies to real people.
- Subdomain used for the trial: aira-90781.zendesk.com. Trial showed 13 days left on 24 Oct 2026, so save screenshots / copies before the trial ends (approx. early Nov 2026 — verify in Zendesk, do not rely on this estimate).
- Next step to strengthen it: expand from 5 to 15–20 tickets with SLA / escalation notes. That expansion is planned, not done yet.

### 2. n8n appointment booking lifecycle (demo, AIRA)
- Source workflow: `Book an appointment` — 20 nodes.
- Flow, from the export: webhook in → availability / routing checks → Google Sheets (4 nodes) and Google Calendar (4 nodes) writes → Gmail confirmations (2 nodes) → webhook response.
- What it shows: full appointment lifecycle handling (book / check / update / cancel / delete across the related sub-workflows), Sheets + Calendar + Gmail integration, branching on availability.
- Honest note: demo-stage. Known AIRA reliability issues in this area included booking-confirmation timeouts and wrong-row Sheet updates — this portfolio does not claim those are fixed in production.

### 3. Multi-tenant call concurrency control with overflow recovery (demo, AIRA)
- Source workflow: `Multi-Tenant Call Concurrency Control with Overflow Recovery` — 25 nodes, including 12 HTTP Request nodes, a Twilio node, and an Execute Workflow node.
- Flow, from the export: webhook in → tenant routing (Switch) → concurrency checks via HTTP calls → overflow path when capacity is hit → webhook responses.
- What it shows: thinking about concurrent calls per tenant, not just a single happy-path call, and a recovery / overflow path instead of dropping the call.

### 4. Call intake + emergency triage (demo, AIRA)
- Source workflow: `Call Intake` — 11 nodes (webhook, code, Gmail, Google Calendar x2, AI agent via OpenRouter, branching).
- The standalone `Emergency Triage` export is only 2 nodes (trigger + set) — it is a routing stub inside the intake flow, not a full triage system on its own. Do not present it as more than that.
- What it shows: intake capture, routing by case type, calendar interaction, and an AI-agent step with structured handling.

### 5. RAG knowledge base (demo, AIRA)
- Source workflow: `knowledgeBase` — 13 nodes, plus the related `C-Memory` workflow (Pinecone vector store, OpenAI embeddings).
- Flow, from the export: Google Drive trigger → document loading and recursive text splitting → OpenAI embeddings → Pinecone vector store → AI agent retrieval, with a Gmail tool available to the agent.
- What it shows: retrieval-augmented answering over documents, not just a chatbot prompt.

### 6. Entra / Microsoft 365 user lifecycle — LAB, COMPLETED Oct 26, 2026
- Joiner / mover / leaver, password reset, in a Microsoft Entra ID Free tenant, using the fictional Northline HVAC company (12 synthetic staff, 3 Security groups: Office, Technicians, Dispatch). Full write-up in entra-user-lifecycle/README.md. Synthetic data only, no production users, no paid services.

## What is NOT in this portfolio (yet)
- Raw n8n JSON exports are NOT published here. A scan of the 52 exports on 24 Oct 2026 found: no API-key values in plain text, but 44 files contain credential references and the exports contain real email addresses. Before any raw file goes public, strip / replace: all real email addresses, webhook URLs, Sheet / Calendar / Drive IDs, and credential blocks. Publish descriptions and diagrams first; publish sanitised JSON only after that redaction pass.
- No client names, no real customer data, no real coworker names. Ticket requesters in the Zendesk demo are synthetic test users (Alex / Sam / Jordan / Taylor / Casey Test).

## Contact
- GitHub: github.com/Fadilniz
- LinkedIn: linkedin.com/in/fadilnizar
- Email: fadil@aira.company
