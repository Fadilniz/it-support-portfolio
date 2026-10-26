# n8n projects — demo, AIRA

All descriptions below are written from the workflow exports, not from live production claims. AIRA is demo-stage with no paying clients. No raw JSON exports are published here: a scan of the 52 exports found credential references in 44 files and real email addresses in the exports, so raw files stay private until a full redaction pass (emails, webhook URLs, Sheet / Calendar / Drive IDs, credential blocks) is done. Descriptions and diagrams first.

## 1. Appointment booking lifecycle

- Source workflow: `Book an appointment` — 20 nodes.
- Flow: webhook in → availability / routing checks → Google Sheets and Google Calendar writes → Gmail confirmations → webhook response.
- Related sub-workflows cover the full lifecycle: book, availability check, update, cancel, and delete.
- What it shows: appointment lifecycle handling, Sheets + Calendar + Gmail integration, and branching on availability.
- Honest note: demo-stage. Known AIRA reliability issues in this area included booking-confirmation timeouts and wrong-row Sheet updates — this portfolio does not claim those are fixed in production.

## 2. Multi-tenant call concurrency control with overflow recovery

- Source workflow: `Multi-Tenant Call Concurrency Control with Overflow Recovery` — 25 nodes, including 12 HTTP Request nodes, a Twilio node, and an Execute Workflow node.
- Flow: webhook in → tenant routing (Switch) → concurrency checks via HTTP calls → overflow path when capacity is hit → webhook responses.
- What it shows: thinking about concurrent calls per tenant, not just a single happy-path call, and a recovery / overflow path instead of dropping the call.

## 3. Call intake + emergency triage

- Source workflow: `Call Intake` — 11 nodes (webhook, code, Gmail, Google Calendar x2, AI agent via OpenRouter, branching).
- The standalone `Emergency Triage` export is only 2 nodes (trigger + set) — it is a routing stub inside the intake flow, not a full triage system on its own. Do not present it as more than that.
- What it shows: intake capture, routing by case type, calendar interaction, and an AI-agent step with structured handling.

## 4. RAG knowledge base

- Source workflow: `knowledgeBase` — 13 nodes, plus the related `C-Memory` workflow (Pinecone vector store, OpenAI embeddings).
- Flow: Google Drive trigger → document loading and recursive text splitting → OpenAI embeddings → Pinecone vector store → AI agent retrieval, with a Gmail tool available to the agent.
- What it shows: retrieval-augmented answering over documents, not just a chatbot prompt.
